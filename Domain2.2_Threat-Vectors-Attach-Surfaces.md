# CompTIA Security+ (SY0-701) Domain 2.2 Explain common threat vectors and attack surfaces.

Domain 2.2 of CompTIA Security+ SY0-701 examines the primary pathways attackers use to reach systems and people. Threat vectors span message-based channels, visual and file-based delivery, voice and physical media, vulnerable and unsupported software, unsecure and wireless networks, open services, default credentials, and the extended supply chain. Human-focused social-engineering techniques further exploit trust and urgency. Understanding these vectors allows organizations to map real attack surfaces and apply layered controls that address both technical exposure and human susceptibility.

## Message-based

Message-based vectors exploit human trust in everyday communication channels to deliver malware, steal credentials, and initiate fraud. Email remains the highest-volume and most versatile channel for phishing, malicious attachments, and business-email compromise. SMS extends similar social-engineering techniques to mobile devices through smishing and one-time-password interception. Instant messaging leverages both consumer and enterprise collaboration platforms to reach users inside trusted conversations. Because these channels are designed for rapid, informal exchange, technical filtering alone is insufficient; effective defense combines secure configuration, multi-factor authentication, continuous monitoring, and sustained user awareness.

### Email

Email remains one of the most frequently exploited threat vectors. Attackers use it to deliver malware, harvest credentials, and initiate business-email compromise or social-engineering campaigns.

Common attack techniques include phishing messages that impersonate trusted entities, spear-phishing that targets specific individuals with personalized content, malicious attachments that execute code when opened, and embedded links that direct victims to credential-harvesting sites or exploit kits. Business-email compromise often involves account takeover or spoofed executive messages that instruct employees to transfer funds or release sensitive data.

Email succeeds as a vector because it is universally used, crosses network boundaries by design, and relies heavily on human judgment. Once a user interacts with a malicious message, the attacker can bypass many perimeter controls and establish a foothold inside the environment.

Defenders reduce email risk through layered controls: secure email gateways that inspect attachments and links, DMARC/DKIM/SPF authentication to detect spoofing, URL rewriting and sandbox detonation of attachments, user-awareness training, and rapid reporting channels for suspicious messages. Multi-factor authentication limits the value of stolen credentials obtained through phishing. Continuous monitoring of mailbox activity and outbound transfers helps detect successful compromises after initial delivery.

Because email combines technical delivery with social engineering, effective protection requires both technological filtering and sustained human vigilance.

### Short Message Service (SMS)

SMS serves as a high-reach threat vector that delivers social-engineering and malware content directly to mobile devices. Attackers exploit the trust users place in text messages and the limited security controls available on many messaging channels.

Common techniques include smishing (SMS phishing) that impersonates banks, delivery services, or internal IT teams; messages containing malicious links that lead to credential-harvesting pages or malware downloads; and one-time-password interception or SIM-swapping attacks that bypass SMS-based multi-factor authentication. Because SMS messages often appear on locked screens and carry a sense of urgency, users frequently interact with them before applying critical evaluation.

SMS lacks the rich authentication and filtering infrastructure available for email. Spoofing of sender identifiers remains straightforward on many networks, and end-to-end encryption is absent from standard SMS. Once a user clicks a link or replies with sensitive information, the attacker gains credentials, session tokens, or a pathway onto the device.

Defenders reduce SMS risk through user-awareness training that specifically addresses text-based social engineering, adoption of stronger multi-factor methods that do not rely on SMS, mobile-threat-defense solutions that inspect device traffic and installed applications, and organizational policies that discourage the use of SMS for sensitive authentication or transaction approval. Monitoring for anomalous account activity after potential SMS compromise provides a final detection layer.

### Instant messaging (IM)

Instant messaging platforms serve as a threat vector by delivering social-engineering content, malicious links, and files directly into trusted communication channels. Attackers exploit both consumer applications and enterprise collaboration tools.

Common techniques include phishing messages that impersonate colleagues or executives, malicious file transfers that execute malware when opened, and link-based credential harvesting. Business-email-compromise style attacks increasingly migrate into instant-messaging channels where urgency and familiarity reduce user scrutiny. Compromised accounts within the messaging platform allow attackers to leverage existing trust relationships and contact lists.

Enterprise instant-messaging systems that integrate with file storage, calendars, and identity providers expand the potential impact of a single compromised account. Consumer applications used for work discussions create shadow-IT channels that bypass official monitoring and data-loss-prevention controls.

Defenders reduce risk through secure configuration of enterprise messaging platforms, enforcement of multi-factor authentication, link and attachment scanning, data-loss-prevention policies that restrict sensitive content, and user training that addresses messaging-specific social engineering. Network controls and cloud-access security brokers can limit unsanctioned messaging applications. Continuous monitoring of unusual messaging activity—especially requests for funds, credentials, or sensitive files—provides early detection of account takeover or insider misuse.

## Image-based

