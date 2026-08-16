# CompTIA Security+ (SY0-701) Domain 1.1 Compare and contrast various types of security controls.

Security controls form the practical foundation of every security program. CompTIA Security+ SY0-701 requires candidates to classify any given control along two independent axes at the same time: the method of implementation (category) and the functional purpose (type).

This dual classification appears throughout the exam. Questions present a specific control or scenario and ask for the correct category, the correct type, or both. Mastery of both axes allows rapid, accurate identification under time pressure and supports real-world control selection and gap analysis.

The notes that follow examine each category and each type in turn, show how the two classifications intersect, and illustrate the combinations with concrete examples drawn from the exam objectives.

## Security Control Categories

CompTIA Security+ SY0-701 classifies security controls along two independent axes. Categories describe how organizations implement a control. Types describe what the control achieves.

The four categories answer the question of implementation method:

- **Technical** controls enforce rules through hardware, software, or firmware.
- **Managerial** controls establish direction through policies, standards, risk assessments, and governance.
- **Operational** controls execute security tasks through people following procedures.
- **Physical** controls protect facilities and assets through tangible barriers, sensors, and human presence.

Every control belongs to one primary category based on its implementation method. The same control also receives one or more type labels (preventive, deterrent, detective, corrective, compensating, or directive) according to its functional effect. A firewall rule is technical and preventive. A written incident response policy is managerial and directive. An analyst reviewing logs is operational and detective. A locked door is physical and preventive.

Organizations combine controls from all four categories to build layered defense. Managerial controls set the requirements. Technical and physical controls enforce those requirements automatically or tangibly. Operational controls ensure people carry out the required processes every day.

### Technical Security Controls

Technical security controls (also called logical controls) implement protection through technology. Organizations deploy these controls via hardware, software, or firmware so the system itself enforces security rules automatically and consistently, without continuous human action for every decision.

A technical control operates inside the computing environment. When an administrator configures a rule, the technology applies that rule to every matching event. Firewalls examine packets against access control lists (ACLs). Encryption algorithms transform readable data into ciphertext. Authentication systems validate credentials before granting access. The system performs these actions every time, regardless of whether a person is watching.

**Core Characteristics**
- **Technology-enforced**: Hardware (security appliances, TPMs), software (antivirus engines, SIEM platforms), or firmware (BIOS/UEFI protections) carries out the control.
- **Automatic execution**: Once configured, the control runs without manual intervention for each instance.
- **Scalable consistency**: The same rule applies uniformly across thousands of endpoints or network flows.
- **Configurable and auditable**: Administrators set parameters, update signatures or policies, and review logs the control generates.

Technical controls differ from managerial controls (policies and risk frameworks written by leadership), operational controls (day-to-day procedures performed by people), and physical controls (locks, fences, cameras that protect facilities and hardware).

**Common Technical Controls and Their Functions**
Organizations combine technical controls with the six functional control types (preventive, deterrent, detective, corrective, compensating, directive). A single technical control often serves more than one function depending on configuration and context.

**Network and boundary protection**
- Firewalls apply rule sets that permit or deny traffic by IP address, port, protocol, or application. A correctly configured firewall acts as a preventive control by blocking unauthorized connections before they reach internal systems.
- Network access control (NAC) solutions evaluate device posture (patch level, antivirus status) before granting network access. NAC enforces preventive restrictions and can trigger corrective actions such as quarantine.
- Intrusion detection systems (IDS) monitor traffic or host activity and generate alerts when signatures or anomalies match known attack patterns. IDS functions primarily as a detective control. Intrusion prevention systems (IPS) extend this by actively dropping or blocking malicious packets, adding a preventive capability.
- Web filters and URL scanners examine outbound or inbound web requests, categorize content, and apply block or allow rules based on reputation and policy.

**Access and identity enforcement**
- Access control lists (ACLs) on routers, switches, file systems, and applications define explicit allow or deny statements for users, groups, or processes. ACLs implement least-privilege authorization and serve as preventive controls.
- Multi-factor authentication (MFA) requires two or more distinct authentication factors (something you know, something you have, something you are). MFA strengthens authentication and reduces the success rate of credential-based attacks.
- Biometric systems capture and compare physiological or behavioral traits (fingerprint, facial recognition, voice) against stored templates. These systems authenticate people at the technical level.

**Data protection**
- Encryption protects confidentiality. Full-disk encryption, file-level encryption, database encryption, and transport-layer encryption (TLS) render data unreadable without the correct key. Encryption functions as a preventive control against unauthorized disclosure and as a compensating control when physical media leaves controlled environments.
- Data loss prevention (DLP) systems inspect data in motion, at rest, or in use and block or alert on attempts to transfer sensitive information outside authorized channels. DLP combines preventive and detective functions.
- Hashing and digital signatures provide integrity verification and non-repudiation. Systems compute cryptographic hashes and compare them to detect unauthorized modification.

**Endpoint and host protection**
- Antivirus and anti-malware engines scan files and processes against signature databases and behavioral heuristics. They detect, quarantine, or remove malicious code, serving both detective and corrective roles.
- Endpoint detection and response (EDR) and extended detection and response (XDR) platforms continuously monitor endpoint activity, record detailed telemetry, detect advanced threats, and enable rapid isolation or remediation. These tools emphasize detection and response.
- Application allow lists (whitelists) permit only approved executables to run. Allow lists act as strong preventive controls by blocking unknown or unauthorized code.
- Host-based firewalls and host intrusion prevention systems apply the same traffic-filtering and behavioral controls directly on the endpoint.

**Monitoring and response platforms**
- Security information and event management (SIEM) systems aggregate logs from multiple sources, correlate events, and generate alerts. SIEM primarily supports detective and corrective functions by enabling rapid identification and investigation of incidents.
- File integrity monitoring tools calculate baselines of critical system files and alert on unauthorized changes, providing detective capability.

**Intersection with Functional Control Types**
A technical control receives its category label from the technology that implements it. The same control receives one or more type labels according to its primary effect:

