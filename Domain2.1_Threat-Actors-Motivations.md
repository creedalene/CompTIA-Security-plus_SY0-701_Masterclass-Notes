# CompTIA Security+ (SY0-701) Domain 2.1 Compare and contrast common threat actors and motivations.

Domain 2.1 of CompTIA Security+ SY0-701 examines who conducts cyber attacks, the attributes that shape their behavior, and the motivations that drive their operations. Threat actors range from highly resourced nation-state groups to opportunistic unskilled attackers, ideologically driven hacktivists, trusted insiders, financially motivated criminal organizations, and the unmanaged risk introduced by shadow IT. Key attributes—internal versus external positioning, available resources and funding, and level of sophistication—determine the methods an actor can sustain and the defenses required to counter them. Motivations span data exfiltration, espionage, service disruption, blackmail, financial gain, philosophical or political beliefs, ethical rationales, revenge, deliberate chaos, and support for warfare. Understanding these dimensions together enables accurate threat modeling and proportionate security investment.

## Threat actors

CompTIA Security+ SY0-701 classifies threat actors by capability, resources, and motivation. Nation-state groups pursue geopolitical objectives with advanced, persistent operations. Unskilled attackers rely on ready-made tools and opportunistic targeting. Hacktivists seek publicity for ideological causes. Insider threats abuse or misuse legitimate access from within. Organized-crime groups operate for financial profit at scale. Shadow IT introduces unmanaged systems through well-intentioned but unauthorized employee actions. Understanding each actor’s typical goals, methods, and constraints enables defenders to prioritize controls and detection strategies appropriately.

### Nation-state

A nation-state threat actor is a government-sponsored or government-directed group that conducts cyber operations in support of national interests. These actors possess substantial resources, advanced technical capabilities, and long-term strategic objectives.

Nation-state groups perform espionage, intellectual-property theft, disruption of critical infrastructure, influence operations, and preparation of the battlefield for potential future conflict. They often maintain persistent access inside target networks for months or years, moving carefully to avoid detection while harvesting data or establishing covert control.

Capabilities typically include custom malware, zero-day exploits, sophisticated social-engineering campaigns, and supply-chain compromises. Attribution is deliberately obscured through false flags, compromised intermediate systems, and the use of proxy groups. Operations may target government agencies, defense contractors, energy systems, telecommunications, research institutions, and political organizations.

Motivations center on geopolitical advantage, economic competitiveness, military superiority, and domestic political control. Because nation-state actors operate with state-level funding and legal immunity inside their own borders, traditional law-enforcement deterrence has limited effect. Defenders therefore prioritize detection of advanced persistent threats, network segmentation, rigorous monitoring, and rapid containment over purely preventive measures.

Organizations that support critical infrastructure, hold sensitive government or intellectual property, or operate in geopolitically sensitive sectors treat nation-state actors as a high-tier threat requiring elevated detection capabilities and incident-response readiness.

### Unskilled attacker

An unskilled attacker, often called a script kiddie, lacks deep technical knowledge and relies on pre-written tools, scripts, or publicly available exploits. These actors download ready-made malware, exploit kits, or attack frameworks and apply them with minimal customization.

Unskilled attackers typically target systems that remain unpatched or misconfigured. They scan large address ranges for known vulnerabilities, launch commodity ransomware, or attempt simple credential attacks. Success depends more on the target’s poor hygiene than on the attacker’s sophistication.

Motivations usually include curiosity, desire for recognition inside online communities, minor financial gain, or the simple thrill of causing disruption. Because the tools are widely distributed, the same attack patterns appear repeatedly across many victims.

Although individual unskilled attackers pose limited strategic threat, their volume creates constant noise and can still produce serious damage when they encounter exposed systems. Automated patching, attack-surface reduction, and basic email and web filtering neutralize the majority of these opportunistic attempts. Defenders treat unskilled attackers as a baseline threat that proper hygiene and commodity security controls effectively mitigate.

### Hacktivist

A hacktivist is a threat actor who uses cyber attacks to promote a political, social, or ideological agenda. The primary objective is visibility and message amplification rather than financial profit or long-term espionage.

