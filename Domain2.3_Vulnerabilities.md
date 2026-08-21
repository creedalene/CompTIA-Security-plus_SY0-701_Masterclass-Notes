# CompTIA Security+ (SY0-701) Domain 2.3 Explain various types of vulnerabilities.

## Application

Applications create their own attack surface through flaws in memory handling, concurrent execution, and trusted code delivery.

Attackers inject malicious code directly into a running process’s memory space so the malware inherits the process’s identity and privileges while remaining hidden from process-name scanners. Oversized input that exceeds a buffer’s allocated size overwrites adjacent memory, letting the attacker rewrite variables, return addresses, or executable instructions and seize control. Concurrent operations that check a resource and later act on that check without re-verification produce race conditions; the gap between time-of-check and time-of-use allows another process to alter the resource and force the application to operate on stale data. Even the update mechanism itself becomes a delivery channel when attackers compromise a vendor’s build system, embed malware inside a digitally signed package, and distribute it through the normal automated pipeline.

These weaknesses share a common root: the application trusts its own memory layout, timing assumptions, or update source without sufficient verification.

### Memory injection

All software executes inside memory (RAM). The CPU processes instructions only after the system loads them from disk into memory. Malware therefore must reach memory to run.

Malware chooses one of two paths. It can launch as its own process. Or it can locate a legitimate running process and inject its code into that process’s memory space.

A process occupies a defined memory range with a start address and an end address. The attacker writes the malicious code somewhere inside that range. Once injected, the malware runs under the identity of the legitimate process. Anti-malware tools that scan for suspicious process names or file signatures often miss it. The injected code also inherits the rights and permissions of the target process. This produces privilege escalation: the malware gains higher access than it would possess on its own.

**DLL Injection**

One of the most common memory-injection techniques is DLL injection. A Dynamic-Link Library (DLL) is a Windows library that contains reusable code and data. Multiple applications load and share the same DLL.

The attacker first places a malicious DLL on storage the system can reach. Next the attacker writes the path to that DLL into the memory of a chosen target process. When the process later needs to load a library, it follows the injected path, pulls the malicious DLL from disk, and maps it into its own address space. The malicious code then executes as part of the legitimate process.

Because the malware runs inside a trusted process, it gains access to that process’s data and inherits its privileges. Detection becomes harder because the process itself appears legitimate. Memory forensics—examining the contents of RAM—can still reveal the injected code that file-based scanners miss.

Memory injection therefore lets attackers hide malware, escalate privileges, and continue operating under the cover of normal system processes.

### Buffer overflow

A buffer overflow occurs when an application writes more data into a reserved memory area (the buffer) than that area can hold. The excess data spills into the adjacent memory space and overwrites whatever values or instructions reside there.

Developers normally perform bounds checking. They verify that incoming data fits inside the allocated buffer size. When the application skips this check, an attacker can supply oversized input and force the overflow.

Most buffer overflows simply crash the application or produce unpredictable results. Attackers search for a specific, repeatable overflow that consistently produces a useful outcome. A successful overflow can change the value of a neighboring variable, alter a return address on the stack, or insert executable instructions. In each case the attacker gains control that the original program never intended to grant.

**Example**

An application stores two variables side by side in memory. Variable A holds eight bytes and currently contains zeros. Variable B holds a two-byte privilege value set to 1979. Any value in Variable B below 2000 grants only user rights. A value above 24 000 grants administrator rights.

The attacker sends nine bytes of data into Variable A. The first eight bytes fill Variable A. The ninth byte overflows into Variable B and changes its value to 25 856. The application now treats the user as an administrator even though no legitimate credentials were supplied.

Because the overflow is controllable and repeatable, the attacker escalates privileges without authenticating. The same technique can overwrite function pointers or return addresses to redirect program execution to attacker-supplied code.

Buffer overflows therefore convert a simple input-validation failure into privilege escalation or arbitrary code execution.

### Race conditions

A race condition occurs when two or more events execute nearly simultaneously inside an application and the application fails to account for their concurrent operation. The resulting state becomes unpredictable or incorrect.