Image-based threat vectors embed malicious content or instructions inside graphic files so that users or automated systems process the image and trigger an attack. The visual appearance remains ordinary, reducing suspicion.

Attackers conceal payloads through steganography, embed malicious code in malformed image files that exploit parser vulnerabilities, or place QR codes that direct mobile devices to phishing sites or malware downloads. Image-based phishing inserts convincing logos or screenshots into messages to increase credibility. Some attacks rely on the image itself executing code when rendered by a vulnerable library or application.

Because images are routinely exchanged in email, messaging platforms, documents, and web pages, they cross security boundaries with minimal inspection. Traditional signature-based detection often fails when the malicious content is hidden or encoded inside legitimate-looking graphics.

Defenders reduce risk by inspecting images for anomalies, restricting automatic rendering of untrusted images, scanning QR codes before use, keeping image-processing libraries patched, and training users to treat unexpected images and QR codes with the same caution applied to links and attachments. Content-disarm-and-reconstruction techniques and sandbox detonation of image files provide additional protection for high-risk environments.

## File-based

File-based threat vectors deliver malicious code or scripts inside documents, executables, archives, or other file types that users or systems open. The file itself becomes the initial access mechanism.

Common carriers include Office documents with malicious macros, PDFs containing embedded exploits, compressed archives that hide executables, and seemingly legitimate installers or updates that package malware. Attackers distribute these files through email attachments, cloud-storage links, removable media, software-download sites, and collaboration platforms. Once opened, the file may execute code, abuse legitimate application features, or exploit vulnerabilities in the parsing software.

File-based attacks succeed because organizations routinely exchange documents and users are conditioned to open them. Modern payloads frequently employ living-off-the-land techniques, macro auto-execution, or double-extension tricks to bypass basic filtering.

Defenders reduce risk through secure email and web gateways that inspect and detonate files, strict application allow-listing, macro restrictions, sandbox analysis of unknown files, endpoint detection that monitors post-execution behavior, and user training that emphasizes caution with unexpected attachments. Keeping document readers and archive utilities patched closes many of the vulnerabilities that file-based exploits target. Content disarmament and reconstruction can strip active content while preserving usability for lower-risk workflows.

## Voice call

Voice calls serve as a threat vector by enabling real-time social engineering that bypasses many technical controls. Attackers use telephone or VoIP channels to impersonate trusted parties and manipulate victims into performing actions or disclosing information.

Common techniques include vishing (voice phishing) that impersonates IT support, banks, executives, or government agencies; callback schemes that instruct victims to call a number controlled by the attacker; and voice deepfakes that clone a known individual’s speech patterns to increase credibility. The attacker builds urgency or authority during the conversation, pressuring the target to reveal credentials, approve transactions, install remote-access software, or disable security controls.

Voice calls succeed because they convey immediacy and personal presence that email or text messages lack. Caller-ID spoofing further reduces suspicion. Once the victim complies, the attacker gains credentials, financial transfers, or a foothold on systems without needing to exploit technical vulnerabilities.

Defenders reduce risk through user-awareness training that addresses voice-based social engineering, verification procedures that require out-of-band confirmation for sensitive requests, multi-factor authentication that limits the value of verbally obtained credentials, and call-filtering or anti-spoofing technologies where available. Organizations establish clear policies that prohibit the disclosure of credentials or the approval of high-risk actions solely on the basis of a phone call. Rapid reporting channels allow employees to escalate suspicious calls before damage occurs.

## Removable device

Removable devices serve as a physical threat vector that introduces malware, exfiltrates data, or bypasses network-based controls. USB drives, external hard disks, memory cards, and similar media move freely between systems and networks.

Attackers load malware onto removable media and distribute it through social engineering, opportunistic drops in public areas, or supply-chain insertion. When a user inserts the device, autorun features, human curiosity, or exploitation of operating-system vulnerabilities can execute the payload. Conversely, insiders or external actors with physical access use removable devices to copy sensitive data and carry it out of controlled environments, circumventing egress monitoring on the network.

Removable media also introduce unpatched or infected systems into otherwise protected networks when users connect personal devices. Because the vector relies on physical access or user interaction, traditional network perimeter defenses provide limited protection.

Defenders reduce risk through technical controls that restrict or disable removable-media use, enforce device encryption and allow-listing, scan inserted media automatically, and monitor for anomalous file transfers to external storage. Endpoint policies can require administrator approval before mounting unknown devices. Physical security measures and user training that discourage the use of untrusted media further shrink the attack surface. In high-security environments, organizations often prohibit removable media entirely or limit it to approved, centrally managed devices.

## Vulnerable software

Vulnerable software constitutes a primary attack surface when applications or operating systems contain exploitable flaws. Attackers locate these weaknesses and use them to execute unauthorized code, escalate privileges, or gain persistent access.