Hacktivists commonly employ website defacement, distributed denial-of-service attacks, data leaks, and doxing. They select targets that symbolize the opposing viewpoint—government agencies, corporations, political organizations, or individuals—and publicize the attacks to attract media attention and inspire supporters.

Technical capability varies widely. Some hacktivist groups operate with modest skills and rely on publicly available tools; others demonstrate moderate sophistication in coordination and target selection. Operations are often opportunistic and time-bound to specific events or controversies.

Because motivation centers on publicity and ideological impact, hacktivists frequently claim responsibility and leave political messages. This visibility aids attribution but also increases the reputational damage inflicted on the victim. Organizations that become symbolic targets maintain elevated monitoring during periods of social or political tension and prepare communication plans for rapid public response.

### Insider threat

An insider threat originates from individuals who already possess authorized access to an organization’s systems, data, or facilities. The actor may be a current or former employee, contractor, or business partner.

Insider threats fall into two broad categories. Malicious insiders intentionally abuse their access for personal gain, revenge, espionage, or ideological reasons. Negligent insiders unintentionally create risk through carelessness, ignored policy, or social-engineering victimization. Both categories can produce severe damage because the actor begins operations from a position of trust and often inside security perimeters.

Common actions include theft of intellectual property, unauthorized data exfiltration, sabotage of systems or data, and facilitation of external attacker access. Detection is difficult because the activity may resemble legitimate work. Behavioral analytics, user-activity monitoring, data-loss-prevention controls, and strict least-privilege enforcement help surface anomalous patterns.

Organizations reduce insider risk through careful hiring and offboarding procedures, continuous access review, segregation of duties, security awareness training, and a culture that encourages reporting of suspicious behavior. Technical controls alone cannot eliminate the threat; governance and personnel processes remain essential. Because insiders already bypass many perimeter defenses, compensating detection and response capabilities receive elevated priority.

### Organized crime

Organized-crime threat actors are structured groups that conduct cyber attacks primarily for financial gain. These groups operate with clear hierarchies, specialized roles, and persistent business models that treat cybercrime as a profitable enterprise.

Typical activities include ransomware deployment, banking trojans, business-email compromise, credit-card theft, identity fraud, and the sale of stolen data or access on underground markets. Many groups offer ransomware-as-a-service or other turnkey attack kits, allowing lower-skilled affiliates to conduct operations while the core organization supplies infrastructure and takes a percentage of profits.

Technical capability ranges from moderate to advanced. Successful groups maintain reliable command-and-control infrastructure, develop or purchase sophisticated malware, and refine social-engineering techniques that maximize payment rates. They frequently target organizations with low tolerance for downtime—hospitals, municipalities, and mid-sized enterprises—because those victims are more likely to pay.

Motivation remains consistently financial. Attacks are selected and timed according to expected return on investment rather than political or ideological goals. Law-enforcement pressure and sanctions can disrupt specific groups, yet the overall ecosystem adapts quickly by shifting infrastructure, rebranding, or moving to new affiliates.

Defenders treat organized-crime actors as a high-volume, high-impact threat that demands reliable backups, network segmentation, email security, endpoint detection, and rapid incident-response capabilities focused on containment and recovery.

### Shadow IT

Shadow IT refers to information-technology systems, applications, or services that employees deploy and use without the knowledge or approval of the organization’s IT or security teams. The actors are typically well-intentioned staff seeking to improve productivity or solve immediate problems, yet their actions create unmanaged risk.

Common examples include unsanctioned cloud storage accounts, unauthorized SaaS applications, personal devices used for work data, and ad-hoc collaboration platforms. Because these resources fall outside official inventory, patching, configuration management, access control, and monitoring processes, they expand the attack surface and create gaps in visibility.

Data stored or processed in shadow IT may violate regulatory requirements, escape data-loss-prevention controls, and become inaccessible during incident response or e-discovery. Credentials reused across personal and corporate services further increase exposure.