- Preventive technical controls stop unauthorized activity before it succeeds (firewall rules, MFA, encryption, application allow lists).
- Detective technical controls identify activity that has occurred or is in progress (IDS alerts, SIEM correlation, file integrity monitoring).
- Corrective technical controls restore systems or data after an incident (automated quarantine by EDR, restoration from encrypted backups, signature-based malware removal).
- Deterrent technical controls discourage attempts through visible technical mechanisms (login warning banners enforced by the operating system, account lockout policies).
- Compensating technical controls provide equivalent protection when a primary control is unavailable or impractical (enhanced monitoring and logging when a critical system cannot be patched immediately).
- Directive technical controls embed rules into systems that guide or enforce required behavior (group policy objects that mandate password complexity or screen-lock timeouts).

**Implementation Considerations**
Administrators configure technical controls according to organizational policy. Misconfiguration turns a strong control into a weak one or creates a new vulnerability. Regular updates to signatures, firmware, and rule sets maintain effectiveness against evolving threats. Logging and monitoring generated by technical controls feed operational processes and support managerial oversight through metrics and reports.

Technical controls scale efficiently across large environments yet remain limited by the quality of their configuration and the completeness of their coverage. They enforce only the rules they have been given; they do not invent new policy. Organizations therefore align technical controls with managerial directives and operational procedures to achieve defense-in-depth.

### Managerial Security Controls

Managerial security controls (also called administrative controls) establish the rules, direction, and oversight for an organization’s security program. Leadership creates these controls through policies, standards, procedures, guidelines, risk assessments, and governance structures. They define what the organization must protect, how risk receives treatment, and who holds accountability.

A managerial control answers the question of intent and requirement. A password policy states that users must create complex passwords of a minimum length. The policy itself does not enforce the rule; a technical control such as Active Directory password settings performs the enforcement. Managerial controls therefore guide and constrain the design and use of technical, operational, and physical controls.

**Core Characteristics**
- **Management-driven**: Executives, security leadership, or governance bodies approve and publish the control.
- **Document-based**: The control exists as written policy, standard, risk register entry, or formal assessment.
- **Oversight-focused**: These controls set risk tolerance, assign ownership, allocate resources, and measure compliance.
- **Indirect enforcement**: They require technical or operational mechanisms to become effective in practice.

Managerial controls differ from technical controls (hardware or software that automatically enforce rules), operational controls (people performing day-to-day security tasks), and physical controls (tangible barriers that protect facilities and assets).

**Common Managerial Controls**
Organizations apply managerial controls across the six functional types (preventive, deterrent, detective, corrective, compensating, directive). The same document or process can serve multiple functions depending on its content and use.

**Policy and governance documents**
- Information security policies declare the organization’s overall security objectives and high-level requirements.
- Acceptable use policies (AUPs) define permitted and prohibited uses of systems, data, and network resources.
- Incident response policies outline roles, authority, and required actions when a security event occurs.
- Business continuity and disaster recovery policies set expectations for continued operations and recovery after disruption.
- Change management policies require formal approval, testing, and documentation before modifications to production systems.
- Data classification policies assign sensitivity labels (public, internal, confidential, restricted) and dictate handling rules for each class.

**Risk management activities**
- Risk assessments identify threats, vulnerabilities, likelihood, and impact. Organizations perform these assessments on an ad-hoc, recurring, one-time, or continuous basis.
- Risk registers record identified risks, assign owners, track key risk indicators, and document residual risk levels.
- Risk analysis applies qualitative ratings (high/medium/low) or quantitative calculations (single loss expectancy, annualized rate of occurrence, annualized loss expectancy) to prioritize treatment.
- Risk management strategies document decisions to mitigate, transfer, accept, or avoid specific risks. Acceptance may include formal exemptions or exceptions.

**Standards, guidelines, and frameworks**
- Password standards mandate length, complexity, history, and lockout thresholds.
- Access control standards define least-privilege principles and authorization models.
- Encryption standards specify algorithms, key lengths, and approved cryptographic solutions.
- Guidelines provide recommended but non-mandatory practices that support policy goals.
- Governance frameworks (for example, alignment with NIST or ISO structures) establish boards, committees, roles, and reporting lines.

**Personnel and third-party oversight**
- Background check requirements and hiring practices set screening criteria for employees and contractors.
- Onboarding and offboarding policies define access provisioning and de-provisioning steps at the start and end of employment.
- Vendor and third-party risk management policies require due diligence, contractual security clauses, and ongoing monitoring of external providers.
- Security awareness program requirements mandate training frequency, content scope, and completion tracking (the program design is managerial; delivery of the training is operational).

**Intersection with Functional Control Types**
A managerial control receives its category label because management creates and owns it. The same control receives type labels according to its primary effect:

- Preventive managerial controls reduce the chance of incidents by establishing clear rules in advance (data classification policies, background check requirements, change approval processes).
- Deterrent managerial controls discourage violations through formal statements of consequence (acceptable use policies that list disciplinary actions, security awareness program mandates).
- Detective managerial controls require processes that discover problems (policies that mandate regular risk assessments or vulnerability assessments, audit requirements).
- Corrective managerial controls direct recovery actions after an event (incident response policies that define containment and eradication steps, disaster recovery policies).
- Compensating managerial controls provide alternative requirements when primary controls cannot be applied (formal risk acceptance with documented compensating measures, temporary exceptions with enhanced monitoring requirements).
- Directive managerial controls explicitly instruct personnel on required behavior (standards that mandate specific configurations, procedures that prescribe step-by-step actions).

**Implementation Considerations**
Leadership publishes managerial controls and revises them through formal review cycles. Effective controls remain current with regulatory, legal, industry, and organizational changes. Monitoring of compliance against these controls produces metrics that feed governance reporting. Gaps between policy requirements and actual implementation surface during audits or assessments and drive updates to both managerial and supporting technical or operational controls.