Vulnerabilities arise from coding errors, insecure design, improper configuration, or failure to apply security updates. Common examples include buffer overflows, injection flaws, broken authentication, insecure deserialization, and unpatched known CVEs. Once an attacker identifies a reachable vulnerable component—whether a public-facing web application, a desktop program, or a background service—the attacker crafts an exploit that triggers the flaw and delivers a payload.

Software remains vulnerable for extended periods when organizations delay patching, use end-of-life products that no longer receive updates, or deploy custom applications that never undergo security testing. Third-party libraries and open-source components introduce additional risk because the organization may not track or update them promptly.

Defenders reduce exposure through continuous vulnerability scanning, disciplined patch management, application allow-listing, network segmentation that limits reachability of vulnerable services, and secure-development practices that catch flaws before release. Software bills of materials help identify vulnerable third-party components. When immediate patching is impossible, compensating controls such as virtual patching, stricter access restrictions, or enhanced monitoring temporarily reduce risk until a permanent fix is applied.

### Client-based vs. agentless

Security tools collect data and enforce controls through two primary architectural approaches: client-based (agent-based) and agentless.

**Client-based (agent-based)** solutions install a persistent software agent on each endpoint or server. The agent runs continuously, collects detailed telemetry, enforces policies, and communicates with a central management platform. Because the agent has local presence, it can inspect processes, memory, files, and network activity even when the system is offline or outside the corporate network. Agents enable real-time detection, immediate response actions such as isolation or process termination, and consistent policy enforcement. The trade-off is the operational overhead of deploying, updating, and monitoring the agents themselves, plus the potential performance impact on the host.

**Agentless** solutions operate without installing software on the target systems. They gather information remotely through protocols such as SSH, WinRM, WMI, SNMP, or API calls, or by examining network traffic and configurations from a central scanner. Agentless approaches simplify deployment, avoid agent-related performance or compatibility issues, and work well for devices that cannot support agents (certain network appliances, legacy systems, or ephemeral cloud instances). Visibility is typically limited to periods when the system is reachable and to the data exposed by the remote interfaces; real-time blocking and deep endpoint telemetry are generally unavailable.

Organizations often combine both models. Agents protect critical or high-risk endpoints that require continuous monitoring and response, while agentless scanning covers a broader population of devices for configuration assessment, vulnerability discovery, and periodic compliance checks. Selection depends on required depth of visibility, real-time response needs, device diversity, and operational capacity to manage agents.

## Unsupported systems and applications

Unsupported systems and applications are platforms that no longer receive security updates, patches, or vendor maintenance. They remain in production yet lack remediation for newly discovered vulnerabilities, creating a persistent and expanding attack surface.

Once a vendor declares end-of-life or end-of-support, the organization must either replace the system or accept that every subsequent vulnerability will remain unpatched. Attackers deliberately scan for and target these known-weak platforms because exploits remain effective indefinitely. Legacy operating systems, outdated applications, industrial-control devices, and medical equipment frequently fall into this category.

Unsupported software also complicates compliance, logging, and integration with modern security tools. Compensating controls become necessary: network isolation, strict access restrictions, application-layer gateways, enhanced monitoring, and virtual patching through intrusion-prevention systems. These measures reduce but do not eliminate risk.

Organizations inventory all unsupported assets, assess business criticality, and establish migration or isolation timelines. Risk-acceptance documentation records residual exposure for systems that cannot be immediately replaced. Long-term reliance on unsupported technology increases the likelihood of successful exploitation and raises the cost of eventual remediation.

## Unsecure networks

Unsecure networks are communication environments that lack adequate authentication, encryption, or access controls, allowing attackers to intercept, modify, or inject traffic with relative ease. Public Wi-Fi, open guest networks, misconfigured corporate wireless, and poorly segmented internal segments commonly fall into this category.

Attackers on an unsecure network perform eavesdropping, man-in-the-middle attacks, session hijacking, and credential harvesting. They may operate rogue access points that mimic legitimate SSIDs, conduct ARP or DNS spoofing, or simply capture unencrypted data that traverses the shared medium. Devices that automatically join previously seen open networks become especially vulnerable.

Because the network itself provides no trustworthy boundary, any system that connects inherits elevated risk. Data in transit, authentication exchanges, and even encrypted sessions that do not properly validate certificates can be compromised.

Defenders reduce exposure by treating all non-controlled networks as hostile. Organizations enforce VPN use for remote and public connections, disable automatic Wi-Fi joining, require strong encryption and mutual authentication on corporate wireless, and apply network-access-control policies that limit privileges of devices arriving from untrusted networks. Endpoint protections—including certificate pinning, encrypted DNS, and continuous monitoring—provide additional safeguards when users must operate on networks the organization does not control. User training reinforces the practice of avoiding sensitive transactions on any network that cannot be verified as secure.

### Wireless

Wireless networks expand the attack surface by transmitting data over radio frequencies that leave the physical boundaries of a facility. Attackers within signal range can intercept traffic, inject frames, or impersonate legitimate access points without physical access to wired infrastructure.