Organizations reduce shadow IT through clear policy, streamlined approval processes for legitimate tools, continuous discovery of unauthorized cloud services, and security-awareness training that explains the risks. When business units can obtain approved solutions quickly, the incentive to bypass official channels declines. Detection technologies that inventory cloud usage and network connections help surface unknown assets so that risk can be assessed and either formalized or eliminated.

## Attributes of actors

CompTIA Security+ SY0-701 evaluates threat actors according to key attributes that shape their behavior and the defenses required against them. Actors are classified as internal or external based on their starting relationship to the organization. Resources and funding determine the scale and persistence they can sustain. Level of sophistication and capability describes the technical skill and tradecraft they can apply. These attributes together allow defenders to anticipate likely methods, set realistic detection priorities, and allocate security investment proportionally to the threats they face.

### Internal/external

Threat actors are classified by their relationship to the target organization. This attribute determines initial access, available knowledge, and the controls that most effectively detect or contain them.

**Internal actors** already possess legitimate access credentials, physical entry, or trusted network placement. Employees, contractors, and business partners fall into this category. Because they operate inside existing trust boundaries, perimeter defenses provide little resistance. Detection therefore relies on behavioral monitoring, data-loss prevention, privilege review, and anomaly detection that can distinguish authorized activity from abuse or error.

**External actors** begin without authorized access. They must first breach perimeter controls, exploit public-facing services, or social-engineer their way inside. Nation-state groups, organized-crime operators, hacktivists, and unskilled attackers typically start as external actors. Once they obtain credentials or a foothold, they may continue to operate with the appearance of internal users.

Many sophisticated campaigns transition from external to internal positioning after the initial compromise. Defenders therefore maintain both strong perimeter controls to block external entry and robust internal detection to surface activity that originates from compromised or malicious trusted identities. Classification of an actor as internal or external guides the placement of monitoring and the prioritization of access-governance controls.

### Resources/funding

Resources and funding describe the financial, technical, and human capital available to a threat actor. This attribute strongly influences the duration, sophistication, and scale of operations an actor can sustain.

Well-funded actors maintain dedicated infrastructure, develop or purchase zero-day exploits, employ specialists, and operate for months or years without needing immediate returns. Nation-state groups and successful organized-crime enterprises typically occupy this tier. Abundant resources enable custom malware, extensive reconnaissance, supply-chain compromises, and the ability to absorb operational losses.

Actors with limited resources rely on publicly available tools, shared infrastructure, and opportunistic targeting. Unskilled attackers and many hacktivists fall into this category. Constrained funding forces them to reuse known exploits, favor high-volume low-effort campaigns, and abandon targets that require prolonged effort.

Funding sources vary. Nation-states draw on government budgets. Organized-crime groups reinvest criminal proceeds. Hacktivists may rely on donations or volunteer labor. Insiders leverage the access and knowledge already paid for by the victim organization.

Defenders assess an actor’s likely resources to gauge the expected sophistication of tools, the persistence of campaigns, and the investment required for effective detection and response. High-resource actors demand advanced detection capabilities and long-term hunting; low-resource actors are largely mitigated by consistent hygiene and commodity controls.

### Level of sophistication/capability

Level of sophistication describes the technical skill, operational tradecraft, and tool quality that a threat actor can apply. Capability determines how effectively an actor can bypass controls, maintain persistence, and achieve objectives while avoiding detection.

High-sophistication actors develop or commission custom malware, exploit zero-day vulnerabilities, conduct extensive reconnaissance, and employ advanced evasion techniques. They plan multi-stage operations, maintain operational security, and adapt quickly when defenders intervene. Nation-state groups and mature organized-crime enterprises typically demonstrate this level of capability.

Moderate-sophistication actors combine publicly available frameworks with limited customization. They can chain known exploits, perform effective social engineering, and sustain campaigns for weeks, yet they rarely produce novel attack methods. Many financially motivated groups operate in this range.

Low-sophistication actors rely almost entirely on ready-made tools, scripts, and exploit kits. They conduct opportunistic scans, reuse commodity malware, and abandon targets that require significant effort. Unskilled attackers and many opportunistic criminals fall into this category.