Managerial controls scale across the enterprise through documentation and communication. Their effectiveness depends on clear ownership, measurable requirements, and consistent alignment with the technical and operational controls that put the rules into practice.

### Operational Security Controls

Operational security controls rely on people to perform day-to-day security tasks and procedures. Staff members execute these controls to enforce managerial policies, support technical systems, and protect physical assets through consistent human action.

An operational control requires active human involvement. A security analyst reviews SIEM alerts each morning, follows an incident response playbook during an event, or conducts user training sessions. The control succeeds only when people carry out the required steps according to documented procedures.

**Core Characteristics**
- **People-executed**: Human operators, administrators, or security staff perform the control through scheduled or event-driven actions.
- **Process-driven**: The control follows established procedures, runbooks, or standard operating procedures derived from managerial policies.
- **Day-to-day focus**: These controls maintain ongoing security posture through routine activities rather than one-time decisions or automated enforcement.
- **Bridge function**: Operational controls translate managerial intent into practical action and feed results back into governance and technical systems.

Operational controls differ from managerial controls (policies and risk frameworks created by leadership), technical controls (hardware or software that enforce rules automatically), and physical controls (tangible barriers such as locks or fences).

**Common Operational Controls**
Organizations apply operational controls across the six functional types (preventive, deterrent, detective, corrective, compensating, directive). A single activity can serve multiple functions based on context and timing.

**Incident and response activities**
- Security analysts follow incident response playbooks to contain, eradicate, and recover from security events. These actions serve corrective and detective functions.
- Teams conduct tabletop exercises and full-scale drills that test response procedures and identify gaps.
- Staff perform post-incident reviews that document lessons learned and update procedures.

**Configuration, change, and maintenance tasks**
- Administrators implement approved changes according to change management procedures, including testing, backout plans, and documentation updates.
- IT staff apply patches, update baselines, and enforce configuration standards on systems.
- Operators manage media protection through secure handling, storage, transport, and destruction of physical and digital media.

**Monitoring and review processes**
- Analysts review logs, SIEM alerts, and vulnerability scan results on a scheduled basis.
- Personnel perform file integrity checks, user access reviews, and privilege audits.
- Teams conduct continuous or recurring vulnerability assessments and track remediation progress.

**Personnel and awareness activities**
- Trainers deliver security awareness sessions that teach employees to recognize phishing, social engineering, and safe computing practices. The delivery of training is operational; the requirement for training is managerial.
- Human resources or security staff execute onboarding and offboarding procedures that provision or revoke access, collect equipment, and brief personnel.
- Organizations practice job rotation and enforce separation of duties through scheduled role changes and dual-control processes.

**Physical and environmental operations**
- Security personnel patrol facilities, monitor surveillance feeds, and respond to physical alarms.
- Staff manage environmental controls, escort visitors, and enforce badge or access procedures at entry points.
- Teams perform inventory, asset tracking, and secure disposal of hardware.

**Intersection with Functional Control Types**
An operational control receives its category label because people perform it. The same control receives type labels according to its primary effect:

- Preventive operational controls reduce the likelihood of incidents through proactive human actions (conducting awareness training, performing regular configuration reviews, enforcing separation of duties).
- Deterrent operational controls discourage violations by making detection or consequences visible (visible guard patrols, scheduled access reviews that personnel know occur).
- Detective operational controls identify events or weaknesses through human review (daily log analysis, vulnerability scan interpretation, physical security rounds).
- Corrective operational controls restore systems or processes after an event (following incident response steps, reimaging systems, restoring from backups under procedure).
- Compensating operational controls provide alternative protection when primary controls are unavailable (increased manual monitoring when a technical control is offline, temporary dual-control procedures during system upgrades).
- Directive operational controls guide required behavior through step-by-step instructions that people must follow (runbooks, standard operating procedures, playbooks).

**Implementation Considerations**
Organizations document operational procedures so staff can execute them consistently under normal and emergency conditions. Effective operational controls require trained personnel, clear ownership, measurable performance metrics, and regular testing. Results from operational activities (incident reports, training completion rates, configuration compliance scores) feed managerial oversight and drive updates to policies and technical configurations.

Operational controls scale through well-written procedures and skilled staff. Their effectiveness depends on human reliability, clear communication of expectations, and continuous improvement based on observed outcomes. When people follow documented processes aligned with managerial requirements and supported by technical systems, operational controls close the gap between policy and practice.

### Physical Security Controls

Physical security controls protect facilities, hardware, and physical assets through tangible measures. Organizations deploy these controls to restrict, deter, detect, or respond to unauthorized physical access and environmental threats.

A physical control operates in the real world. Bollards stop vehicles from ramming into a building entrance. Fences define and harden the perimeter. Locks and access badges control who enters secure rooms. Cameras and sensors record or alert on activity. These controls work independently of software or policy documents yet support both technical and operational security.

**Core Characteristics**
- **Tangible implementation**: Physical devices, structures, or personnel create barriers or monitoring capabilities that people can see and touch.
- **Facility and asset focus**: Controls protect buildings, data centers, wiring closets, workstations, servers, and storage media from unauthorized physical interaction or environmental harm.
- **Layered defense**: Organizations place controls at the perimeter, building entry points, internal zones, and individual asset level.
- **Complementary role**: Physical controls reduce the effectiveness of remote or logical attacks by denying attackers direct access to hardware.

Physical controls differ from technical controls (hardware or software that enforce rules automatically), managerial controls (policies and risk frameworks created by leadership), and operational controls (people performing day-to-day security tasks).

**Common Physical Security Controls**
CompTIA SY0-701 identifies specific physical controls under fundamental security concepts. Organizations apply these controls across the six functional types (preventive, deterrent, detective, corrective, compensating, directive).