Common techniques include eavesdropping on unencrypted or weakly encrypted traffic, setting up rogue or evil-twin access points that trick clients into connecting, deauthentication attacks that force stations to reassociate, and exploitation of protocol weaknesses in WEP, WPA, or misconfigured WPA2/WPA3 implementations. Attackers also target wireless management interfaces, exploit insecure guest networks, and abuse poorly segmented IoT or BYOD devices that join the same radio environment.

Because wireless signals propagate beyond walls, traditional perimeter controls provide incomplete protection. Clients may automatically reconnect to previously seen SSIDs, enabling association with malicious access points that spoof trusted names.

Defenders reduce wireless risk through strong encryption (WPA3 where available, otherwise properly configured WPA2-Enterprise), mutual authentication via 802.1X, disabling legacy protocols, continuous wireless intrusion detection and prevention, strict segmentation of guest and IoT traffic, and regular surveys for rogue devices. Client hardening—including certificate validation and prohibition of automatic connection to open networks—further limits exposure. Physical placement of access points and transmit-power control help constrain signal leakage beyond controlled areas.

### Wired

Wired networks provide a physical transmission path that attackers can exploit when they gain access to cabling, switches, or network jacks. Although wired links do not radiate signals beyond the cable, physical proximity or insider access converts them into a viable threat vector.

Attackers insert unauthorized devices into open ports, perform MAC address spoofing, conduct ARP poisoning on local segments, or tap cabling to intercept unencrypted traffic. Compromised switches or misconfigured VLANs allow lateral movement across otherwise separated network zones. Physical access to a network drop in a conference room, lobby, or unsecured office can grant direct connectivity to internal segments that wireless attackers cannot reach without credentials.

Because many organizations still treat internal wired networks as relatively trusted, traffic on these segments often lacks the encryption and strong authentication applied to external or wireless connections. Once an attacker attaches to the wired infrastructure, traditional perimeter firewalls provide little protection.

Defenders reduce wired risk through port security, 802.1X network access control, continuous monitoring for unauthorized devices, encryption of sensitive internal traffic, strict physical security of network closets and cabling, and disablement of unused ports. Network segmentation and micro-segmentation further limit the value of any single compromised jack or switch port. Regular discovery scans and infrastructure integrity checks help detect unauthorized changes to the wired topology.

### Bluetooth

Bluetooth provides a short-range wireless threat vector that attackers exploit to compromise devices, intercept data, or establish unauthorized connections. Its convenience and frequent default configurations expand the attack surface on mobile devices, headsets, keyboards, and IoT endpoints.

Common techniques include bluejacking (unsolicited messages), bluesnarfing (unauthorized data access), BlueBorne-style remote code execution, and pairing hijacks that allow an attacker to impersonate a trusted peripheral. Attackers also exploit weak or legacy pairing mechanisms, eavesdrop on unencrypted traffic, and use Bluetooth as a covert command-and-control channel or data-exfiltration path once a device is compromised.

Because Bluetooth operates independently of the corporate Wi-Fi or wired network, traditional network security controls do not inspect its traffic. Devices in discoverable mode or those that automatically accept pairing requests become easy targets in public spaces or dense office environments.

Defenders reduce Bluetooth risk by disabling the interface when it is not required, enforcing non-discoverable mode, requiring strong pairing authentication, keeping device firmware updated, and applying mobile-device management policies that control Bluetooth use. Endpoint detection and network monitoring can surface anomalous Bluetooth activity. In high-security environments, organizations prohibit Bluetooth entirely or restrict it to approved, centrally managed accessories.

## Open service ports

Open service ports expose network services to potential interaction and therefore constitute a direct attack surface. Each listening port represents a possible entry point that an attacker can probe, fingerprint, and exploit.

Unnecessary or poorly secured ports allow reconnaissance, brute-force authentication attempts, and exploitation of vulnerable services. Common high-risk examples include exposed remote-desktop, database, administrative web interfaces, and legacy protocols that transmit credentials in cleartext. Attackers systematically scan large address ranges for open ports, identify the running service and version, then apply known exploits or credential attacks.

Even services that require authentication expand the attack surface by revealing their presence and offering a target for password spraying or zero-day exploitation. When open ports face the internet without additional filtering, the risk increases dramatically.

Defenders reduce exposure through continuous port scanning and inventory, strict host-based and network firewall rules that permit only required traffic, disablement of unused services, and placement of administrative interfaces behind VPN or jump-host controls. Network segmentation further limits the reachability of internal service ports. Regular vulnerability scanning of listening services and prompt patching close the pathways that open ports otherwise provide. The principle of least functionality—running only necessary services—remains the most effective long-term control.

## Default credentials

Default credentials are the usernames and passwords that manufacturers assign to devices, applications, and services at the time of shipment. Attackers routinely exploit systems on which these defaults remain unchanged.