Sophistication is not static. Actors can purchase higher capability through criminal markets or improve over time through experience. Defenders evaluate the sophistication they are likely to face in order to set appropriate detection thresholds, allocate hunting resources, and decide which advanced controls justify their cost. Matching defensive investment to realistic adversary capability avoids both under-protection and wasteful over-engineering.

## Motivations

### Data exfiltration

Data exfiltration is the unauthorized transfer of data from an organization to a location controlled by a threat actor. It constitutes both a primary motivation for many attacks and the observable outcome of successful intrusion.

Actors move data through multiple channels: encrypted network connections, cloud-storage uploads, email, removable media, DNS tunneling, or steganographic embedding inside legitimate traffic. High-value targets include intellectual property, customer records, authentication credentials, strategic plans, and personal information that supports further fraud or espionage.

Exfiltration often occurs late in an attack lifecycle, after the actor has located and staged the desired data. Slow, low-volume transfers or blending with normal traffic patterns help evade detection. Once the data leaves the environment, the organization loses control over its confidentiality and may face regulatory penalties, competitive harm, or downstream abuse of the stolen information.

Defenders detect exfiltration through data-loss-prevention systems, network-traffic analysis, anomalous outbound volume or destination monitoring, and endpoint controls that restrict unauthorized transfer methods. Effective prevention combines least-privilege access, encryption of sensitive data at rest, network segmentation, and continuous monitoring of egress points. Rapid containment and assessment of what left the environment become critical once exfiltration is identified.

### Espionage

Espionage is the covert collection of sensitive information for strategic, political, military, or economic advantage. As a motivation it drives long-term, stealthy operations rather than immediate disruption or financial extortion.

Nation-state actors dominate cyber-enabled espionage, targeting government agencies, defense contractors, research institutions, critical-infrastructure operators, and commercial firms that hold valuable intellectual property or negotiation data. The objective is persistent access and continuous intelligence gathering while remaining undetected for as long as possible.

Operators prioritize quiet reconnaissance, credential theft, lateral movement, and careful data staging before exfiltration. Custom malware, zero-day exploits, and supply-chain compromises are common tools. Attribution is actively obscured so that the sponsoring state can maintain deniability.

Successful espionage yields intelligence that informs policy, military planning, economic competition, or future disruptive operations. Because the value lies in continued access, actors often refrain from destructive actions that would reveal their presence. Defenders therefore emphasize advanced detection of anomalous behavior, rigorous network segmentation, and continuous hunting for low-and-slow activity that commodity security tools may miss.

### Service disruption

Service disruption is the intentional degradation or interruption of an organization’s ability to deliver systems, applications, or business functions. As a motivation it drives attacks whose primary objective is unavailability rather than data theft or financial extortion.

Actors achieve disruption through distributed denial-of-service attacks, ransomware that encrypts critical systems, wiper malware that destroys data, sabotage of industrial controls, or physical attacks on infrastructure. Targets frequently include government services, financial institutions, healthcare providers, transportation systems, and energy operators—entities whose downtime produces immediate public or economic impact.

Motivations for disruption vary. Nation-states may seek to weaken an adversary’s operational capacity or create political pressure. Hacktivists aim to silence or embarrass opposing organizations. Organized-crime groups sometimes use disruption as leverage for ransom. Insider threats may act out of revenge or ideology.

Because the goal is visible impact, service-disruption attacks often produce rapid, high-profile effects. Defenders prioritize resilience: network and application redundancy, DDoS mitigation, tested backups and recovery procedures, segmentation that limits blast radius, and continuous monitoring that enables rapid isolation of affected systems. The measure of success for the defender is the ability to restore service within defined recovery-time objectives while preserving data integrity.

### Blackmail

Blackmail is the use of stolen or fabricated compromising information to coerce a victim into paying money, providing access, or taking specific actions. As a cyber motivation it combines data theft with explicit threats of public exposure or further harm.

Actors first obtain sensitive material—personal data, private communications, intellectual property, or evidence of regulatory violations—through intrusion, insider access, or social engineering. They then contact the victim, demonstrate possession of the material, and demand payment or compliance under threat of release. Ransomware operations that threaten to publish stolen data (double extortion) represent a large-scale, industrialized form of blackmail.

