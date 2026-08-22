# CompTIA Security+ (SY0-701) Domain 2.4 Given a scenario, analyze indicators of malicious activity.

## Malware attacks

Malware attacks form a core category of malicious activity under CompTIA Security+ SY0-701 objective 2.4. Malware is software intentionally designed to disrupt, damage, or gain unauthorized access to systems. Attackers deploy it to achieve goals such as data theft, system control, financial extortion, or operational disruption. Analysts must recognize the distinct behaviors, delivery methods, and indicators of each malware type to identify compromise and select appropriate responses.

Malware reaches targets through the threat vectors listed in objective 2.2—phishing, vulnerable services, supply-chain compromise, removable media, and social engineering. Once active, different malware families prioritize different outcomes: encryption and extortion, covert data collection, autonomous spreading, stealthy persistence, or delayed destruction. Many modern samples combine multiple functions, so a single infection may deliver a Trojan that installs a keylogger, a rootkit, and later a ransomware payload.

Effective analysis focuses on observable indicators: unusual process behavior, unexpected network connections, file-system changes, disabled security tools, and anomalous resource consumption. Mitigation relies on the techniques in objective 2.5—segmentation, least privilege, hardening, patching, and endpoint detection—while incident response follows the lifecycle in objective 4.8.

The sections that follow detail each malware type examined on the SY0-701 exam: ransomware, Trojan, worm, spyware, bloatware, virus, keylogger, logic bomb, and rootkit. Each entry covers definition, mechanism, variants, indicators, impact on the CIA triad, threat actors, mitigations, and response considerations.

### Ransomware

Ransomware is a category of malware that encrypts files on a target system or locks the user out of the device, then demands payment—typically in cryptocurrency—for the decryption key or restored access. The attack denies the victim use of their own data or systems until the ransom condition is met or alternative recovery occurs. CompTIA Security+ SY0-701 classifies ransomware under malware attacks within objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
The malware gains execution on a host, then systematically encrypts user files, databases, and sometimes system volumes using strong symmetric algorithms (commonly AES) combined with asymmetric key wrapping (RSA or similar). The private decryption key remains under attacker control. After encryption completes, the malware drops a ransom note—usually a text file, HTML page, or desktop wallpaper—containing payment instructions, a unique victim identifier, and a deadline. Many modern variants first exfiltrate sensitive data before encryption begins.

Attackers frequently delete or encrypt Volume Shadow Copies and other local recovery points so the victim cannot simply roll back. Encryption proceeds rapidly across mapped drives, network shares, and cloud-synced folders when the compromised account holds sufficient privileges.

**Variants and Evolution**
- **Crypto-ransomware**: Encrypts files in place and appends a new extension (e.g., .locked, .encrypted). The original content becomes unreadable without the key.
- **Locker ransomware**: Locks the entire operating system or display, preventing login or normal use without encrypting individual files.
- **Double extortion**: Combines encryption with prior data theft. Attackers threaten to publish or sell the stolen data on leak sites if the ransom is unpaid. Backups alone no longer neutralize the threat because confidentiality is already compromised.
- **Triple extortion**: Extends pressure by contacting the victim’s customers, partners, or regulators and threatening further disclosure.
- **Ransomware-as-a-Service (RaaS)**: Developers package the malware, negotiation portals, and leak-site infrastructure, then lease access to affiliates who perform the intrusion. Revenue is shared. This model lowers the skill barrier and increases attack volume.

**Delivery Vectors and Attack Surface**
Ransomware reaches systems through the same initial-access techniques listed in objective 2.2:
- Phishing and spear-phishing emails carrying malicious attachments or links
- Compromised credentials reused on remote-access services (RDP, VPN)
- Exploitation of unpatched software vulnerabilities
- Malicious downloads from drive-by websites or software supply-chain compromise
- Lateral movement after an initial foothold, often via tools that disable security products and propagate across the domain

Once inside, the malware may use living-off-the-land binaries, PowerShell, or legitimate administrative tools to avoid detection while it stages encryption.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, look for these concrete signs:
- Sudden appearance of ransom notes across multiple directories
- Mass file-extension changes and inability to open previously accessible documents
- High disk and CPU activity from a previously unknown process performing rapid sequential file reads and writes
- Deletion or encryption of Volume Shadow Copies and backup catalogs
- Unusual outbound network traffic preceding encryption (data exfiltration)
- Disabled antivirus, EDR, or Windows Defender services
- New scheduled tasks, registry Run keys, or services that maintain persistence
- Accounts performing large-scale file access outside normal patterns

These indicators often surface first in endpoint detection and response (EDR) alerts, SIEM correlation rules, or user reports of inaccessible files.

**Impact on the CIA Triad**
Ransomware primarily attacks **availability** by rendering data and systems unusable. Encryption simultaneously damages **integrity** because the original content is altered. When double-extortion techniques are used, **confidentiality** is also breached through unauthorized data extraction. Business processes halt, regulatory reporting obligations arise, and recovery costs frequently exceed the ransom demand itself.

**Associated Threat Actors**
Organized crime groups drive the majority of ransomware campaigns; their primary motivation is financial gain. Nation-state actors occasionally deploy ransomware-style tools for disruption or as cover for other objectives, but the dominant profile remains criminal. RaaS ecosystems allow less-skilled affiliates to participate while core developers retain control of the encryption keys and payment infrastructure.

**Mitigation Techniques**
Objective 2.5 lists core techniques that directly reduce ransomware risk:
- **Segmentation and isolation**: Limit lateral movement so a single compromised host cannot reach critical file servers or domain controllers.
- **Access control and least privilege**: Restrict accounts so ransomware cannot encrypt broad portions of the environment or delete backups.
- **Hardening and configuration enforcement**: Disable unnecessary services, enforce application allow-listing, and remove default credentials.
- **Patching**: Close the vulnerabilities that attackers exploit for initial access and privilege escalation.
- **Endpoint protection**: Deploy and keep current antivirus/EDR solutions capable of detecting both known ransomware signatures and behavioral indicators (mass file encryption, shadow-copy deletion).