Developers normally design code to handle sequential steps. When concurrent processes interleave in unexpected ways, the application produces outcomes the programmer never intended.

**Time-of-Check (TOC) / Time-of-Use (TOU)**

The most common form is the Time-of-Check to Time-of-Use (TOCTOU) race condition. The application first checks a system value or resource state (the time of check). Later it performs an action that depends on that value (the time of use). Between the check and the use, another process alters the value. The application then acts on outdated information.

**Example**

Two users transfer funds between Account A and Account B. Both accounts start with $100.

- User 1 and User 2 each check the balances and both see $100 in each account.  
- User 1 deposits $50 into Account B. The deposit updates immediately, so Account B now shows $150.  
- User 2 also deposits $50 into Account B. Account B now shows $200.  
- User 1 withdraws $50 from Account A. From User 1’s view, Account A holds $50 and Account B holds $200.  
- User 2 performs the same withdrawal. Because the application does not update withdrawals for all users at once, User 2 still sees the earlier balances. The final recorded state shows Account A at $50 and Account B at $200, yet Account A should actually hold $0.

The gap between the balance check and the actual withdrawal allows the race condition to create an incorrect ledger.

Race conditions therefore let concurrent operations corrupt shared data, produce inconsistent states, or enable unauthorized actions whenever the application fails to synchronize its checks with its subsequent uses.

**Time-of-check (TOC)**

An application reaches a decision point and inspects a resource—file permissions, account balance, process state, or access flag. That inspection is the time-of-check. The code records the result and continues under the belief that nothing will change.

While the application moves toward the later action, a second process rewrites the same resource. The original check is now stale. When the application finally acts, it operates on data that no longer matches reality.

In banking software the TOC step confirms a balance of $500. Concurrent activity drains the account to zero before the transfer executes. The application still trusts the earlier verification and completes the withdrawal, producing an overdraft that should never have been allowed.

Any security-relevant decision that is separated in time from its enforcement creates this window. The longer the interval between inspection and action, the wider the opportunity for concurrent interference.

**Time-of-use (TOU)**

After an application finishes its security inspection, it later performs the actual operation that depends on that inspection. This later moment is the time-of-use. The code treats the earlier result as still valid and proceeds without re-verifying the resource.

Concurrent activity can rewrite the resource in the intervening gap. The application reaches the TOU step and acts on information that no longer exists. Privilege checks, file opens, balance deductions, and access grants all become unreliable once the original state has changed.

A process confirms write permission on a configuration file (TOC). Before it opens and modifies the file, an attacker replaces the legitimate file with a symbolic link pointing to a sensitive system file. At the TOU step the application writes its data into the wrong location, elevating the attacker’s control.

The TOU phase therefore converts a temporary verification into a permanent action. Any design that separates the decision from its execution leaves a window attackers can occupy and exploit.

### Malicious update

Operating systems and applications regularly pull patches and new code through automated update channels. Each update installs fresh executable content, so the same pipeline that closes vulnerabilities can also deliver malware.

Attackers target the update process itself. They compromise a vendor’s build system, insert their own code into the legitimate package, and allow the vendor’s normal distribution and digital-signing process to push the altered update to every customer. Because the package carries a valid signature and arrives through the expected channel, security tools and users treat it as trusted.

The 2020 SolarWinds Orion incident illustrates the risk. Attackers modified the Orion source on the vendor’s development network. The resulting updates were digitally signed by SolarWinds and delivered through the product’s built-in update mechanism. Organizations that applied the update received both the intended management features and a backdoor that granted the attackers privileged access across government and commercial networks.

Digital signatures, trusted distribution servers, and application-controlled update engines raise the bar, yet they cannot fully eliminate the threat once the vendor’s own development environment is breached. Any automated update path therefore remains a high-value vector for large-scale, trusted-code distribution of malware.

## Operating system (OS)-based