Targets range from individuals to corporations and public figures. Corporate blackmail frequently focuses on data that would trigger regulatory fines, reputational damage, or competitive disadvantage. The coercion depends on the victim’s perception that the cost of exposure exceeds the cost of compliance.

Defenders reduce blackmail risk by limiting the volume of sensitive data that can be exfiltrated, detecting and blocking unauthorized outbound transfers, and maintaining incident-response plans that include legal, communications, and law-enforcement coordination. Once blackmail occurs, organizations must weigh payment against the likelihood of repeated demands and the value of preserving evidence for investigation. Prevention through strong data protection and egress monitoring remains more effective than post-incident negotiation.

### Financial gain

Financial gain is the motivation to obtain money or transferable economic value through cyber operations. It drives the majority of volume-based cybercrime and shapes the tactics of organized-crime groups and many opportunistic attackers.

Actors generate revenue through ransomware payments, business-email compromise, theft and sale of payment-card data, banking trojans, cryptocurrency theft, fraudulently initiated transfers, and the monetization of stolen personal or corporate data on underground markets. Some groups operate ransomware-as-a-service platforms, taking a percentage of affiliate earnings while supplying infrastructure and malware.

Target selection follows expected return on investment. Organizations with low tolerance for downtime, high insurance coverage, or large volumes of valuable data attract disproportionate attention. Attacks are refined to maximize payment probability and minimize operational cost.

Because the objective is profit rather than destruction or long-term access, financially motivated actors often prefer techniques that produce rapid, reliable returns. Defenders counter this motivation with reliable offline backups, network segmentation that limits ransomware spread, email and payment controls that block fraudulent transfers, and rapid detection that shortens the window for data theft or encryption. Reducing the economic attractiveness of an attack remains one of the most effective deterrents against financially driven threat actors.

### Philosophical/political beliefs

Philosophical or political beliefs motivate threat actors who conduct cyber operations to advance an ideology, protest a policy, or influence public opinion. The primary objective is message delivery and symbolic impact rather than financial profit or long-term intelligence collection.

Hacktivists constitute the most visible expression of this motivation. They select targets that represent opposing governments, corporations, or institutions and employ defacement, data leaks, denial-of-service attacks, or doxing to attract attention and rally supporters. Operations often coincide with real-world political events, anniversaries, or controversies to maximize visibility.

Capability varies from rudimentary script-driven campaigns to moderately coordinated efforts that combine social engineering with publicly available attack tools. Because publicity is essential to the goal, actors frequently claim responsibility and publish political statements alongside the technical effects.

Organizations that symbolize contested political or social issues maintain heightened monitoring during periods of elevated tension and prepare communication strategies for rapid public response. Defensive priorities focus on protecting public-facing services, limiting the exposure of sensitive internal data that could be leaked for propaganda value, and preserving service availability under denial-of-service pressure. The motivation itself is resilient to traditional financial deterrence; visibility and ideological reinforcement sustain the activity.

### Ethical

Ethical motivation describes actors who conduct cyber activities because they believe the actions are morally justified or serve a greater good. In the CompTIA framework this category includes both authorized security researchers operating under permission and unauthorized actors who claim moral legitimacy for their intrusions.

Authorized ethical actors—penetration testers, red-team operators, and bug-bounty researchers—work under explicit contracts or safe-harbor policies. Their goal is to discover and report vulnerabilities so that organizations can remediate them before malicious exploitation occurs. They follow scoped rules of engagement and disclose findings responsibly.

Unauthorized actors motivated by ethical beliefs may still violate law or policy. They often justify intrusions as exposing wrongdoing, protecting privacy, or forcing security improvements. Even when the claimed intention is beneficial, the absence of authorization places these actions outside legal and organizational boundaries and creates the same technical risk as other unauthorized access.

Organizations distinguish authorized ethical activity from unauthorized activity through clear written authorization, defined scopes, and formal reporting channels. Security programs that maintain well-publicized vulnerability-disclosure policies and bug-bounty programs channel ethical motivation into constructive paths and reduce the likelihood of unsolicited, potentially disruptive testing.