Additional resilience measures from Domain 3 and 4 reinforce these controls:
- Maintain offline, encrypted, immutable backups that ransomware cannot reach or encrypt.
- Test restoration procedures regularly.
- Implement multifactor authentication on all remote-access and privileged accounts.
- Monitor for anomalous file-access patterns and outbound data transfers.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8), ransomware triggers rapid movement through containment, eradication, and recovery:
- **Containment**: Isolate affected hosts from the network, disable compromised accounts, and block command-and-control domains.
- **Eradication**: Remove the malware binary, any persistence mechanisms, and the initial access vector.
- **Recovery**: Restore from verified clean backups. Paying the ransom does not guarantee a working decryption key and may encourage further attacks; official guidance generally discourages payment.
- **Lessons learned**: Update playbooks, improve detection rules, and address the root cause (unpatched system, weak credentials, insufficient segmentation).

Tabletop exercises that simulate ransomware on critical systems expose gaps in backup integrity, communication plans, and decision authority before a real incident occurs.

**Key Exam Distinctions**
Ransomware differs from other malware types in its explicit extortion goal and reliance on encryption or locking for leverage. Unlike a worm that primarily propagates, or a Trojan that opens a backdoor, ransomware’s success metric is payment or irreversible data loss. Recognition of ransom notes, mass encryption activity, and shadow-copy deletion remains the primary analytical cue for SY0-701 scenarios.

### Trojan

A Trojan (or Trojan horse) is malware that disguises itself as legitimate software or a useful file. The user executes the program believing it is safe. Once running, the Trojan performs hidden malicious actions. CompTIA Security+ SY0-701 places Trojans under malware attacks in objective 2.4 (analyze indicators of malicious activity). Unlike viruses or worms, a Trojan does not self-replicate or spread on its own.

**Core Mechanism**
The attacker packages malicious code inside a file that appears trustworthy—an installer, game, utility, document, or update. Social engineering convinces the user to open or run the file. After execution, the Trojan can:
- Open a backdoor that grants remote control
- Install additional malware (ransomware, spyware, keyloggers)
- Steal credentials, files, or system information
- Modify system settings or disable security tools
- Establish persistence through registry keys, scheduled tasks, or services

The Trojan relies entirely on user action for initial execution. It then uses the privileges of the logged-in account (or escalated privileges if it can) to carry out its payload.

**Common Variants**
- **Remote Access Trojan (RAT)**: Creates a covert channel that lets the attacker view the desktop, capture keystrokes, transfer files, activate the webcam or microphone, and issue commands.
- **Banking Trojan**: Targets financial applications and web sessions to intercept login credentials or alter transaction data.
- **Downloader / Dropper**: Delivers and installs other malware after the initial infection.
- **Backdoor Trojan**: Maintains persistent unauthorized access for later use.
- **Fake antivirus or utility Trojan**: Presents itself as security software while actually installing malware or demanding payment.

**Delivery Vectors**
Trojans arrive through the threat vectors listed in objective 2.2:
- Phishing emails with malicious attachments or links
- Drive-by downloads from compromised or malicious websites
- Software downloaded from unofficial sources or torrents
- Infected removable media
- Supply-chain compromise of legitimate software updates
- Social-engineering messages that urge the user to “update” or “install” a required tool

Once the user runs the disguised file, the Trojan activates. Lateral movement may follow if the compromised account has network privileges.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, watch for these signs:
- Unexpected new processes, services, or scheduled tasks
- Outbound connections to unfamiliar external IP addresses or domains (especially high-port or non-standard protocols)
- Sudden appearance of remote-access tools or unusual network listeners
- Modified system files, registry Run keys, or startup entries
- Disabled or altered antivirus / EDR settings
- Unexplained high CPU, disk, or network activity from a newly installed program
- User reports of a program that “looked legitimate” but behaved strangely after installation
- Presence of known Trojan file hashes or behavioral signatures in endpoint logs

RATs often produce periodic beaconing traffic to a command-and-control (C2) server. Banking Trojans may inject code into browser processes or create fraudulent overlay windows.

**Impact on the CIA Triad**
Trojans primarily compromise **confidentiality** by stealing data and credentials. They also damage **integrity** when they alter system configurations or inject malicious code. **Availability** can suffer if the Trojan installs ransomware, launches denial-of-service components, or consumes excessive resources. Persistent backdoors leave the system open to repeated future attacks.

**Associated Threat Actors**
Organized crime groups frequently deploy Trojans for financial theft and as initial access tools for ransomware campaigns. Nation-state actors use sophisticated Trojans and RATs for long-term espionage. Unskilled attackers often download and run pre-built Trojans obtained from dark-web marketplaces. Insider threats may deliberately introduce Trojans, though external delivery remains far more common.

**Mitigation Techniques**
Objective 2.5 techniques that reduce Trojan risk include:
- **Application allow-listing / control**: Permit only approved executables to run.
- **Access control and least privilege**: Limit the damage a Trojan can inflict if executed under a standard user account.
- **Hardening and configuration enforcement**: Disable autorun, restrict script execution, and remove unnecessary administrative rights.
- **Patching**: Close vulnerabilities that Trojans may exploit after initial foothold for privilege escalation.
- **Endpoint detection and response (EDR)**: Detect behavioral anomalies such as unexpected process trees, network connections, or file modifications.
- **User awareness training**: Teach recognition of social-engineering lures that deliver Trojans.