**Perimeter and entry protection**
- Bollards (short, sturdy posts) and other vehicle barriers prevent cars or trucks from reaching building entrances or critical infrastructure. They serve primarily as preventive and deterrent controls.
- Fencing creates a physical boundary around a property. Height, material, and topping (barbed or razor wire) increase resistance to climbing. Fencing functions as a preventive and deterrent control.
- Access control vestibules (also called mantraps) consist of two interlocking doors that form a small enclosed space. Only one door opens at a time, forcing sequential authentication and preventing tailgating. These act as strong preventive controls.
- Access badges and badge readers grant or deny entry based on credential validation. When combined with turnstiles or locked doors, they enforce preventive access control.
- Lighting illuminates exterior areas, entrances, and critical zones. Proper lighting deters unauthorized activity and improves the effectiveness of video surveillance.

**Surveillance and detection**
- Video surveillance systems (cameras) record activity in real time or store footage for later review. Visible cameras deter intruders; continuous monitoring or recording supports detection.
- Security guards provide human presence, check credentials, patrol areas, and respond to alarms. Guards combine deterrent, detective, and corrective functions.
- Sensors detect physical intrusion or environmental changes:
  - Infrared sensors detect body heat or motion through temperature differences.
  - Pressure sensors register weight or force on floors, mats, or surfaces.
  - Microwave sensors emit radio waves and detect disturbances in the reflected signal.
  - Ultrasonic sensors use high-frequency sound waves to identify movement.
  These sensors primarily serve detective functions and often trigger alarms or camera recording.

**Asset and environmental protection**
- Locks (mechanical or electronic) secure doors, cabinets, racks, and device cases. They function as preventive controls.
- Environmental controls (HVAC monitoring, fire suppression, water detection, temperature and humidity sensors) protect equipment from damage caused by heat, cold, moisture, or fire. These support availability and act as preventive or detective controls depending on configuration.

**Intersection with Functional Control Types**
A physical control receives its category label because it exists as a tangible object or human presence in physical space. The same control receives type labels according to its primary effect:

- Preventive physical controls stop unauthorized access before it succeeds (bollards, fencing, access control vestibules, locks, badge readers).
- Deterrent physical controls discourage attempts through visible presence or consequence (visible cameras, security guards, lighting, warning signs at perimeter fences).
- Detective physical controls identify intrusion or environmental events that have occurred or are in progress (video surveillance, motion sensors, pressure sensors, alarm systems).
- Corrective physical controls restore security after an event (guards responding to an alarm, resetting locks, replacing damaged barriers).
- Compensating physical controls provide alternative protection when preferred controls are unavailable (temporary barriers during construction, increased guard presence when electronic access systems fail).
- Directive physical controls guide required behavior through physical design or posted instructions (clearly marked secure zones, mandatory badge display requirements enforced at entry points).

**Implementation Considerations**
Organizations select and place physical controls according to risk assessments that evaluate threats such as unauthorized entry, theft, vandalism, vehicle attacks, and environmental hazards. Effective placement creates concentric layers: perimeter barriers first, then building entry controls, then internal zone restrictions, then asset-level protections. Integration with technical systems (badge readers linked to identity systems, cameras feeding SIEM or monitoring platforms) and operational procedures (guard response protocols, visitor escort policies) multiplies effectiveness.

Physical controls require regular inspection, maintenance, and testing. Damaged fences, non-functional cameras, or expired access credentials reduce protection. Organizations document physical security layouts, maintain inventories of controlled access points, and review footage or sensor logs as part of ongoing security operations. When properly designed and maintained, physical controls deny attackers the physical access needed to bypass or compromise technical and operational defenses.

## Security Control Types

CompTIA Security+ SY0-701 classifies security controls by function as well as by implementation category. Control types describe the primary effect a control produces in the security lifecycle.

The six types answer the question of purpose:

- **Preventive** controls stop unauthorized activity before it succeeds.
- **Deterrent** controls discourage attempts by increasing perceived risk of detection or consequences.
- **Detective** controls identify activity that is occurring or has already occurred.
- **Corrective** controls restore systems or processes to a secure state after an incident.
- **Compensating** controls provide alternative protection when the preferred control cannot be implemented.
- **Directive** controls instruct people on required or prohibited behavior.

Every control receives at least one type label based on its dominant effect. The same control also belongs to a category (technical, managerial, operational, or physical) according to how organizations implement it. A single control can serve multiple types depending on configuration and context—an intrusion prevention system both detects and blocks, while a visible camera both deters and records.

Organizations combine all six types across the four categories to create defense in depth. Preventive and deterrent controls reduce the number of incidents. Detective controls provide visibility. Corrective controls limit damage and restore operations. Compensating controls address gaps. Directive controls ensure people understand what the organization requires.

### Preventive Security Controls

Preventive security controls stop unauthorized or unwanted activity before it succeeds. Organizations deploy these controls to reduce the likelihood of security incidents by blocking access, enforcing restrictions, or eliminating opportunities for attack.

A preventive control operates ahead of an event. A firewall drops packets that match deny rules before they reach internal systems. Multi-factor authentication rejects login attempts that lack a second factor. A locked door keeps unauthorized people outside a server room. These controls aim to keep threats from becoming incidents.

**Core Characteristics**
- **Pre-event action**: The control intervenes before damage, unauthorized access, or policy violation occurs.
- **Risk reduction focus**: Preventive controls lower the probability of successful attacks or errors rather than detecting or repairing them after the fact.
- **Cross-category application**: Organizations implement preventive controls through technology, policy, human procedures, and physical barriers.
- **First line of defense**: These controls form the initial barrier in a defense-in-depth strategy.

Preventive controls differ from detective controls (which identify events that have occurred or are in progress), corrective controls (which restore systems after an incident), deterrent controls (which discourage attempts through psychological effect), compensating controls (which provide alternatives when preferred controls are unavailable), and directive controls (which instruct people on required behavior).

**Common Preventive Controls by Category**