Vendors publish or hard-code well-known credential pairs for initial setup. When administrators fail to replace them, the same credentials grant immediate authenticated access to anyone who can reach the login interface. Internet-wide scans continuously identify devices still using factory defaults—routers, cameras, IoT sensors, databases, and management consoles—and compromise them within minutes of discovery.

Default accounts often possess elevated privileges, enabling rapid lateral movement, configuration changes, or malware installation. Because the credentials require no brute-force effort, the attack is both low-cost and highly reliable against unprepared targets.

Defenders eliminate this vector by changing all default credentials during initial provisioning, enforcing unique strong passwords or key-based authentication, and verifying through automated configuration checks that no default accounts remain active. Network controls that restrict access to management interfaces provide a compensating layer until remediation is complete. Inventory and scanning processes that specifically flag default-credential usage close the gap between policy and actual device state.

## Supply chain

The supply chain encompasses every external party that contributes hardware, software, services, or data to an organization’s operations. Attackers treat this extended ecosystem as a high-leverage vector: compromise one trusted link and the malicious content or access travels downstream under the cover of legitimacy.

Supply-chain attacks take several forms. Adversaries insert backdoors into software during development or build processes, replace legitimate updates with trojanized versions, ship hardware containing hidden implants, or exploit the remote-access tools that vendors and managed service providers use for support. Because the organization has already established trust with the supplier, the malicious payload often bypasses traditional security inspection and is installed with elevated privileges.

The impact multiplies across customers. A single compromised software vendor or hardware manufacturer can affect thousands of organizations simultaneously. Detection is difficult; the attack arrives inside expected channels and may remain dormant until activated. Attribution and remediation become complex when the root cause lies outside the victim’s direct control.

Organizations manage supply-chain risk by maintaining a complete inventory of suppliers and components, enforcing contractual security requirements, demanding software bills of materials and signed updates, isolating vendor access, and continuously monitoring for anomalous behavior that originates from trusted third-party connections. Independent verification of critical components and the ability to shift to alternative suppliers when risk becomes unacceptable further reduce dependence on any single external party. Treating the supply chain as an extension of the attack surface—rather than a trusted black box—remains essential to limiting cascading compromise.

### Managed service providers (MSPs)

Managed service providers supply outsourced IT administration, monitoring, and security services to multiple customer organizations. Their privileged, persistent access across many environments turns them into a high-value supply-chain target and a distinct threat vector.

When an attacker compromises an MSP, the same credentials, remote-management tools, and network connections that the provider uses for legitimate support become pathways into every customer the MSP serves. A single breach can therefore cascade across dozens or hundreds of organizations. Attackers specifically seek MSP environments because the return on investment is multiplied by the number of downstream victims.

Common entry methods include phishing against MSP staff, exploitation of remote-monitoring and management (RMM) platforms, theft of shared administrative credentials, and abuse of poorly segmented customer-support networks. Once inside, the attacker can push malware, alter configurations, or exfiltrate data while appearing as routine managed-service activity.

Customer organizations inherit this risk even when their own perimeter defenses remain intact. Contracts, shared-responsibility matrices, and continuous verification of the MSP’s security posture become essential controls. Techniques such as just-in-time access, strict network segmentation of vendor connections, independent logging of all MSP activity, and regular review of privileged accounts reduce the blast radius. Organizations also require evidence of the MSP’s own vulnerability management, multi-factor authentication enforcement, and incident-response capability before granting production access.

The MSP relationship replaces a purely technical perimeter with a trust relationship that must be continuously validated. Failure to treat the provider as an extension of the attack surface leaves a privileged, often under-monitored pathway open to determined adversaries.

### Vendors

Vendors introduce third-party risk whenever an organization relies on external products, software, or services that connect to its environment or process its data. The vendor’s security posture becomes an extension of the organization’s own attack surface.

A compromised vendor can deliver trojanized software updates, expose shared credentials, or provide an attacker with legitimate remote-access pathways. Supply-chain attacks frequently begin with a software or hardware vendor whose development or distribution systems have been breached; the malicious content then travels downstream inside trusted packages. Cloud and SaaS vendors that store or process customer data create additional exposure: a breach at the provider can release information the customer never directly controlled.

Even well-intentioned vendors expand risk through excessive privileges, weak identity practices, or inadequate segmentation between their support systems and customer tenants. Contractual access granted for maintenance or integration often persists longer than necessary and receives less monitoring than internal accounts.

Organizations manage vendor risk by inventorying all third-party relationships, classifying them by data sensitivity and connectivity, and imposing security requirements through contracts and continuous assessment. Techniques include least-privilege access for vendor accounts, network isolation of vendor connections, mandatory multi-factor authentication, regular review of vendor access logs, and requirements for timely vulnerability disclosure and patching. Software bills of materials and signed updates help verify the integrity of delivered code. When a vendor’s controls fall short, compensating controls or termination of the relationship become necessary to keep residual risk within acceptable limits.

