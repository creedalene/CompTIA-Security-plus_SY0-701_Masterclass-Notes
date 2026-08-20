# C###mpTIA Security+ (SY0-701) Domain 2.2 Explain common threat vectors and attack surfaces.

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

## File-based

## Voice call

## Removable device

## Vulnerable software

### Client-based vs. agentless

## Unsupported systems and applications

## Unsecure networks

### Wireless

### Wired

### Bluetooth

## Open service ports

## Default credentials

## Supply chain

### Managed service providers (MSPs)

### Vendors

### Suppliers

## Human vectors/social engineering

### Phishing

### Vishing

### Smishing

### Misinformation/disinformation

### Impersonation

### Business email compromise

### Pretexting

### Watering hole

### Brand impersonation

### Typosquatting

## Conclusion