**Technical preventive controls**
- Firewalls apply rule sets that permit or deny traffic by address, port, protocol, or application and block unauthorized connections.
- Access control lists (ACLs) on routers, switches, file systems, and applications enforce explicit allow or deny decisions.
- Multi-factor authentication (MFA) requires additional verification beyond a password and stops credential-only attacks.
- Encryption renders data unreadable without the correct key and prevents unauthorized disclosure of stored or transmitted information.
- Application allow lists permit only approved executables to run and block unknown or malicious code.
- Network segmentation and isolation limit the scope of potential compromise by restricting traffic between zones.
- Patch management and secure configuration baselines close known vulnerabilities before attackers can exploit them.
- Data loss prevention (DLP) systems inspect and block unauthorized transfers of sensitive data.

**Managerial preventive controls**
- Security policies and standards mandate required protections such as least privilege, data classification handling rules, and password complexity.
- Background check requirements and hiring standards reduce the risk of insider threats by screening personnel before access is granted.
- Change management policies require formal review and approval before modifications reach production systems.
- Risk assessments identify high-risk areas so organizations can prioritize preventive measures.

**Operational preventive controls**
- Staff deliver security awareness training that teaches employees to recognize and avoid phishing, social engineering, and unsafe practices.
- Personnel enforce separation of duties and job rotation so no single individual controls an entire critical process.
- Administrators apply approved configurations and perform regular access reviews that remove unnecessary privileges.
- Teams execute media protection procedures that securely handle, store, and destroy sensitive physical and digital media.

**Physical preventive controls**
- Locks, badge readers, and access control vestibules (mantraps) restrict entry to authorized individuals only.
- Fencing, bollards, and vehicle barriers prevent unauthorized physical or vehicle approach to facilities and critical infrastructure.
- Secure racks, cabinets, and device locks protect hardware from tampering or theft.

**Intersection with Control Categories**
A preventive control receives its type label because it stops activity before success. The same control also carries a category label based on how organizations implement it:

- A firewall rule is both technical and preventive.
- A background check policy is both managerial and preventive.
- Delivery of phishing-resistance training is both operational and preventive.
- A locked server room door is both physical and preventive.

Many controls serve more than one type depending on configuration and context. An IDS that only alerts is detective; an IPS that actively blocks matching traffic is preventive. Encryption protects confidentiality preventively and can also support corrective recovery when combined with secure key management.

**Implementation Considerations**
Organizations select preventive controls based on risk assessments that identify the most likely and highest-impact threats. Effective preventive controls align with managerial policies, receive proper configuration and maintenance, and integrate with detective and corrective measures for defense in depth. Overly restrictive preventive controls can impair legitimate business operations; organizations therefore balance security strength against operational usability.

Regular testing, updates, and reviews keep preventive controls effective against evolving threats. Signature databases, firmware, access lists, and physical barriers all require ongoing attention. When preventive controls function correctly, they reduce the volume of incidents that reach detective and corrective stages and lower overall risk exposure.

### Deterrent Security Controls

Deterrent security controls discourage unauthorized or malicious activity by creating a psychological barrier. Organizations deploy these controls so potential attackers or policy violators perceive higher risk of detection or consequences and choose not to proceed.

A deterrent control works through visibility and implied threat. A login banner warns users that the system monitors activity and that unauthorized use brings legal penalties. Visible cameras and security guards signal that someone observes the area. Bright lighting removes shadows where an intruder might hide. These controls do not physically or logically block every attempt; they reduce the willingness of people to try.

**Core Characteristics**
- **Psychological effect**: The control influences human decision-making by increasing perceived risk of detection, identification, or punishment.
- **Visibility emphasis**: Effective deterrents remain noticeable so potential violators recognize their presence.
- **Complementary role**: Deterrent controls support preventive, detective, and corrective measures by lowering the number of attempts that reach those layers.
- **Cross-category application**: Organizations implement deterrents through technology, policy statements, human presence, and physical design.

Deterrent controls differ from preventive controls (which actively block or stop activity), detective controls (which identify events that occur), corrective controls (which restore systems after an incident), compensating controls (which provide alternatives when preferred controls are unavailable), and directive controls (which instruct people on required behavior).

**Common Deterrent Controls by Category**

**Technical deterrent controls**
- Login warning banners and splash screens display legal notices that the system is for authorized use only, that activity is monitored, and that violations may result in prosecution or disciplinary action.
- Account lockout policies and visible failed-login counters signal that repeated unauthorized attempts trigger protective responses.
- System messages or interface elements that indicate monitoring or logging is active discourage casual misuse.

**Managerial deterrent controls**
- Acceptable use policies (AUPs) and security policies explicitly state prohibited actions and the consequences of violations, including termination or legal action.
- Codes of conduct and disciplinary frameworks communicate that the organization enforces rules consistently.
- Published risk acceptance or exception processes make clear that unauthorized deviations carry accountability.

**Operational deterrent controls**
- Visible security awareness campaigns and training reinforce that the organization detects and responds to policy violations.
- Regular, observable access reviews and privilege audits remind personnel that the organization tracks and questions unnecessary permissions.
- Scheduled and announced security drills or inspections increase awareness that oversight occurs.

**Physical deterrent controls**
- Visible video surveillance cameras and monitoring signs indicate continuous observation of entrances, corridors, and critical areas.
- Security guards provide a human presence that potential intruders must confront or evade.
- Adequate exterior and interior lighting eliminates dark areas that could conceal unauthorized activity.
- Perimeter fencing, barriers, and posted warning signs communicate restricted access and the likelihood of detection.
- Clearly marked secure zones and badge requirements make unauthorized entry conspicuous.

**Intersection with Control Categories**
A deterrent control receives its type label because it discourages attempts through psychological impact. The same control also carries a category label based on implementation method:

- A login banner is both technical and deterrent.
- An acceptable use policy that lists penalties is both managerial and deterrent.
- Visible guard patrols are both operational (or physical) and deterrent.
- Well-lit camera coverage is both physical and deterrent.

Many controls serve multiple types. A security camera that is highly visible acts as a deterrent; the same camera that records footage and triggers alerts also functions as a detective control. A locked door is primarily preventive, yet its visible presence can also deter casual attempts.