### Suppliers

Suppliers form a critical link in the supply chain and therefore constitute a distinct threat vector. Any organization that provides hardware, software components, raw materials, or specialized services can become the entry point through which attackers reach their actual targets.

Compromise often occurs upstream. An attacker infiltrates a supplier’s development environment, manufacturing process, or distribution channel and inserts malicious code, counterfeit components, or backdoored firmware. The tainted product then travels through normal procurement and installation channels, inheriting the trust placed in the legitimate supplier. Because the malicious content arrives inside an expected delivery, traditional perimeter defenses rarely inspect it closely.

Suppliers with privileged network connections or ongoing remote-support access create additional pathways. Weak security practices at the supplier—unpatched systems, shared credentials, or inadequate segmentation—allow attackers to pivot from the supplier’s environment into the customer’s. The more exclusive or specialized the supplier, the harder rapid substitution becomes, increasing pressure to continue the relationship despite known weaknesses.

Organizations address supplier risk through structured due diligence before contracting, contractual security requirements, periodic reassessment, and technical controls that limit the blast radius of any single supplier. Techniques include requiring software bills of materials, verifying digital signatures on delivered code, isolating supplier access to the minimum necessary resources, and maintaining independent monitoring of all supplier activity. When a supplier cannot or will not meet security expectations, residual risk must be explicitly accepted, mitigated with compensating controls, or eliminated by changing suppliers.

## Human vectors/social engineering

Social engineering exploits human psychology rather than technical vulnerabilities. Attackers manipulate trust, urgency, authority, and familiarity so that targets voluntarily disclose information, grant access, or execute actions that compromise security.

The major techniques share a common pattern: the attacker assumes a credible identity or scenario, creates pressure to act quickly, and requests something the victim is normally authorized to provide. Phishing and its variants (vishing, smishing) use fraudulent messages across email, voice, and text channels. Business email compromise and pretexting refine the same approach with detailed research and role-playing. Impersonation, brand impersonation, and typosquatting borrow legitimate visual or domain cues to lower suspicion. Watering-hole attacks shift the deception to websites the victims already trust. Misinformation and disinformation extend the influence campaign beyond individual targets to shape broader perception and decision-making.

Because these attacks succeed through human interaction, purely technical controls are incomplete. Effective defense combines continuous awareness training, out-of-band verification procedures, multi-factor authentication, strict payment and access-approval workflows, and rapid reporting channels. Organizations that treat social engineering as a primary initial-access method—and design processes that assume messages and requests may be fabricated—significantly reduce the likelihood and impact of successful human-vector attacks.

### Phishing

Phishing is a social-engineering attack that uses fraudulent messages to trick recipients into revealing credentials, installing malware, or performing actions that benefit the attacker. The message impersonates a trusted entity and creates a sense of urgency or authority that overrides normal caution.

Attackers deliver phishing primarily through email, but the same technique appears in SMS (smishing), instant messaging, and voice calls (vishing). The message typically contains a malicious link that leads to a credential-harvesting site or an attachment that executes malware when opened. Spear-phishing targets specific individuals with personalized details, while business-email compromise often impersonates executives to authorize fraudulent transfers.

Success depends on human interaction rather than technical exploitation. Once the victim complies, the attacker gains account access, financial resources, or a foothold inside the network. Because phishing bypasses many perimeter controls by exploiting trust, it remains one of the most common initial-access methods.

Defenders combine technical filtering—secure email gateways, link rewriting, attachment sandboxing, and DMARC/DKIM/SPF authentication—with continuous user awareness training and easy reporting channels. Multi-factor authentication reduces the value of stolen credentials. Rapid detection of anomalous account behavior after a suspected phishing event limits the damage of successful compromises. No single control eliminates phishing; layered technical and human defenses together shrink the window of opportunity.

### Vishing

Vishing (voice phishing) is a social-engineering attack conducted over telephone or VoIP channels. The attacker impersonates a trusted party—IT support, bank representative, government official, or company executive—and manipulates the target into disclosing information or performing actions in real time.

The call creates urgency and authority that email or text messages often lack. Callers spoof caller-ID information to appear legitimate, then request credentials, one-time codes, remote-access installation, or financial transfers. Deepfake voice technology increases credibility by cloning a known individual’s speech patterns. Because the interaction is live, the attacker can adapt instantly to the victim’s responses and overcome hesitation.

Vishing succeeds when organizations lack verification procedures for sensitive requests received by phone. Once the victim complies, the attacker obtains account access, funds, or a foothold on systems without exploiting technical vulnerabilities.

Defenders counter vishing through user training that emphasizes out-of-band verification, policies that prohibit disclosure of credentials or approval of high-risk actions solely on the basis of a phone call, multi-factor authentication that limits the value of verbally obtained secrets, and call-filtering technologies where available. Clear reporting channels allow employees to escalate suspicious calls before damage occurs. Technical controls alone cannot stop vishing; procedural discipline and human awareness remain essential.