Additional controls include email attachment filtering, web content filtering, and regular integrity checks of critical system files.

**Incident Response Considerations**
Under the incident-response process (objective 4.8):
- **Containment**: Isolate the affected host, block C2 domains or IPs, and disable compromised accounts.
- **Eradication**: Remove the Trojan binary, any dropped secondary malware, and all persistence mechanisms (registry entries, services, scheduled tasks).
- **Recovery**: Restore affected systems from known-clean images or backups and verify that no residual backdoors remain.
- **Lessons learned**: Update detection rules, improve email and download controls, and reinforce user training on executable risks.

Because Trojans often serve as the entry point for more destructive payloads, rapid isolation prevents further lateral movement or data theft.

**Key Exam Distinctions**
A Trojan requires user execution and does not self-propagate. A virus attaches to files and spreads when those files are shared or executed. A worm spreads autonomously across networks without user action. Ransomware focuses on encryption and extortion; a Trojan may deliver ransomware but its defining trait is deception. On the exam, recognize the “looks legitimate but is malicious” characteristic and the reliance on social engineering for delivery.

### Worm

A worm is self-replicating malware that spreads automatically across networks or systems without requiring user action or attachment to a host file. Once active on one host, it seeks additional vulnerable targets and copies itself to them. CompTIA Security+ SY0-701 classifies worms under malware attacks in objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
The worm exploits a vulnerability, weak configuration, or open service to gain initial execution. It then scans the network for other systems that share the same weakness. Upon finding a target, it transfers a copy of itself and begins the process again. Many worms carry a secondary payload—ransomware, backdoors, cryptominers, or denial-of-service tools—that activates after successful propagation. Because the worm does not need a host file or user interaction, it can spread rapidly through an unsegmented network.

**Propagation Characteristics**
Worms typically move by:
- Exploiting unpatched remote-code-execution vulnerabilities
- Brute-forcing or using default credentials on network services (SMB, RDP, SSH)
- Leveraging poorly secured file shares or removable media that auto-execute
- Using email or messaging systems in some hybrid variants, though pure network worms avoid user interaction

Once resident, the worm may create new processes, open listening ports, or modify system configurations to ensure continued operation and further spread.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, look for these signs:
- Sudden spikes in network traffic, especially scanning or connection attempts to many internal hosts
- Rapid appearance of identical processes or files across multiple systems
- High CPU, memory, or bandwidth consumption on multiple endpoints simultaneously
- Unexpected open ports or services appearing on previously clean hosts
- Failed authentication attempts followed by successful logins from the same source across the network
- Deletion or modification of system logs and security tools
- Unusual outbound connections from many hosts to the same external command-and-control address

Worm activity often produces correlated alerts from network detection systems, EDR platforms, and SIEM correlation rules that show sequential infection of adjacent systems.

**Impact on the CIA Triad**
Worms primarily attack **availability** by consuming bandwidth, CPU, and storage as they replicate and scan. They can also degrade **integrity** when they modify system files or install additional malware. **Confidentiality** suffers if the worm includes data-exfiltration or backdoor capabilities. Large-scale worm outbreaks can halt business operations by saturating network links or overloading critical servers.

**Associated Threat Actors**
Organized crime groups deploy worms as delivery mechanisms for ransomware or cryptominers to maximize reach. Nation-state actors occasionally use sophisticated worms for rapid, widespread disruption or as a precursor to deeper compromise. Unskilled attackers may release older or publicly available worm code, producing noisy but still damaging outbreaks. The autonomous nature of worms makes them attractive for any actor seeking speed and scale.

**Mitigation Techniques**
Objective 2.5 techniques that limit worm impact include:
- **Segmentation and isolation**: Restrict lateral movement so a worm cannot freely scan and infect the entire network.
- **Access control and least privilege**: Reduce the credentials and privileges available for the worm to exploit.
- **Hardening and configuration enforcement**: Disable unnecessary services, close unused ports, and eliminate default credentials.
- **Patching**: Close the specific vulnerabilities that worms exploit for remote execution and propagation.
- **Endpoint detection and response**: Identify anomalous process creation, network scanning, and mass file-write behavior characteristic of worms.
- **Network monitoring**: Detect and block unusual scanning patterns and lateral traffic.

Additional controls include application allow-listing, host-based firewalls with strict outbound rules, and timely removal of unused network protocols.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8):
- **Containment**: Isolate infected segments immediately, block the worm’s communication ports or protocols, and disconnect compromised hosts from the network.
- **Eradication**: Remove the worm binary, any secondary payloads, and persistence mechanisms from all affected systems. Verify that the original vulnerability is patched.
- **Recovery**: Rebuild or restore systems from known-clean images and validate that no residual copies remain on network shares or removable media.
- **Lessons learned**: Update network segmentation, accelerate patch cycles for the exploited vulnerability, and refine detection rules for scanning behavior.

Because worms spread autonomously, containment must occur faster than the worm’s replication rate. Isolation of entire network segments often proves more effective than host-by-host remediation during an active outbreak.

**Key Exam Distinctions**
A worm self-replicates and spreads without user action or a host file. A virus requires a host file and typically needs user action to execute and spread. A Trojan relies on deception and user execution but does not self-replicate. On the exam, the defining traits of a worm are autonomous network propagation and the resulting rapid, multi-host impact visible in traffic spikes and sequential infections.

### Spyware

Spyware is malware that secretly monitors a user’s activity, collects sensitive information, and transmits that data to a remote attacker or third party without the user’s knowledge or consent. CompTIA Security+ SY0-701 lists spyware under malware attacks in objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
Once installed, spyware runs quietly in the background. It captures keystrokes, screenshots, browser history, form data, credentials, system configuration details, or microphone and webcam input. The collected information is packaged and sent to a command-and-control server or attacker-controlled location. Many spyware variants also establish persistence through registry keys, scheduled tasks, or browser extensions so they survive reboots. The malware prioritizes stealth: it avoids high CPU usage, disables security alerts when possible, and often disguises its processes under legitimate-looking names.