**Implementation Considerations**
Organizations select deterrent controls that remain credible and consistently enforced. Empty threats or non-functional cameras reduce effectiveness and can undermine overall security culture. Deterrents work best when potential violators believe detection is likely and consequences are real.

Placement and visibility matter. Cameras pointed at entrances, banners that appear before authentication, and guards stationed at key points maximize psychological impact. Organizations combine deterrents with actual preventive and detective capabilities so that attempts that ignore the deterrent still encounter technical or physical barriers and generate alerts.

Regular review ensures deterrent controls stay current with legal requirements, organizational policy, and threat landscape. When people perceive that monitoring is active and enforcement is consistent, deterrent controls lower the volume of unauthorized attempts that reach deeper layers of defense.

### Detective Security Controls

Detective security controls identify unauthorized activity, policy violations, or security events that are in progress or have already occurred. Organizations deploy these controls to generate alerts, create records, and provide visibility so response teams can investigate and act.

A detective control reveals what preventive controls did not stop. An intrusion detection system (IDS) examines network traffic or host activity and raises an alert when signatures or anomalies match known attack patterns. Security information and event management (SIEM) platforms correlate logs from multiple sources and surface suspicious sequences. File integrity monitoring tools compare current file states against a trusted baseline and report unauthorized changes. These controls do not block the activity themselves; they make the activity visible.

**Core Characteristics**
- **During or after event focus**: The control operates while an incident unfolds or after it has taken place.
- **Visibility and alerting**: Detective controls produce logs, alerts, reports, or evidence that support investigation and response.
- **Cross-category application**: Organizations implement detection through technology, human review processes, policy requirements, and physical sensors.
- **Enabler of response**: Effective detection shortens the time between compromise and containment.

Detective controls differ from preventive controls (which stop activity before success), corrective controls (which restore systems after an incident), deterrent controls (which discourage attempts through psychological effect), compensating controls (which provide alternatives when preferred controls are unavailable), and directive controls (which instruct people on required behavior).

**Common Detective Controls by Category**

**Technical detective controls**
- Intrusion detection systems (IDS) monitor network traffic or host processes and generate alerts on signature matches or behavioral anomalies. Network-based IDS inspects packets; host-based IDS examines system activity.
- Security information and event management (SIEM) solutions aggregate logs, correlate events across systems, and produce prioritized alerts.
- Endpoint detection and response (EDR) and extended detection and response (XDR) platforms continuously collect endpoint telemetry, detect advanced threats, and surface actionable findings.
- Antivirus and anti-malware engines identify known malicious code through signatures or heuristics and report detections.
- File integrity monitoring tools establish baselines of critical system files and alert on unauthorized modifications.
- Log management systems collect, store, and enable searching of security-relevant events from operating systems, applications, and network devices.
- Honeypots, honeynets, and honeytokens attract and record attacker interaction, providing early warning of reconnaissance or intrusion attempts.

**Managerial detective controls**
- Audit and monitoring policies require regular review of access logs, privilege assignments, and security events.
- Risk assessment and vulnerability management policies mandate scheduled evaluations that surface weaknesses.
- Compliance monitoring requirements direct ongoing verification that controls remain effective.

**Operational detective controls**
- Security analysts review SIEM alerts, firewall logs, and authentication records on a scheduled or continuous basis.
- Personnel perform user access reviews and privilege audits that identify excessive or unauthorized permissions.
- Teams conduct vulnerability scanning and interpret results to detect missing patches or misconfigurations.
- Staff monitor physical security feeds or respond to sensor-triggered alerts as part of routine duties.

**Physical detective controls**
- Video surveillance systems record activity and support real-time or post-event review of entrances, critical areas, and assets.
- Motion, infrared, pressure, microwave, and ultrasonic sensors detect physical intrusion or unexpected presence and trigger alarms.
- Alarm systems and notification mechanisms alert security personnel when sensors or doors register unauthorized activity.
- Security guards observe areas, check credentials, and report anomalies during patrols.

**Intersection with Control Categories**
A detective control receives its type label because it identifies activity that is occurring or has occurred. The same control also carries a category label based on implementation method:

- An IDS alert is both technical and detective.
- A policy requiring daily log review is both managerial and detective.
- An analyst examining SIEM dashboards is both operational and detective.
- A motion sensor that triggers an alarm is both physical and detective.

Many controls serve multiple types. An intrusion prevention system (IPS) that both detects and actively blocks traffic combines detective and preventive functions. A security camera that is highly visible acts as a deterrent while its continuous recording supports detection. File integrity monitoring detects changes and can also support corrective investigation.

**Implementation Considerations**
Organizations tune detective controls to balance sensitivity against false positives. Excessively noisy alerts overwhelm analysts and reduce response effectiveness; overly narrow detection misses real threats. Effective detection requires reliable log sources, synchronized time across systems, adequate retention, and skilled personnel who can interpret results.

Integration improves outcomes. Technical detection feeds operational review processes; operational findings inform managerial risk decisions and policy updates. Organizations test detection capability through exercises, red-team activity, and regular validation that alerts fire as expected.

When detective controls function well, they shrink the window of exposure, supply evidence for investigation and legal processes, and enable faster transition to corrective actions. Detection alone does not stop attacks; it provides the visibility required for timely and effective response.

### Corrective Security Controls

Corrective security controls restore systems, data, or processes to a secure and operational state after a security incident or unauthorized activity has occurred. Organizations deploy these controls to eliminate the effects of an event, recover functionality, and reduce the chance of immediate recurrence.

A corrective control acts after the fact. Antivirus software quarantines or removes malware that has already executed. An endpoint detection and response (EDR) platform isolates a compromised host from the network. Administrators restore critical files from known-good backups. Incident responders follow playbooks to eradicate attacker presence and return systems to baseline. These controls repair damage and close the incident.