Operating systems form the foundation of every computing platform. Their massive code bases—Windows 11 alone contains tens of millions of lines—create continuous opportunities for undiscovered flaws. Attackers prioritize these platforms because a single successful exploit can affect every application and user running on the system.

Vendors release patches as soon as researchers or attackers report new vulnerabilities. Microsoft consolidates most of its fixes into monthly releases on the second Tuesday of each month, commonly called Patch Tuesday. A typical release addresses dozens of issues that range from elevation of privilege and security-feature bypasses to remote code execution.

Once a vulnerability becomes public, attackers race to reverse-engineer the patch and weaponize the original flaw. Systems that remain unpatched after disclosure therefore face immediate risk. Administrators must therefore treat every security update as time-critical: test the patch in a controlled environment when the infrastructure is large, install it promptly, and maintain current backups so any unexpected side-effect can be reversed.

The core defense against OS-based vulnerabilities is continuous, verified patching. Unpatched operating systems leave known attack paths open; timely updates close those paths before exploit code can spread.

## Web-based

Web applications that accept user input and render dynamic content create two primary injection paths attackers routinely exploit.

When an application embeds unvalidated input directly into a Structured Query Language (SQL) statement, the attacker can rewrite the query itself. A single crafted fragment such as OR 1=1 forces the database to return every record, grant elevated privileges, or destroy data—all from an ordinary browser form field.

When the same unvalidated input reaches the browser as executable script, the attacker injects JavaScript that runs under the trusted site’s security context. Reflected XSS delivers the payload through a malicious link that executes once; stored XSS plants the script permanently so every subsequent visitor becomes a victim. In both cases the browser willingly hands over session tokens and cookies to the attacker.

Both attacks succeed because the application treats untrusted input as executable code rather than pure data. Parameterized queries and rigorous output encoding close these channels before the database or the browser ever sees the malicious payload.

### Structured Query Language injection (SQLi)

Applications that interact with databases accept user input and embed it into Structured Query Language (SQL) statements. SQL is the language used to query and modify relational databases. When the application fails to validate or sanitize that input, an attacker can insert additional SQL commands of their own.

The attacker types the malicious fragment directly into a form field or URL parameter. The application concatenates the fragment into the original query and sends the combined statement to the database. A classic injection ends the intended condition with a single quote and appends `OR 1=1`. Because 1 always equals 1, the database returns every matching row instead of the single intended record.

With this control the attacker can read the entire database, alter or delete records, escalate privileges inside the database engine, or shut the database down. The attack requires no specialized tools; any ordinary browser is sufficient.

Proper defenses force the application to treat all user input as data rather than executable code. Parameterized queries and prepared statements keep the attacker’s input outside the SQL command structure, eliminating the injection path.

### Cross-site scripting (XSS)

Cross-site scripting (XSS) lets an attacker inject malicious scripts—most often JavaScript—into a trusted website so that the victim’s browser executes those scripts under the website’s security context. The browser trusts the legitimate domain and therefore grants the injected code access to cookies, session tokens, and other private data belonging to that site.

Two primary forms exist.

**Non-persistent (reflected) XSS**  
The attacker crafts a malicious URL that embeds the script. When the victim clicks the link, the vulnerable website reflects the script back in its response. The browser runs the script once and immediately sends session information or other data to the attacker.

**Persistent (stored) XSS**  
The attacker posts the script into a permanent location such as a comment field, forum message, or social-media feed. Every subsequent visitor who loads that page automatically executes the script. The attack scales without further action from the attacker.

In both cases the victim’s browser becomes the unwitting agent that steals credentials or performs actions on the attacker’s behalf while the user remains unaware. Input validation and output encoding on the application side, combined with current browser patches, close the injection points that make XSS possible.

## Hardware

### Firmware

### End-of-life

### Legacy

## Virtualization

### Virtual machine (VM) escape

### Resource reuse

## Cloud-specific

## Supply chain

### Service provider

### Hardware provider

### Software provider

## Cryptographic

## Misconfiguration

## Mobile device

### Side loading

### Jailbreaking

## Zero-day

## Conclusion