### Smishing

Smishing delivers phishing content through SMS text messages. Attackers craft short, urgent texts that impersonate banks, package-delivery services, internal IT teams, or government agencies and embed a malicious link or request for sensitive information.

Mobile users often read and react to texts quickly, especially when the message appears on a lock screen or carries a time-sensitive warning. The limited screen space and lack of rich security indicators make it harder to scrutinize the sender or URL. Spoofed sender numbers further reduce suspicion. Once a recipient taps the link or replies with credentials, the attacker captures logins, session tokens, or installs malware on the device.

SMS-based one-time passwords also become targets; attackers who already possess a username and password can prompt the victim via text to forward a code, completing an account takeover.

Controls that reduce smishing risk include user training focused specifically on text-based social engineering, replacement of SMS one-time passwords with stronger multi-factor methods, mobile-threat-defense tools that evaluate device traffic and installed apps, and organizational policies that discourage reliance on SMS for authentication or sensitive approvals. Monitoring account activity for signs of compromise after a suspicious text provides a final safety net when prevention fails.

### Misinformation/disinformation

Misinformation is false or inaccurate information spread without deliberate harmful intent. Disinformation is false information created and distributed with the explicit goal of deceiving or manipulating an audience. Both appear as threat vectors when attackers use them to shape perceptions, erode trust, or create conditions that enable further technical attacks.

Threat actors publish fabricated news, forged documents, deepfake audio or video, and coordinated social-media content to influence public opinion, damage reputations, or distract defenders. During an active intrusion, disinformation can mask the real source of an attack or convince employees to take unsafe actions. Nation-state groups and politically motivated actors frequently combine technical operations with influence campaigns so that the psychological effect amplifies the technical impact.

Because these campaigns target human judgment rather than system vulnerabilities, traditional security controls detect them poorly. The damage appears as loss of public trust, flawed business decisions, or internal confusion that slows incident response.

Organizations counter misinformation and disinformation through media-literacy training, verified internal communication channels, rapid public-response procedures, and monitoring of external narratives that mention the organization. Technical measures such as digital-signature verification of official content and deepfake-detection tools provide supporting evidence, yet the core defense remains the ability of people to question unexpected or emotionally charged information before acting on it.

### Impersonation

Impersonation occurs when an attacker assumes the identity of a trusted person or system to gain confidence, access, or information. The technique underpins many social-engineering and technical attacks.

Human impersonation includes pretexting phone calls, spoofed emails that appear to come from executives, and fake help-desk interactions. Technical impersonation covers rogue access points that mimic legitimate SSIDs, websites that clone login pages, and compromised accounts that let an attacker speak with the authority of a real employee. Deepfake audio and video raise the fidelity of impersonation by reproducing a known individual’s voice or appearance.

The attacker’s goal is to make the target suspend normal verification. Once trust is established, the victim may disclose credentials, approve payments, install software, or grant remote access. Because the request appears to originate from a familiar source, standard suspicion filters fail.

Effective countermeasures focus on verification rather than recognition. Organizations enforce out-of-band confirmation for sensitive requests, apply multi-factor authentication so that possession of a single identity factor is insufficient, and train staff to treat unexpected urgency as a warning signal. Technical controls such as DMARC, certificate validation, and mutual authentication make pure technical impersonation more difficult. When impersonation does succeed, rapid detection of anomalous account or transaction behavior limits the resulting damage.

### Business email compromise

Business email compromise (BEC) is a targeted social-engineering attack in which criminals impersonate trusted business identities to redirect money or sensitive data. The attacker’s goal is financial theft or fraudulent transfer of assets rather than malware deployment.

Attackers typically compromise or convincingly spoof an executive, finance employee, or known vendor account. They then issue payment instructions, request changes to banking details, or solicit confidential documents. Because the message appears to originate from a legitimate internal or partner mailbox, ordinary phishing filters often miss it. Variations include attorney impersonation, vendor-invoice fraud, and payroll-diversion schemes.

BEC relies on reconnaissance. Criminals research organizational structure, reporting lines, and ongoing projects so the request fits expected business processes. Once the fraudulent transfer is completed, recovery is difficult; funds move quickly through multiple accounts and jurisdictions.

Organizations reduce BEC exposure by enforcing multi-factor authentication on all email accounts, applying DMARC policies that make spoofing harder, and requiring secondary verification—phone confirmation or dual approval—for any payment or account-change request. Finance and executive teams receive specific training that treats unexpected wire-transfer instructions as high-risk until independently confirmed. Behavioral monitoring that flags unusual payment patterns or sudden changes in vendor banking information provides an additional detection layer after prevention controls are bypassed.

### Pretexting

Pretexting is a social-engineering technique in which the attacker invents a plausible scenario, or pretext, to persuade a target to release information or perform an action. The fabricated story gives the request an appearance of legitimacy and urgency.