**Core Characteristics**
- **Post-event action**: The control operates after an incident has been detected or has produced observable effects.
- **Restoration focus**: Corrective controls return assets to a known-good or policy-compliant state and may include steps that limit further impact.
- **Cross-category application**: Organizations implement corrective measures through technology, documented procedures, human response actions, and physical repairs.
- **Link to prevention of recurrence**: Many corrective actions also strengthen defenses so the same incident is less likely to succeed again.

Corrective controls differ from preventive controls (which stop activity before success), detective controls (which identify events that occur), deterrent controls (which discourage attempts through psychological effect), compensating controls (which provide alternatives when preferred controls are unavailable), and directive controls (which instruct people on required behavior).

**Common Corrective Controls by Category**

**Technical corrective controls**
- Antivirus and anti-malware engines quarantine, clean, or delete malicious code that has been detected on a system.
- Endpoint detection and response (EDR) and extended detection and response (XDR) platforms automatically or on-demand isolate compromised endpoints, kill malicious processes, and support remediation.
- Backup and recovery systems restore data, configurations, or entire systems from known-good copies after ransomware, corruption, or unauthorized modification.
- Automated or scripted remediation tools reapply secure configurations, revoke compromised credentials, or roll back unauthorized changes.
- Patch deployment after exploitation closes the vulnerability that an attacker used.

**Managerial corrective controls**
- Incident response policies define required recovery phases, roles, communication paths, and criteria for returning systems to production.
- Post-incident review and lessons-learned requirements mandate documentation of root cause and corrective actions that update policies or standards.
- Business continuity and disaster recovery policies establish recovery time objectives and recovery point objectives that guide restoration priorities.

**Operational corrective controls**
- Incident response teams execute playbooks to contain the incident, eradicate attacker artifacts, recover systems, and verify normal operation.
- Administrators restore data from backups, rebuild systems from secure images, and validate that restored assets meet security baselines.
- Personnel apply emergency configuration changes or temporary workarounds under change control procedures while permanent fixes are prepared.
- Staff conduct post-incident access reviews and credential resets to remove any unauthorized privileges the attacker obtained.

**Physical corrective controls**
- Security personnel respond to alarms, escort unauthorized individuals out of restricted areas, and secure the location.
- Teams repair or replace damaged fences, locks, doors, cameras, or barriers after physical intrusion or vandalism.
- Staff reset physical access systems, re-key locks, or re-issue credentials after compromise of physical access tokens.

**Intersection with Control Categories**
A corrective control receives its type label because it restores a secure state after an event. The same control also carries a category label based on implementation method:

- Automated malware removal is both technical and corrective.
- An incident response policy that mandates recovery steps is both managerial and corrective.
- Analysts following a playbook to reimage a host are both operational and corrective.
- Guards securing a breached door and repairing the lock are both physical and corrective.

Many controls serve multiple types. Restoring from an encrypted backup is corrective for availability and integrity; the encryption itself was preventive for confidentiality. Isolating a host with EDR is corrective in the moment and can also serve a preventive function by limiting lateral movement. Lessons learned that update firewall rules turn a corrective process into improved prevention.

**Implementation Considerations**
Organizations prepare corrective controls in advance through tested backups, documented playbooks, pre-staged recovery media, and trained response personnel. Effective correction depends on reliable detection; without timely awareness of the incident, corrective action begins too late.

Recovery prioritizes critical assets according to business impact. Teams verify that restored systems are free of attacker persistence before returning them to production. Post-incident activities capture root cause, update configurations or policies, and measure recovery time against objectives.

Corrective controls close the incident lifecycle. When organizations combine rapid detection with rehearsed corrective procedures, they limit damage, restore operations faster, and feed improvements back into preventive and detective layers.

### Compensating Security Controls

Compensating security controls provide alternative protection when an organization cannot implement the preferred or primary control. Organizations deploy these controls to achieve comparable risk reduction through different means when technical limitations, cost, legacy systems, or business constraints prevent the ideal solution.

A compensating control fills a gap. When a critical server cannot receive a security patch because a vendor application would break, the organization adds enhanced monitoring, stricter network segmentation, and more frequent access reviews around that server. When a legacy system lacks support for multi-factor authentication, the organization requires additional approval workflows and session monitoring. These alternatives do not match the primary control exactly; they reduce residual risk to an acceptable level.

**Core Characteristics**
- **Alternative implementation**: The control substitutes for a preferred control that is impractical, unavailable, or delayed.
- **Comparable protection goal**: Compensating controls aim to deliver equivalent or sufficient risk reduction rather than identical functionality.
- **Documented justification**: Organizations typically record why the primary control cannot be used and how the compensating control addresses the risk.
- **Cross-category application**: Compensating measures appear in technical configurations, managerial decisions, operational procedures, and physical arrangements.

Compensating controls differ from preventive controls (which stop activity before success), detective controls (which identify events that occur), corrective controls (which restore systems after an incident), deterrent controls (which discourage attempts through psychological effect), and directive controls (which instruct people on required behavior).

**Common Compensating Controls by Category**

**Technical compensating controls**
- Enhanced logging, alerting, and continuous monitoring on systems that cannot be patched or upgraded immediately.
- Network segmentation, micro-segmentation, or stricter firewall rules that isolate vulnerable or legacy systems from broader network access.
- Application allow-listing or host-based intrusion prevention on endpoints that lack modern endpoint detection capabilities.
- Additional encryption or data loss prevention rules applied to compensate for weaker access controls on a specific repository.
- Just-in-time or temporary elevated access mechanisms that limit standing privileges when full privileged access management is not yet deployed.

**Managerial compensating controls**
- Formal risk acceptance with documented compensating measures and defined review dates when a primary control remains unimplemented.
- Temporary exceptions or exemptions that require additional oversight, reporting, or approval steps.
- Strengthened contractual requirements or vendor monitoring when a third-party system cannot meet preferred security standards.