**Common Variants**
- **Keylogger**: Records every keystroke, including usernames, passwords, and messages.
- **Screen scraper / screenshot tool**: Captures images of the desktop at set intervals or when specific applications open.
- **Browser spyware / hijacker**: Tracks web activity, modifies search results, injects advertisements, or redirects traffic.
- **System monitor**: Collects hardware details, installed software lists, network configuration, and running processes.
- **Mobile spyware**: Targets smartphones and tablets to access location data, call logs, text messages, and app contents.
- **Adware with spyware components**: Displays unwanted advertisements while simultaneously harvesting user data.

**Delivery Vectors**
Spyware reaches systems through the same vectors outlined in objective 2.2:
- Phishing emails or messages that trick users into opening attachments or clicking links
- Bundled installation with free or pirated software
- Drive-by downloads from compromised websites
- Malicious browser extensions or add-ons
- Exploited software vulnerabilities that allow silent installation
- Physical access that enables direct placement of spyware tools

Users often remain unaware because the installation process appears legitimate or occurs without visible prompts.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, watch for these signs:
- Unexpected outbound network connections to unfamiliar domains or IP addresses
- New or unknown processes and services that persist after reboot
- Browser homepage, search engine, or new-tab page changes without user action
- Unusual spikes in disk or network activity during idle periods
- Disabled or repeatedly failing antivirus and firewall components
- Presence of unexpected browser toolbars, extensions, or certificates
- System slowdowns combined with increased data usage
- Log entries showing repeated access to credential stores, browser databases, or user profile folders

Keyloggers may produce small, frequent data transfers. Screen-capture spyware often generates larger periodic uploads.

**Impact on the CIA Triad**
Spyware primarily compromises **confidentiality** by stealing credentials, personal data, intellectual property, and communication content. It can also damage **integrity** when it alters browser settings, injects code, or modifies system files. **Availability** may suffer if the spyware consumes excessive resources or disables security tools that protect the system.

**Associated Threat Actors**
Organized crime groups deploy spyware for credential theft and financial fraud. Nation-state actors use advanced spyware for long-term espionage and intelligence collection. Cybercriminals selling data on dark-web markets also rely on spyware to harvest large volumes of personal information. Insider threats may install spyware deliberately, though external delivery remains more common.

**Mitigation Techniques**
Objective 2.5 techniques that reduce spyware risk include:
- **Access control and least privilege**: Limit the ability of spyware to read sensitive files or install persistence mechanisms.
- **Hardening and configuration enforcement**: Restrict browser extension installation, disable unnecessary services, and enforce application allow-listing.
- **Patching**: Close vulnerabilities that allow silent installation.
- **Endpoint detection and response**: Identify anomalous process behavior, unexpected network connections, and unauthorized access to credential stores.
- **Network monitoring and filtering**: Block known spyware command-and-control domains and detect unusual outbound data patterns.
- **User awareness training**: Teach recognition of phishing and the risks of installing untrusted software or browser extensions.

Additional controls include regular integrity checks of critical system files, browser security policies, and removal of administrative rights from standard user accounts.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8):
- **Containment**: Isolate the affected host, block identified command-and-control destinations, and prevent further data exfiltration.
- **Eradication**: Remove the spyware binary, associated persistence mechanisms, malicious browser extensions, and any secondary payloads.
- **Recovery**: Reset compromised credentials, restore altered browser and system settings, and verify that no residual monitoring components remain.
- **Lessons learned**: Update detection rules for stealthy data-collection behavior, strengthen software installation controls, and reinforce user training on untrusted downloads.

Because spyware focuses on long-term stealthy collection, rapid credential resets and thorough system examination are essential after removal.

**Key Exam Distinctions**
Spyware secretly gathers and transmits information without the user’s knowledge. A Trojan relies on deception to gain execution but may perform many different malicious actions. A keylogger is a specific type of spyware focused on keystroke capture. Adware primarily displays advertisements; when it also harvests data, it crosses into spyware territory. On the exam, the defining traits of spyware are covert monitoring and unauthorized data transmission.

### Bloatware

Bloatware is unwanted pre-installed software that manufacturers or vendors load onto devices before sale. It consumes system resources, adds little or no value for the user, and expands the attack surface. CompTIA Security+ SY0-701 lists bloatware under malware attacks in objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
Vendors install bloatware during the manufacturing or imaging process. The software often runs at startup, places background processes in memory, and may phone home to external servers. Some packages include trial versions of commercial applications, promotional tools, or system utilities that the average user never needs. Because the software starts automatically and holds elevated or persistent privileges, it can collect usage data, display advertisements, or introduce vulnerabilities that attackers later exploit. Removal is frequently difficult because the programs resist standard uninstall methods or reappear after system updates.

**Common Characteristics**
- Pre-loaded trial software and promotional applications
- Manufacturer-specific utilities and support tools that run continuously
- Browser toolbars, search helpers, or homepage changers
- Background services that monitor system health or usage and report data externally
- Mobile apps that request extensive permissions and remain installed by default on smartphones and tablets
- Games, media players, or cloud-storage clients that users did not request

These programs rarely self-replicate or encrypt files, yet they degrade performance and create unnecessary exposure.

**Presence and Delivery**
Bloatware arrives already installed on new computers, laptops, tablets, and mobile devices. It also appears through:
- Vendor system-image updates that reinstall removed components
- Bundled installation packages that slip extra software onto a system during a legitimate download
- OEM recovery partitions that restore the original software load when a user resets the device