### Revenge

Revenge is the motivation to inflict harm on an organization or individual in retaliation for a perceived personal or professional wrong. The actor seeks emotional satisfaction or retribution rather than financial profit, intelligence, or ideological publicity.

Revenge-driven attacks frequently originate from insider threats—disgruntled current or former employees, contractors, or partners who already possess knowledge of systems and access pathways. External actors may also pursue revenge after business disputes, terminated relationships, or public conflicts. Typical actions include data destruction, unauthorized disclosure of sensitive information, sabotage of systems, or targeted harassment campaigns.

Because the motivation is personal, target selection is narrow and often highly specific. The actor may focus on particular systems, data sets, or individuals associated with the grievance. Timing frequently correlates with termination, disciplinary action, or other triggering events.

Organizations reduce revenge risk through structured offboarding that immediately revokes access, continuous monitoring of privileged activity, separation of duties, and workplace practices that limit the intensity of grievances. Detecting revenge activity relies on behavioral analytics and rapid correlation of anomalous actions with recent personnel events. Once an attack occurs, preserving evidence and coordinating with legal and human-resources teams become essential both for response and for potential prosecution.

### Disruption/chaos

Disruption and chaos describe the motivation to create disorder, undermine confidence, or demonstrate power by interfering with normal operations. The actor values the visible breakdown of systems and the resulting uncertainty more than financial profit or intelligence collection.

Attacks driven by this motivation include widespread denial-of-service campaigns, destructive malware that wipes data or renders systems unbootable, sabotage of industrial controls, and coordinated disinformation that amplifies technical effects. Targets are often chosen for maximum public visibility or societal impact—government services, financial networks, transportation, healthcare, or large public-facing platforms.

Actors may be nation-states seeking to destabilize an adversary, ideologically motivated groups aiming to erode trust in institutions, or individuals pursuing notoriety. The common thread is the intentional production of unpredictable or cascading failure rather than a controlled, reversible outcome such as ransomware encryption with a recovery key.

Defenders counter disruption-focused threats by building resilience: redundant systems, tested failover procedures, offline backups, network segmentation that limits blast radius, and rapid isolation capabilities. Monitoring for early indicators of destructive activity and maintaining crisis-communication plans further reduce the lasting impact of chaos-driven attacks. The measure of defensive success is the ability to contain damage and restore predictable operations before societal or organizational confidence erodes.

### War

War as a cyber motivation describes operations conducted in direct support of armed conflict or in preparation for kinetic hostilities. Nation-state actors use cyber capabilities to degrade an adversary’s military, economic, or civilian infrastructure, to collect battlefield intelligence, and to shape the information environment.

Objectives include disruption of command-and-control systems, disablement of logistics and energy networks, degradation of communications, and psychological impact on civilian populations. Attacks may occur in the lead-up to conventional conflict, concurrently with military operations, or as standalone coercive campaigns intended to achieve strategic effects without open warfare.

Techniques range from destructive malware and sophisticated denial-of-service attacks to precise compromise of industrial control systems and satellite or telecommunications infrastructure. Operations are typically planned at the state level, integrate with broader military doctrine, and operate under rules of engagement defined by the sponsoring government.

Defenders in sectors designated as critical infrastructure or defense-related industries treat war-motivated activity as a high-tier, low-frequency, high-impact threat. Preparation emphasizes resilience, segmentation of operational technology from enterprise networks, offline recovery capabilities, and close coordination with government defense and intelligence agencies. The distinguishing characteristic of this motivation is its explicit alignment with national military objectives rather than independent financial, ideological, or personal goals.

## Conclusion

Effective defense begins with clear recognition of the actors likely to target an organization, the resources and skills they can apply, and the outcomes they seek. Matching detection, prevention, and response capabilities to these realities allows security teams to prioritize controls, allocate resources efficiently, and reduce both the likelihood and the impact of successful attacks. Mastery of threat-actor types, attributes, and motivations provides the analytical foundation required for the remainder of the threat and vulnerability domains on the SY0-701 exam and for practical risk-based security decision-making.