**Operational compensating controls**
- Increased frequency of manual access reviews, log inspections, or configuration audits around systems that lack automated controls.
- Dual-control or two-person integrity procedures that require two individuals for sensitive actions when technical separation of duties is incomplete.
- Heightened security awareness or targeted training for users of systems that carry elevated residual risk.
- Manual verification steps inserted into processes that lack automated validation.

**Physical compensating controls**
- Increased security guard presence or more frequent patrols when electronic access control systems are offline or incomplete.
- Temporary physical barriers, additional locks, or relocated assets when preferred facility controls cannot be installed immediately.
- Enhanced visitor escort requirements or secondary identity checks at entry points that lack full badge integration.

**Intersection with Control Categories**
A compensating control receives its type label because it serves as an alternative when the preferred control is unavailable. The same control also carries a category label based on implementation method:

- Continuous enhanced monitoring on an unpatchable server is both technical and compensating.
- A documented risk acceptance with extra oversight requirements is both managerial and compensating.
- Analysts performing daily manual reviews of a high-risk system are both operational and compensating.
- Extra guard coverage during a period of broken electronic locks is both physical and compensating.

Compensating controls often combine with other types. Extra monitoring is also detective. Stricter segmentation is also preventive. The compensating label highlights that the organization selected the measure because the ideal control could not be applied.

**Implementation Considerations**
Organizations select compensating controls through risk analysis that confirms the alternative sufficiently reduces residual risk. Documentation records the gap, the chosen compensation, the expected effectiveness, and the planned timeline for implementing the preferred control when feasible.

Compensating controls require ongoing validation. Temporary measures can become permanent by default if organizations do not track and retire them. Periodic review ensures the compensation remains effective and that progress continues toward the preferred control.

When primary controls cannot be implemented, well-designed compensating controls maintain an acceptable security posture and demonstrate due diligence. They buy time, limit exposure, and keep residual risk within the organization’s tolerance while longer-term solutions are developed.

### Directive Security Controls

Directive security controls instruct people on required or prohibited behavior. Organizations deploy these controls to communicate clear expectations, mandate specific actions, and guide personnel toward compliant conduct.

A directive control tells individuals what they must do. An acceptable use policy states that employees must not share credentials and must lock workstations when leaving their desks. A standard operating procedure lists the exact steps for handling sensitive media. Posted signs require visitors to display badges at all times. These controls shape behavior through explicit direction rather than technical enforcement or physical barriers.

**Core Characteristics**
- **Instructional purpose**: The control communicates rules, required actions, or prohibited activities to people.
- **Behavioral guidance**: Directive controls rely on human understanding and compliance rather than automatic technical enforcement.
- **Foundation for other controls**: Clear direction enables effective implementation of preventive, detective, and corrective measures.
- **Cross-category application**: Organizations express directives through written policies, procedures, training content, signage, and system messages.

Directive controls differ from preventive controls (which actively block unauthorized activity), detective controls (which identify events that occur), corrective controls (which restore systems after an incident), deterrent controls (which discourage attempts through psychological effect), and compensating controls (which provide alternatives when preferred controls are unavailable).

**Common Directive Controls by Category**

**Technical directive controls**
- System banners, login messages, and on-screen notifications that state acceptable use rules or required security actions.
- Group Policy or configuration settings that display mandatory security messages or enforce user acknowledgment of policies.
- Application prompts that require users to confirm understanding of data handling rules before proceeding.

**Managerial directive controls**
- Security policies that mandate specific behaviors such as password construction, data classification handling, and incident reporting requirements.
- Standards that define mandatory technical and operational requirements (password length, encryption algorithms, access review frequency).
- Procedures and playbooks that list required step-by-step actions for change management, incident response, media handling, and account provisioning.
- Guidelines that recommend preferred practices while still directing personnel toward secure choices.
- Acceptable use policies that explicitly list permitted and forbidden activities along with expectations for compliance.

**Operational directive controls**
- Security awareness training content that instructs employees on how to recognize phishing, handle sensitive data, and report incidents.
- Briefings and onboarding sessions that communicate required security behaviors for new personnel.
- Job aids, checklists, and runbooks that personnel follow during routine and emergency security tasks.
- Verbal or written instructions from supervisors that reinforce mandatory security actions.

**Physical directive controls**
- Posted signs that require badge display, prohibit tailgating, or restrict access to authorized personnel only.
- Markings and labels on secure areas, media, or equipment that direct proper handling or indicate restricted status.
- Visitor instructions and escort requirements communicated at entry points.

**Intersection with Control Categories**
A directive control receives its type label because it instructs people on required behavior. The same control also carries a category label based on implementation method:

- A login banner stating acceptable use rules is both technical and directive.
- A written incident response policy that mandates reporting timelines is both managerial and directive.
- Training that teaches required reporting steps is both operational and directive.
- A sign requiring badge display is both physical and directive.

Directive controls often support other types. A policy that requires multi-factor authentication is directive; the technical MFA implementation is preventive. A procedure that requires daily log review is directive; the analyst performing the review is operational and the review itself is detective. Clear direction increases the effectiveness of every other control type.

**Implementation Considerations**
Organizations write directive controls in clear, actionable language so personnel understand exactly what is required. Ambiguous or overly complex instructions reduce compliance. Effective directives align with technical capabilities and operational realities; rules that personnel cannot follow create gaps.

Communication and acknowledgment matter. Organizations distribute policies, require formal acknowledgment, and reinforce direction through training and visible reminders. Regular review keeps directives current with technology, threats, and business processes.

When personnel receive clear, consistent direction and understand the required actions, directive controls establish the behavioral foundation that allows technical, operational, and physical controls to function as designed.

## Conclusion

Accurate classification of security controls remains a core skill for both the SY0-701 exam and practical security work. Every control carries a category that identifies its implementation method and one or more types that identify its functional purpose. Candidates who internalize both axes answer exam questions faster and with higher accuracy. Practitioners who apply the same dual lens select balanced controls, identify gaps, and maintain effective defense-in-depth across technical systems, policies, daily operations, and physical environments.