Users typically discover bloatware only after noticing slowed performance or unexpected network activity.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, look for these signs:
- Numerous unknown processes and services that start automatically at boot
- High baseline CPU, memory, or disk usage on a newly imaged or factory-reset system
- Unexpected outbound connections from manufacturer-branded or trial software
- Browser settings that change without user action
- Difficulty removing programs through standard uninstall tools
- Repeated reappearance of the same applications after cleanup or Windows updates
- Excessive permissions requested by pre-installed mobile apps

These indicators often appear immediately after a new device is powered on or after a system recovery.

**Impact on the CIA Triad**
Bloatware primarily reduces **availability** by consuming CPU, memory, storage, and network bandwidth. It can compromise **confidentiality** when the software collects and transmits usage data, device identifiers, or user behavior information. **Integrity** may suffer if the packages modify browser settings, install additional components, or introduce vulnerable libraries that attackers later abuse.

**Associated Sources**
Original equipment manufacturers (OEMs), software vendors, and mobile carriers place bloatware on devices to generate revenue through partnerships, trial conversions, or data collection. While not classic cybercriminal malware, the software creates conditions that opportunistic attackers and organized crime groups can exploit. Unskilled users often leave the software in place, maintaining an expanded attack surface.

**Mitigation Techniques**
Objective 2.5 techniques that reduce bloatware risk include:
- **Hardening and configuration enforcement**: Remove or disable unnecessary pre-installed applications and services during system provisioning.
- **Access control and least privilege**: Prevent residual bloatware components from running with elevated rights.
- **Application allow-listing**: Permit only approved software to execute.
- **Endpoint detection and response**: Identify persistent background processes and unexpected network connections originating from manufacturer software.
- **Image management**: Deploy clean, minimal operating-system images instead of vendor-supplied images that contain bloatware.
- **Mobile device management**: Enforce policies that strip or restrict pre-installed apps on smartphones and tablets.

Additional practices include using official vendor removal tools when available and auditing startup programs after every major system update.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8):
- **Containment**: Disable or block network access for the identified bloatware processes to stop data transmission.
- **Eradication**: Uninstall the software using vendor tools, PowerShell, or mobile-device management commands. Remove associated scheduled tasks, services, and registry entries.
- **Recovery**: Verify that performance returns to baseline and that no residual components remain. Re-image the system with a clean baseline if removal proves incomplete.
- **Lessons learned**: Update provisioning checklists to strip bloatware from all new devices and document approved minimal software sets.

Because bloatware often resists casual removal, systematic cleanup during initial device setup prevents long-term exposure.

**Key Exam Distinctions**
Bloatware is unwanted pre-installed software that degrades performance and increases attack surface. It differs from spyware, which actively and secretly harvests data as its primary purpose, and from Trojans, which rely on deception to gain execution. On the exam, recognize bloatware by its presence on new or recovered systems, its resistance to removal, and the resulting resource consumption and expanded attack surface.

### Virus

A virus is malware that attaches itself to a legitimate host file, program, or boot sector. It requires user action to execute and then spreads by infecting additional files. CompTIA Security+ SY0-701 lists viruses under malware attacks in objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
The virus inserts its code into a host file or boot record. When the user opens or runs the infected file, the viral code executes first or alongside the legitimate program. The virus then searches for other suitable targets on the local system or connected storage and inserts copies of itself into those files. Many viruses also deliver a secondary payload—data destruction, backdoors, or further malware—once activated. Because the virus depends on a host file and user execution, it cannot spread autonomously across a network the way a worm does.

**Common Types**
- **File infector**: Attaches to executable files (.exe, .dll, scripts) and activates when the program runs.
- **Boot-sector virus**: Infects the master boot record or boot sector so it loads before the operating system.
- **Macro virus**: Hides inside document macros (Word, Excel, or other office files) and executes when the user enables macros.
- **Polymorphic virus**: Changes its code signature with each infection to evade signature-based detection.
- **Metamorphic virus**: Rewrites its own code completely on each infection while preserving function.
- **Multipartite virus**: Combines multiple infection methods, such as both file and boot-sector techniques.

**Delivery and Propagation**
Viruses reach systems through the vectors in objective 2.2:
- Email attachments that users open
- Infected files downloaded from the internet or shared drives
- Removable media that users insert and access
- Infected software installers or cracked applications
- Documents that prompt users to enable macros

Once executed, the virus spreads locally by infecting other files on the same system or on any writable network share the user can access. It does not independently scan and exploit remote hosts.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, look for these signs:
- Unexpected changes to file sizes, hashes, or modification timestamps
- Programs that behave abnormally or crash after previously working normally
- Appearance of unfamiliar files or file extensions
- Antivirus alerts for known viral signatures or heuristic detections
- Boot failures or unusual messages during system startup
- Macro warnings that appear more frequently than expected
- Sudden loss of files or corruption of documents after opening an attachment

Polymorphic and metamorphic viruses may produce fewer consistent signatures, so behavioral indicators and file-integrity monitoring become more important.

**Impact on the CIA Triad**
Viruses primarily damage **integrity** by altering host files and system components. They can also reduce **availability** when the payload deletes data, corrupts the boot process, or consumes resources. **Confidentiality** suffers if the virus steals information or installs additional spyware or backdoors.

**Associated Threat Actors**
Organized crime groups and unskilled attackers both distribute viruses, often as delivery vehicles for more profitable payloads such as ransomware or credential stealers. Nation-state actors occasionally use highly sophisticated polymorphic or targeted viruses for sabotage or persistent access. The dependence on user action makes viruses common in phishing and social-engineering campaigns.