The attacker assumes a role the victim is likely to trust—help-desk technician, auditor, vendor, or fellow employee—and supplies enough contextual detail to make the narrative believable. Once the target accepts the premise, the attacker asks for credentials, access codes, internal documents, or remote-session approval. Because the interaction feels like a normal business process, the victim often complies without additional verification.

Pretexting occurs over phone calls, email, instant messaging, or in-person encounters. It frequently serves as the opening move for larger attacks such as business-email compromise or account takeover. Success depends on research; the more accurately the attacker mirrors real organizational language and procedures, the harder the deception becomes to detect.

Organizations counter pretexting by establishing strict verification procedures for any request involving access or sensitive data, training staff to recognize unsolicited authority claims, and requiring out-of-band confirmation before releasing information or granting elevated privileges. Technical controls such as multi-factor authentication and just-in-time access further limit the damage if a pretext succeeds. Clear reporting channels allow employees to escalate suspicious interactions before they escalate into breaches.

### Watering hole

A watering-hole attack compromises a website that a specific group of users is known to visit and waits for those users to become infected. Instead of targeting individuals directly, the attacker poisons a location the victims already trust.

The attacker first profiles the target population—employees of a particular company, members of an industry, or users of a specialized community—and identifies websites they frequent. The chosen site is then breached and injected with exploit code or malicious redirects. When a member of the intended group visits the site, the exploit delivers malware tailored to their environment. Because the traffic originates from a legitimate, expected destination, traditional reputation-based filters rarely block it.

Watering-hole campaigns are often selective. The malicious content may activate only for visitors coming from certain IP ranges or using specific browser configurations, reducing collateral exposure and delaying detection. The technique is favored by sophisticated actors who need reliable access to a narrow set of high-value targets.

Defenders reduce risk by keeping browsers and plugins patched, restricting the use of unneeded browser extensions, employing network-based exploit detection, and monitoring for unusual outbound connections after employees visit external sites. Website owners can further protect their visitors through rigorous patching, content-security policies, and integrity monitoring of web resources. When an organization learns that a frequently used site has been compromised, rapid communication and temporary access restrictions limit the window of exposure.

### Brand impersonation

Brand impersonation occurs when an attacker copies the name, logo, visual design, or communication style of a trusted organization to make malicious content appear legitimate. The goal is to borrow the victim’s confidence in that brand and redirect it toward a fraudulent request.

Attackers create look-alike websites, spoofed emails, fake social-media accounts, and counterfeit mobile applications that closely mimic the real brand. Small differences—extra characters in a domain name, slightly altered color schemes, or mismatched URLs—are easy to overlook under time pressure. Once the target accepts the imitation as genuine, the attacker harvests credentials, payment details, or malware installation consent.

Brand impersonation frequently supports phishing, business-email compromise, and fraudulent e-commerce schemes. It also enables the distribution of trojanized software that appears to come from a known vendor. Because the visual cues match expectations, technical indicators alone often fail to raise suspicion.

Organizations protect their own brands through trademark monitoring, rapid takedown of fraudulent sites and accounts, certificate transparency logging, and public education about official communication channels. Internally, defenders train users to verify domains and contact paths independently, enforce multi-factor authentication so that stolen credentials have limited value, and deploy email and web filters that detect look-alike domains. Continuous monitoring for new domains or social-media profiles that closely resemble the legitimate brand shortens the window attackers can exploit.

### Typosquatting

Typosquatting registers domain names that closely resemble legitimate ones, relying on common typing errors to capture traffic. Attackers anticipate mistakes such as missing letters, transposed characters, wrong top-level domains, or hyphen variations and claim those addresses first.

When a user mistypes a URL or clicks a carefully crafted link, the browser resolves to the attacker-controlled site instead of the intended destination. The fraudulent page often mirrors the real brand’s appearance and may host credential-harvesting forms, malware downloads, or advertising that generates revenue for the attacker. Email addresses on typosquatted domains can also intercept messages intended for the legitimate organization.

The technique succeeds because the difference between the real and fake domains is small enough to escape casual notice, especially on mobile devices or under time pressure. Typosquatting supports phishing campaigns, brand impersonation, and drive-by download attacks.

Organizations defend against typosquatting by registering common misspellings of their own domains, monitoring for newly registered look-alike names, and enforcing DMARC policies that make email spoofing harder. Users reduce risk by bookmarking critical sites, carefully inspecting URLs before entering credentials, and treating unexpected login pages with suspicion. Browser-based warnings and reputation services that flag recently registered or low-reputation domains provide additional technical barriers.

## Conclusion

Attackers succeed by following the path of least resistance across technical and human surfaces. Effective defense requires continuous reduction of unnecessary exposure, rapid detection of anomalous activity, and processes that assume requests and content may be fabricated. Mastery of threat vectors and attack surfaces equips candidates to evaluate risk accurately and to design controls that close the most common entry points before they are exploited.