**Mitigation Techniques**
Objective 2.5 techniques that limit virus risk include:
- **Hardening and configuration enforcement**: Disable unnecessary macros, restrict script execution, and enforce application allow-listing.
- **Access control and least privilege**: Reduce the ability of an infected process to modify critical system files or infect network shares.
- **Patching**: Keep applications and operating systems updated so secondary exploits inside the virus payload are less effective.
- **Endpoint detection and response**: Detect anomalous file modifications, process injections, and known viral behaviors.
- **Email and web filtering**: Block common infection vectors before users can open them.
- **User awareness training**: Teach recognition of suspicious attachments and the risks of enabling macros.

Additional controls include regular file-integrity monitoring and timely antivirus signature updates.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8):
- **Containment**: Isolate the affected host and disconnect shared storage to stop further file infection.
- **Eradication**: Remove the virus from all infected files using updated antivirus tools or restore clean copies from backups. Repair or replace damaged boot sectors.
- **Recovery**: Verify system integrity, restore any deleted or corrupted data, and confirm that no residual viral code remains.
- **Lessons learned**: Update detection rules, strengthen macro and attachment policies, and reinforce user training on execution risks.

Because viruses hide inside legitimate files, thorough scanning of all accessible storage and verification of file hashes are required for complete cleanup.

**Key Exam Distinctions**
A virus attaches to a host file and requires user action to execute and spread. A worm self-replicates across networks without a host file or user interaction. A Trojan disguises itself as legitimate software but does not infect other files. On the exam, the defining traits of a virus are host-file dependence and the need for user execution to propagate.

### Keylogger

A keylogger is malware or a hardware device that records every keystroke a user types. It captures usernames, passwords, messages, credit-card numbers, and other sensitive input, then stores or transmits the data to an attacker. CompTIA Security+ SY0-701 lists keyloggers under malware attacks in objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
Software keyloggers install on the target system and hook into the operating system’s input stream or browser processes. Every keystroke passes through the keylogger before reaching the intended application. The malware buffers the captured data and periodically sends it to a remote server or writes it to a hidden local file. Hardware keyloggers sit between the keyboard and the computer (inline adapters, modified cables, or compromised peripherals) and record keystrokes independently of the operating system. Both forms aim for stealth so the user continues typing normally while the attacker collects credentials and confidential information.

**Common Variants**
- **Software keylogger**: Runs as a process, service, or injected module on the host operating system or inside a browser.
- **Hardware keylogger**: Physical device placed on the keyboard cable, USB port, or inside the keyboard itself.
- **Kernel-level keylogger**: Operates at a low system level to evade many user-mode detection tools.
- **Form-grabbing keylogger**: Captures data directly from web forms before encryption, bypassing HTTPS protection on the wire.
- **Mobile keylogger**: Targets smartphones and tablets to record virtual-keyboard input, text messages, and app credentials.

**Delivery Vectors**
Keyloggers reach systems through the vectors in objective 2.2:
- Phishing emails or malicious downloads that install software keyloggers
- Trojans or other malware that drop a keylogger as a secondary payload
- Physical access that allows an attacker to attach a hardware keylogger
- Compromised or counterfeit peripherals supplied through the supply chain
- Exploited software vulnerabilities that permit silent installation
- Malicious browser extensions that monitor typed input

Software variants often arrive bundled with other malware; hardware variants require brief physical or supply-chain access.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, look for these signs:
- Unexpected processes or services that remain resident and access keyboard or input APIs
- Outbound network connections that transfer small, regular amounts of data
- Hidden log files that grow as the user types
- Unusual browser extensions or injected scripts that monitor form submissions
- Hardware devices or USB adapters that do not match the expected keyboard inventory
- Antivirus or EDR alerts for known keylogger signatures or behavioral hooks
- System slowdowns or input lag that coincide with new software installations

Kernel-level and form-grabbing keyloggers may produce fewer obvious file-system artifacts, making network and behavioral monitoring essential.

**Impact on the CIA Triad**
Keyloggers primarily compromise **confidentiality** by stealing credentials, personal messages, financial data, and intellectual property. They can also damage **integrity** if the attacker uses the stolen information to alter accounts or systems. **Availability** is rarely the direct target, although poorly written keyloggers may introduce input lag or instability.

**Associated Threat Actors**
Organized crime groups deploy keyloggers for credential theft and financial fraud. Nation-state actors use advanced keyloggers for long-term espionage against high-value targets. Insider threats may install hardware or software keyloggers to capture colleagues’ credentials. Unskilled attackers often obtain ready-made keylogger tools from underground markets.

**Mitigation Techniques**
Objective 2.5 techniques that reduce keylogger risk include:
- **Access control and least privilege**: Limit the ability of untrusted software to install input hooks or run with elevated rights.
- **Hardening and configuration enforcement**: Restrict software installation, disable unnecessary browser extensions, and enforce application allow-listing.
- **Endpoint detection and response**: Detect abnormal process behavior, API hooking, and unexpected access to keyboard input streams.
- **Network monitoring**: Identify regular small data exfiltration patterns characteristic of keyloggers.
- **Physical security**: Control access to workstations and inspect keyboard cables and USB ports for unauthorized devices.
- **User awareness training**: Teach recognition of phishing and the risks of installing untrusted software or peripherals.
- **Multifactor authentication**: Reduce the value of stolen passwords even if a keylogger succeeds.

Additional controls include secure attention key sequences, on-screen keyboards for sensitive entry, and regular peripheral inventories.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8):
- **Containment**: Isolate the affected host, block identified exfiltration destinations, and remove any physical keylogger devices.
- **Eradication**: Remove the software keylogger, associated persistence mechanisms, and any secondary malware. Replace compromised hardware keyboards or adapters.
- **Recovery**: Reset all credentials that may have been typed while the keylogger was active, restore system integrity, and verify that no residual monitoring components remain.
- **Lessons learned**: Update detection rules for input-hooking behavior, strengthen physical access controls, and reinforce policies on peripheral devices and software installation.

Because keyloggers capture data over time, assume that all credentials entered during the infection window are compromised and require immediate rotation.

**Key Exam Distinctions**
A keylogger specifically records keystrokes and input data. It is a specialized form of spyware focused on credential and information theft. A general spyware program may collect broader system or behavioral data; a Trojan may deliver a keylogger but is defined by deception rather than keystroke capture. On the exam, the defining trait of a keylogger is the covert recording of typed input for later exfiltration or local storage.

### Logic bomb

A logic bomb is malware that remains dormant until a predefined condition is met, then executes a malicious payload. The trigger can be a specific date, time, event, or system state. CompTIA Security+ SY0-701 lists logic bombs under malware attacks in objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
An attacker or malicious insider inserts code that checks continuously or periodically for its trigger condition. Until the condition occurs, the code produces no visible effect and often hides inside legitimate programs, scripts, or scheduled tasks. When the trigger activates—such as a calendar date, the deletion of a specific user account, or the absence of a required file—the logic bomb releases its payload. The payload may delete files, corrupt data, encrypt systems, create backdoors, or shut down services. Because the malicious activity is delayed, the logic bomb can evade detection for long periods.

**Common Triggers**
- Date or time (time bomb)
- Launch of a particular application
- Login of a specific user account
- Deletion or modification of a named file or user
- Absence of a required “keep-alive” file or process
- System uptime or performance threshold
- Network connectivity or domain-join status

The trigger logic is usually simple and embedded directly in the code so that the bomb activates automatically without further attacker interaction.

**Placement and Delivery**
Logic bombs reach systems through the vectors in objective 2.2 and through insider access:
- Malicious code inserted into legitimate scripts, scheduled tasks, or application source
- Trojans or other malware that install a logic bomb as a delayed payload
- Insider placement by a disgruntled employee or contractor with privileged access
- Compromised software updates or supply-chain packages that include conditional malicious code

Because the bomb can sit quietly for months or years, it is frequently planted by individuals who expect to be gone when the trigger fires.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, look for these signs:
- Unexpected destructive actions that occur on a precise date or after a specific event
- Scheduled tasks, scripts, or services that contain conditional logic tied to dates, usernames, or file existence
- Code or configuration that checks for the presence or absence of particular files or accounts
- Sudden file deletions, service stops, or system changes that coincide with a known trigger event
- Audit logs showing creation of unusual scheduled tasks or modification of startup scripts by a privileged user
- Absence of continuous command-and-control traffic (the bomb does not need ongoing external contact)

Detection often occurs only after the payload activates, making proactive code and scheduled-task review essential.

**Impact on the CIA Triad**
Logic bombs primarily damage **integrity** and **availability** by deleting, corrupting, or encrypting data and by disrupting services when the trigger fires. **Confidentiality** may also suffer if the payload includes data exfiltration or the creation of persistent backdoors. The delayed nature of the attack can magnify impact because the organization may have reduced monitoring or changed personnel by the time the bomb detonates.

**Associated Threat Actors**
Insider threats are the most common source of logic bombs; a departing employee or contractor plants the code to retaliate after access is removed. Organized crime and nation-state actors occasionally embed logic bombs inside other malware to create timed disruption or to destroy evidence after a mission window closes. Unskilled attackers rarely create sophisticated logic bombs, though simple time-based scripts appear in some basic malware kits.

**Mitigation Techniques**
Objective 2.5 techniques that reduce logic-bomb risk include:
- **Access control and least privilege**: Limit who can create or modify scheduled tasks, scripts, and startup programs.
- **Hardening and configuration enforcement**: Restrict the ability to install unauthorized code and enforce change-management processes.
- **Endpoint detection and response**: Monitor for new or altered scheduled tasks, unusual conditional logic in scripts, and unexpected file or service changes.
- **Code and configuration review**: Audit scripts, scheduled tasks, and application code for suspicious date checks or event-driven conditions.
- **Logging and monitoring**: Record creation and modification of scheduled tasks and privileged actions so investigators can trace placement.
- **Separation of duties**: Ensure no single individual can both plant and conceal a logic bomb without oversight.

Additional controls include regular integrity checks of critical scripts and automated alerts for new scheduled tasks.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8):
- **Containment**: Disable the triggering mechanism if still dormant, isolate affected systems, and prevent further payload execution.
- **Eradication**: Remove the logic-bomb code, associated scheduled tasks, and any secondary payloads. Review all similar scripts and tasks across the environment.
- **Recovery**: Restore deleted or corrupted data from clean backups and verify that no residual conditional code remains.
- **Lessons learned**: Strengthen change-control processes, improve monitoring of privileged actions, and update detection rules for date-based or event-based conditions.

Because logic bombs can be planted long before activation, forensic examination of historical logs and code repositories is often required to identify the responsible party.

**Key Exam Distinctions**
A logic bomb stays inactive until a specific condition is met, then executes its payload. A virus or worm begins its activity upon execution and focuses on replication. A Trojan relies on deception for delivery but does not inherently wait for a future trigger. On the exam, the defining trait of a logic bomb is the delayed, condition-based activation of a malicious action.

### Rootkit

A rootkit is malware that conceals its own presence and the presence of other malicious components by modifying the operating system or firmware. It grants the attacker privileged (root or administrator) access while actively hiding files, processes, network connections, and registry entries from standard detection tools. CompTIA Security+ SY0-701 lists rootkits under malware attacks in objective 2.4 (analyze indicators of malicious activity).

**Core Mechanism**
Once installed with elevated privileges, the rootkit intercepts or alters system calls, kernel functions, or boot processes. It filters the information returned to user-mode tools so that antivirus software, task managers, and directory listings never display the hidden malware. Some rootkits operate in kernel mode for deep control; others reside in the boot process or firmware so they load before the operating system and security tools. The rootkit maintains persistence across reboots and often provides a backdoor for continued remote access. Its primary goal is long-term stealth rather than immediate destructive action.

**Common Types**
- **User-mode rootkit**: Operates at the application level by hooking API calls. Easier to detect than deeper variants.
- **Kernel-mode rootkit**: Modifies the operating-system kernel to intercept system calls and hide objects at a low level.
- **Bootkit / boot-sector rootkit**: Infects the master boot record or bootloader so it loads before the operating system.
- **Firmware rootkit**: Embeds itself in device firmware (BIOS/UEFI, network card, hard-drive controller) and survives operating-system reinstallation.
- **Hypervisor-level rootkit**: Runs beneath the operating system by installing a thin virtualization layer that the host OS cannot easily see.

**Installation and Delivery**
Rootkits reach systems through the vectors in objective 2.2 and through privilege escalation:
- Exploitation of software vulnerabilities that allow code execution with elevated rights
- Trojans or other malware that drop a rootkit after initial compromise
- Physical or supply-chain access that permits firmware or boot-sector modification
- Social-engineering attacks that trick administrators into running privileged installers
- Lateral movement after an attacker has already obtained administrator credentials

Successful installation almost always requires administrator or SYSTEM-level privileges at the moment of deployment.

**Indicators of Malicious Activity**
When analyzing a scenario under objective 2.4, look for these signs:
- Processes, files, or network connections that appear in low-level tools but remain invisible to standard utilities
- Unexpected discrepancies between different system-information tools (for example, one tool lists a process while another does not)
- Disabled or malfunctioning security software that cannot be re-enabled
- Unusual system behavior such as unexplained network traffic or performance degradation without corresponding visible processes
- Failed integrity checks of system files, boot records, or firmware
- Presence of unknown kernel modules, drivers, or boot-time components
- Alerts from specialized rootkit-detection tools that examine memory or raw disk structures

Because rootkits actively hide evidence, conventional antivirus scans often return clean results even while the system remains compromised.

**Impact on the CIA Triad**
Rootkits primarily compromise **confidentiality** by enabling long-term undetected access and data theft. They damage **integrity** by altering operating-system components, boot processes, and security tools. **Availability** can suffer if the rootkit destabilizes the system or if removal requires extensive recovery procedures. The persistent, privileged access a rootkit provides multiplies the impact of any additional malware it protects.

**Associated Threat Actors**
Nation-state actors frequently deploy sophisticated rootkits and bootkits for long-term espionage. Organized crime groups use rootkits to protect ransomware, banking Trojans, or credential stealers from detection. Advanced persistent threat teams rely on rootkits to maintain stealthy footholds after initial compromise. Unskilled attackers rarely create or successfully deploy kernel- or firmware-level rootkits.

**Mitigation Techniques**
Objective 2.5 techniques that reduce rootkit risk include:
- **Access control and least privilege**: Prevent attackers from obtaining the elevated rights required to install most rootkits.
- **Hardening and configuration enforcement**: Enable secure boot, measured boot, and driver-signature enforcement to block unauthorized low-level code.
- **Patching**: Close the privilege-escalation and remote-code-execution vulnerabilities that allow rootkit installation.
- **Endpoint detection and response**: Use tools capable of memory analysis, boot-sector inspection, and behavioral detection of system-call hooking.
- **Integrity monitoring**: Continuously verify critical system files, boot records, and firmware hashes against known-good baselines.
- **Application allow-listing and secure configuration**: Limit the ability to load unsigned drivers or modify boot components.

Additional controls include UEFI secure boot, trusted platform modules, and regular firmware updates from trusted sources.

**Incident Response Considerations**
Under the incident-response lifecycle (objective 4.8):
- **Containment**: Isolate the affected host from the network to prevent further command-and-control activity or lateral movement.
- **Eradication**: Remove the rootkit using specialized anti-rootkit tools, offline scanning, or, in severe cases, complete operating-system and firmware reinstallation from trusted media. Bootkits and firmware rootkits often require firmware re-flashing or hardware replacement.
- **Recovery**: Restore systems from known-clean images, re-apply security baselines, and verify that secure boot and integrity controls are active.
- **Lessons learned**: Strengthen privilege management, improve detection of low-level anomalies, and update boot and firmware security policies.

Because rootkits can survive ordinary operating-system reinstallation, responders must examine and, if necessary, re-flash firmware and boot components.

**Key Exam Distinctions**
A rootkit focuses on hiding itself and other malware while maintaining privileged access. A Trojan relies on deception for delivery but does not inherently conceal system objects. A virus or worm prioritizes replication. Spyware emphasizes data collection. On the exam, the defining traits of a rootkit are stealth, system-level or firmware-level persistence, and the active concealment of files, processes, and network activity.

## Physical attacks
### Brute force
### Radio frequency identification (RFID) cloning
### Environmental
## Network attacks
### Distributed denial-of-service (DDoS)
**Amplified**
**Reflected**
### Domain Name System (DNS) attacks
### Wireless
### On-path
### Credential replay
### Malicious code
## Application attacks
### Injection
### Buffer overflow
### Replay
### Privilege escalation
### Forgery
### Directory traversal
## Cryptographic attacks
### Downgrade
### Collision
### Birthday
## Password attacks
### Spraying
### Brute force
## Indicators
### Account lockout
### Concurrent session usage
### Blocked content
### Impossible travel
### Resource consumption
### Resource inaccessibility
### Out-of-cycle logging
### Published/documented
### Missing logs
