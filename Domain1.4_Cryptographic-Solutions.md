# CompTIA Security+ (SY0-701) Domain 1.4 Explain the importance of using appropriate cryptographic solutions.

Domain 1.4 of CompTIA Security+ SY0-701 covers the cryptographic solutions that protect confidentiality, integrity, authenticity, and non-repudiation. The domain spans public-key infrastructure, encryption methods and levels, hardware and software key-protection tools, obfuscation techniques, hashing and related password protections, digital signatures, distributed ledgers, and the operational elements of digital certificates. Mastery of these topics enables candidates to select, implement, and evaluate appropriate cryptographic controls across diverse environments.

## Public key infrastructure (PKI)

Public key infrastructure provides the framework that binds public keys to verified identities and enables their trustworthy use at scale. PKI relies on asymmetric key pairs, digital certificates, and trusted authorities to support confidential communication, authentication, and non-repudiation across large environments.

The core cryptographic elements of PKI are the public key, the private key, and, when recovery is required, key escrow.

### Public key

A public key is the openly shared half of an asymmetric key pair. Anyone may possess and use the public key; it cannot decrypt data or forge signatures that require the corresponding private key.

In asymmetric cryptography the public key performs two primary functions:
- **Encryption** — A sender encrypts data with the recipient’s public key. Only the holder of the matching private key can decrypt the resulting ciphertext.
- **Signature verification** — A recipient verifies a digital signature by applying the claimed signer’s public key. Successful verification confirms both integrity of the message and origin from the private-key holder.

Public keys travel in digital certificates issued by a trusted certificate authority. The certificate binds the public key to an identity and supplies the cryptographic evidence needed for validation. Systems distribute public keys freely through directories, certificate stores, or direct exchange.

Because the public key is designed for open distribution, its compromise does not immediately expose encrypted data or allow signature forgery. Security depends on the continued secrecy of the matching private key and on the integrity of the certificate that asserts ownership of the public key.

Organizations protect the authenticity of public keys through certificate chains, revocation checking, and trusted root stores. When a public key is correctly bound to a verified identity, it enables confidential communication and non-repudiable signatures without prior shared secrets.

### Private key

A private key is the secret half of an asymmetric key pair. Only the legitimate owner must possess and protect it. Compromise of the private key allows an attacker to decrypt data encrypted to the matching public key and to forge digital signatures that appear to originate from the owner.

The private key performs two primary cryptographic operations:
- **Decryption** — The owner uses the private key to decrypt ciphertext that was encrypted with the corresponding public key.
- **Digital signature generation** — The owner creates a digital signature by applying the private key to a hash of the message. Anyone who possesses the matching public key can verify the signature.

Because the private key grants these powerful capabilities, organizations apply strict protection measures. Hardware security modules (HSMs), Trusted Platform Modules (TPMs), smart cards, and secure enclaves store private keys in tamper-resistant environments. Software-based keys receive strong encryption at rest and rigorous access controls. Key-generation ceremonies, dual control, and audit logging further reduce the risk of unauthorized exposure.

Private keys never travel across networks in unprotected form. Certificate authorities and relying parties receive only the public key. When a private key is lost, stolen, or suspected of compromise, the associated certificate is revoked and a new key pair is generated.

The security of every asymmetric system ultimately rests on continuous protection of the private key. Strong algorithms and correct public-key distribution cannot compensate for a private key that leaves the owner’s control.

### Key escrow

Key escrow is the practice of placing a copy of a cryptographic key with a trusted third party so that the key can be recovered under predefined conditions. Organizations use escrow primarily for private keys or symmetric keys that encrypt critical data, ensuring that encrypted information remains accessible if the original key holder is unavailable or the key is lost.

In a typical escrow arrangement the key owner generates or receives a key and deposits a protected copy with an escrow agent. Legal or contractual rules specify the exact circumstances under which the agent may release the key—examples include court order, employee departure, or declared disaster. Split-knowledge or dual-control techniques often require multiple authorized parties to cooperate before the escrowed key is reconstructed.

Key escrow balances availability against confidentiality risk. It prevents permanent data loss when keys are misplaced, yet it creates an additional target and potential point of unauthorized disclosure. Organizations therefore apply strong access controls, auditing, and legal safeguards around the escrow process and store escrowed material in highly protected environments such as hardware security modules.

When properly implemented, key escrow provides a controlled recovery path for encrypted assets without leaving the organization permanently locked out of its own data.

## Encryption

Encryption transforms readable data into ciphertext so that unauthorized parties cannot understand it. CompTIA Security+ SY0-701 requires understanding of the levels at which encryption is applied, the distinction between data-at-rest and data-in-transit protection, the two fundamental cryptographic approaches (symmetric and asymmetric), the methods used to establish shared secrets, the algorithms that implement these operations, and the key lengths that determine practical strength.

Organizations select and combine these elements according to data sensitivity, performance needs, threat models, and regulatory requirements to maintain confidentiality across storage and communication.

### Levels

**Full-Disk Encryption**

Full-disk encryption (FDE) encrypts the entire contents of a storage device, including the operating system, applications, and user data. The encryption engine operates below the file system, typically in the disk controller or through software that intercepts all disk I/O. Authentication (password, TPM, smart card, or PIN) unlocks the disk at boot time. Once unlocked, data is decrypted transparently for authorized processes. FDE protects data at rest if the device is lost or stolen while powered off or locked. It does not protect data while the system is running and the disk is unlocked.

**Partition Encryption**

Partition encryption applies cryptographic protection to one or more selected partitions on a disk while leaving other partitions unencrypted. Administrators choose which volumes require protection, reducing performance overhead compared with full-disk encryption. The approach is useful when only specific data sets need strong protection or when system partitions must remain unencrypted for compatibility or recovery reasons.

**File Encryption**

File encryption protects individual files or selected groups of files. The operating system or an application encrypts the file contents and typically manages the associated keys through a user or system keystore. File-level encryption allows granular control—sensitive documents can be encrypted while other files remain in plaintext. It remains effective even if the underlying disk or volume is not encrypted, and encrypted files retain protection when copied to other media.

**Volume Encryption**

Volume encryption protects a logical storage volume, which may span one or more physical disks or partitions. Technologies such as encrypted virtual disks or software-defined volumes apply encryption to the entire volume. The volume must be unlocked (mounted with the correct key or credentials) before its contents become accessible. Volume encryption offers a middle ground between full-disk and file-level approaches, securing a defined collection of data without encrypting the entire physical device.

**Database Encryption**

Database encryption protects data managed by a database management system. Implementation options include transparent data encryption of data files or tablespaces, or column-level encryption of specific sensitive fields. The database engine handles encryption and decryption, often with keys stored in a secure external module. Database encryption defends against unauthorized access to database files at rest and can limit exposure even for privileged database administrators when properly configured.

**Record Encryption**

Record encryption protects individual records or fields within a data store or application. The application or middleware encrypts selected data elements before storage and decrypts them only for authorized processes. This granular approach minimizes the amount of ciphertext that must be handled and allows different records to use different keys or access policies. Record-level encryption is common for highly sensitive elements such as payment card numbers, Social Security numbers, or authentication secrets.

**Selection Considerations**

Organizations choose encryption levels according to the sensitivity of the data, performance requirements, key-management capabilities, and threat model. Higher-level encryption (full-disk or volume) provides broad coverage with simpler key handling for data-at-rest scenarios. Lower-level encryption (file, database, or record) delivers finer control and remains effective when data moves between systems. Many environments combine multiple levels to achieve defense in depth.

### Transport/communication

Transport or communication encryption protects data while it moves between systems. The encryption operates on the network path so that intercepted traffic remains unreadable without the correct keys.

Protocols such as Transport Layer Security (TLS) and its predecessor Secure Sockets Layer (SSL) establish an encrypted channel between client and server. The parties negotiate cipher suites, authenticate one or both ends with certificates, and then encrypt application data for the duration of the session. Internet Protocol Security (IPsec) provides similar protection at the network layer, encrypting entire IP packets between hosts or gateways. Secure Shell (SSH) encrypts remote-administration sessions. Virtual private network (VPN) solutions combine these or related protocols to create encrypted tunnels across untrusted networks.

Transport encryption defends against eavesdropping, man-in-the-middle alteration, and traffic analysis on the communication path. It does not protect data at rest on the endpoints; once the data is decrypted by the receiving application or system, other controls must secure it.

Organizations enforce transport encryption by requiring TLS for web and API traffic, mandating IPsec or VPN for sensitive network links, and disabling weak or obsolete protocol versions and cipher suites. Certificate validation, perfect forward secrecy, and strong key-exchange methods further strengthen the channel.

Properly implemented transport encryption ensures that data remains confidential and unmodified while in transit across any network segment that cannot be fully trusted.

### Asymmetric

Asymmetric encryption uses a mathematically related key pair—one public and one private—to protect confidentiality and support digital signatures. The public key may be freely distributed; the private key remains known only to its owner.

A sender encrypts data with the recipient’s public key. Only the matching private key can decrypt the ciphertext. This property enables secure communication without a pre-shared secret. Conversely, a private-key holder creates a digital signature by applying the private key to a message hash; anyone who possesses the corresponding public key can verify the signature, confirming both integrity and origin.

Common asymmetric algorithms include RSA, Elliptic Curve Cryptography (ECC), and Diffie-Hellman (used primarily for key exchange). Asymmetric operations are computationally more expensive than symmetric encryption, so systems typically use asymmetric cryptography to exchange or agree on a symmetric session key, then protect bulk data with the faster symmetric algorithm.

Asymmetric encryption underpins public-key infrastructure, certificate-based authentication, secure email, TLS handshakes, and non-repudiation services. Security depends on the continued secrecy of private keys and the trustworthy binding of public keys to identities through certificates.

### Symmetric

Symmetric encryption uses a single shared secret key for both encryption and decryption. The same key that transforms plaintext into ciphertext must be used to reverse the process and recover the original data.

Sender and receiver must possess identical copies of the key and must protect it from unauthorized disclosure. Key distribution and key management therefore become critical: if an attacker obtains the shared key, all data encrypted under that key becomes readable and the attacker can also forge ciphertext.

Symmetric algorithms operate efficiently on large volumes of data and impose relatively low computational overhead. Common algorithms include AES (Advanced Encryption Standard), ChaCha20, and legacy algorithms such as 3DES (now deprecated for most uses). Block ciphers process fixed-size blocks of data; stream ciphers generate a continuous keystream that is combined with the plaintext.

Because of its speed, symmetric encryption protects bulk data at rest and in transit. Systems frequently combine it with asymmetric cryptography: asymmetric methods securely exchange or agree on a temporary symmetric session key, after which the faster symmetric algorithm encrypts the actual payload.

Security of symmetric encryption rests entirely on the secrecy and strength of the shared key. Organizations enforce strong key generation, secure distribution, regular rotation, and protected storage to maintain confidentiality.

### Key exchange

Key exchange is the process that allows two parties to establish a shared secret key over an insecure channel without previously sharing a secret. The resulting key then protects subsequent communication, typically through symmetric encryption.

Asymmetric techniques enable secure key exchange. In Diffie-Hellman key exchange the parties generate ephemeral key pairs, exchange public values, and independently compute an identical shared secret. Elliptic-curve Diffie-Hellman (ECDH) performs the same function with smaller key sizes and equivalent security. RSA key transport encrypts a randomly generated symmetric key under the recipient’s public key so that only the private-key holder can recover it.

Modern protocols such as TLS combine key exchange with authentication. The server (and optionally the client) presents a certificate to prove identity, then the parties execute a key-exchange algorithm to derive session keys. Perfect forward secrecy is achieved when ephemeral Diffie-Hellman is used: compromise of long-term private keys does not expose past session keys.

Key exchange must resist man-in-the-middle attacks. Without authentication of the exchanged public values, an active attacker can interpose and establish separate keys with each party. Certificate validation, pre-shared identity, or out-of-band verification supply the required authentication.

Successful key exchange produces a shared secret known only to the legitimate parties and usable for efficient symmetric protection of bulk data. The security of the subsequent session rests on the strength of the key-exchange algorithm, the quality of random values, and the integrity of the authentication step that binds the exchange to verified identities.

### Algorithms

Cryptographic algorithms are the mathematical procedures that perform encryption, decryption, hashing, and digital signature operations. Security depends on the algorithm’s design strength, correct implementation, and appropriate key sizes.

Symmetric algorithms use a single shared key. AES (Advanced Encryption Standard) is the current standard for bulk encryption and operates on 128-bit blocks with key lengths of 128, 192, or 256 bits. ChaCha20 is a high-performance stream cipher often paired with Poly1305 for authenticated encryption. Older algorithms such as DES and 3DES are deprecated because of insufficient key length or practical attacks.

Asymmetric algorithms rely on key pairs. RSA bases security on the difficulty of factoring large integers and remains widely used for key transport and digital signatures. Elliptic Curve Cryptography (ECC) provides equivalent security with smaller keys and lower computational cost; common curves include P-256 and Curve25519. Diffie-Hellman and its elliptic-curve variant (ECDH) enable secure key exchange.

Hash algorithms produce fixed-length digests. SHA-256 and SHA-3 are current secure choices; MD5 and SHA-1 are broken for collision resistance and must not be used for security-critical purposes.

Organizations select algorithms according to current cryptographic standards, performance constraints, and regulatory requirements. Weak or obsolete algorithms are disabled through configuration and policy so that only approved, secure suites remain available. Regular review ensures that algorithm choices continue to resist known attacks as computing power and cryptanalysis advance.

### Key length

Key length is the size of a cryptographic key measured in bits. Longer keys increase the computational effort required for brute-force attacks and generally provide stronger security, provided the algorithm itself remains sound.

Symmetric keys rely solely on length and secrecy for strength. AES accepts 128-, 192-, or 256-bit keys. A 128-bit key already renders exhaustive search infeasible with current and near-term technology; 256-bit keys supply additional margin against future advances. Shorter symmetric keys, such as the 56-bit DES key, have been broken and are obsolete.

Asymmetric keys require greater length because the underlying mathematical problems (integer factorization or discrete logarithms) admit more efficient attacks than simple brute force. RSA keys of 2048 bits are the current minimum for most uses; 3072-bit or 4096-bit keys provide longer-term protection. Elliptic-curve keys achieve comparable security with far smaller sizes: a 256-bit ECC key roughly matches a 3072-bit RSA key in strength.

Security standards and regulatory frameworks publish minimum key-length requirements that evolve as computing power and cryptanalytic techniques improve. Organizations enforce these minima through cryptographic policy, configuration baselines, and automated scanning. Using a strong algorithm with an insufficient key length produces a false sense of security and leaves data vulnerable to practical attack.

Key length must be evaluated together with algorithm choice, implementation quality, and key-management practices. Adequate length is a necessary but not sufficient condition for cryptographic strength.

## Tools

CompTIA Security+ SY0-701 identifies hardware and software tools that protect cryptographic keys and sensitive operations. Trusted Platform Modules supply a hardware root of trust on individual devices. Hardware security modules provide high-assurance, tamper-resistant key storage and cryptographic processing for critical systems. Key management systems centralize the generation, distribution, rotation, and control of keys across the enterprise. Secure enclaves create isolated execution environments that shield code and data even when the host operating system is compromised.

These tools reduce reliance on software-only protections and limit the exposure of key material to the broader computing environment.

### Trusted Platform Module (TPM)

A Trusted Platform Module is a dedicated microcontroller that provides hardware-rooted cryptographic functions and secure storage. The TPM is soldered or otherwise fixed to the system motherboard and resists software-based extraction of its secrets.

The TPM generates, stores, and manages cryptographic keys inside a protected boundary. Private keys created within the TPM can be configured so that they never leave the chip in usable form. The module also supports secure random-number generation, cryptographic hashing, and asymmetric operations.

During boot the TPM measures firmware, bootloader, and operating-system components and records the measurements in Platform Configuration Registers (PCRs). Sealed encryption keys can be bound to specific PCR values so that data decrypts only when the system has booted into an expected, untampered state. This capability underpins measured boot and full-disk encryption solutions that require hardware attestation of platform integrity.

Remote attestation allows a TPM-equipped system to prove its software state to a remote verifier by signing current PCR values with an attestation key. Device health and compliance checks in Zero Trust and network-access-control architectures frequently rely on this feature.

Because the TPM is a hardware root of trust, compromise of the operating system does not automatically expose keys stored inside the module. Organizations enable and provision TPMs to strengthen key protection, support disk encryption, and supply verifiable evidence of platform integrity.

### Hardware security module (HSM)

A hardware security module is a dedicated, hardened cryptographic device that generates, stores, and manages keys inside a tamper-resistant boundary. HSMs provide higher assurance than software key stores or general-purpose TPMs for high-value keys and high-throughput cryptographic operations.

The HSM performs encryption, decryption, digital signature generation, and key-agreement functions without exposing raw private key material. Keys can be created inside the module and configured so that they never leave in cleartext. Access to cryptographic functions requires authentication of the calling application or operator, often through multi-factor or dual-control mechanisms.

Physical and logical tamper protections detect or respond to intrusion attempts by deleting sensitive material or rendering the device inoperable. Many HSMs undergo independent validation to standards such as FIPS 140-2 or FIPS 140-3, providing measurable assurance of the protection boundary.

Organizations deploy HSMs to protect certificate-authority root and intermediate keys, payment-processing keys, code-signing keys, and large-scale TLS private keys. Network-attached HSMs serve multiple applications simultaneously while maintaining centralized key control and audit logging.

Because the HSM isolates critical keys from the host operating system and application memory, compromise of a server does not automatically yield the keys themselves. Proper lifecycle management—generation, backup under dual control, rotation, and zeroization—preserves the security advantages of the hardware boundary.

### Key management system

A key management system (KMS) is a centralized solution that generates, distributes, stores, rotates, and revokes cryptographic keys throughout their lifecycle. Organizations use a KMS to enforce consistent policy, reduce manual handling of secrets, and maintain auditability across applications and infrastructure.

The KMS creates keys inside a protected boundary—often backed by a hardware security module—and releases them only to authenticated and authorized clients under defined policy. Applications request keys or cryptographic operations through secure APIs rather than embedding long-term secrets in code or configuration files. The system logs every key creation, access, rotation, and deletion event.

Lifecycle functions include automated rotation on a schedule or after a security event, secure backup and recovery under dual control, and immediate revocation when a key is compromised or no longer needed. Access policies can restrict keys by application identity, environment, time, or geographic location.

Cloud providers and on-premises products both offer KMS capabilities. Cloud KMS services integrate with identity platforms and support envelope encryption, in which a master key protected by the KMS encrypts data-encryption keys that remain under customer control.

A well-operated key management system removes the need for developers and administrators to handle raw key material, enforces least-privilege access to cryptographic functions, and supplies the visibility required for compliance and incident response. Without centralized key management, keys proliferate in unmanaged locations and become difficult to rotate or revoke when compromise occurs.

### Secure enclave

A secure enclave is an isolated, hardware-protected execution environment that runs sensitive code and protects data even when the main operating system is compromised. The enclave maintains its own memory encryption and access controls so that processes outside the enclave cannot read or alter its contents.

The processor reserves a protected region of memory and enforces hardware-level isolation. Code loaded into the enclave is measured and attested; remote parties can verify that the expected code is running inside a genuine enclave before releasing secrets to it. Keys and sensitive material generated or unsealed inside the enclave remain inaccessible to the host operating system, hypervisor, or other applications.

Secure enclaves support use cases such as protecting private keys, processing confidential data, and performing attestation for device health. Mobile devices and modern servers implement enclave technologies under different commercial names, yet all share the same design goal: a hardware-rooted boundary that limits the trusted computing base for high-value operations.

Because the enclave’s security rests on hardware isolation rather than operating-system controls, compromise of the host does not automatically expose enclave-resident secrets. Organizations use secure enclaves to raise the assurance level of key storage, cryptographic operations, and sensitive computations beyond what software-only protections can achieve.

## Obfuscation

Obfuscation techniques protect sensitive data by concealing its presence or replacing it with non-sensitive substitutes. Steganography hides data inside ordinary carrier files so that the existence of the secret remains undetected. Tokenization substitutes irreversible tokens for original values and stores the real data in a protected vault. Data masking replaces sensitive content with realistic but fictitious values for use in non-production environments. These methods reduce exposure, limit compliance scope, and complement encryption by minimizing the sensitive data that systems and users actually handle.

### Steganography

Steganography hides the existence of a message or file inside another, seemingly innocuous carrier so that observers do not realize secret communication is occurring. Unlike encryption, which makes content unreadable but visible as ciphertext, steganography conceals the fact that hidden data is present at all.

Common carrier files include images, audio, video, and documents. Techniques embed the secret payload in unused or least-significant portions of the carrier—for example, altering the least-significant bits of image pixels or inserting data into audio samples below the threshold of human perception. The modified carrier appears normal when opened with ordinary software.

Detection relies on statistical analysis, visual or auditory anomalies, or specialized steganalysis tools that look for patterns inconsistent with unmodified files. Because the payload is often small relative to the carrier, steganography alone provides limited bandwidth and is frequently combined with encryption: the secret data is encrypted first, then embedded.

Organizations encounter steganography both as a defensive obfuscation method and as an adversarial technique for covert data exfiltration or command-and-control channels. Security monitoring therefore includes inspection of media files and network transfers for signs of hidden content when threat models include covert channels.

### Tokenization

Tokenization replaces sensitive data elements with non-sensitive substitute values called tokens. The original data is stored in a secure, isolated repository; systems receive and process only the token.

A tokenization system generates a token that has no mathematical relationship to the original value or that is produced by a one-way, irreversible process. Applications store and transmit the token in place of the real data. When the original value is required, an authorized process presents the token to the tokenization service and receives the sensitive data under strict access controls and auditing.

Tokenization is widely applied to payment-card numbers, Social Security numbers, account identifiers, and other regulated data. Because most processing systems never see the original values, the scope of compliance requirements such as PCI DSS is reduced. A breach of a token-using application yields only tokens that cannot be reversed without access to the protected token vault.

Tokenization differs from encryption. Encrypted data can be decrypted with the correct key; a well-designed token cannot be reversed without the tokenization system itself. Format-preserving tokens retain the length and structure of the original data so that existing applications and databases require minimal modification.

Organizations implement tokenization to minimize the exposure of sensitive data, shrink compliance scope, and limit the impact of application-level breaches while still enabling necessary business processing.

### Data masking

Data masking replaces sensitive values with realistic but fictitious substitutes so that non-production environments or unauthorized viewers never receive the original data. The masked data retains the format and statistical characteristics needed for development, testing, or analytics while removing actual sensitive content.

Common techniques include:
- Substitution of real values with fabricated but plausible values
- Shuffling of values within a column
- Redaction or nulling of selected fields
- Encryption-style transformation that remains irreversible in the masked environment

Static data masking produces a permanent sanitized copy of a database for use in development or test systems. Dynamic data masking leaves the original data intact in the production repository and applies masking rules in real time according to the identity and privileges of the requesting user.

Organizations apply data masking to protect personal information, payment data, and proprietary records when production data must be used outside the highest-security environments. Because the masked values have no recoverable link to the originals, exposure of a masked data set does not disclose the true sensitive information.

Effective masking preserves referential integrity and application functionality so that systems continue to operate correctly while eliminating unnecessary risk of data exposure.

## Hashing

Hashing converts an arbitrary-length input into a fixed-length string of bits called a digest or hash value. The process is one-way: computing the digest from the input is straightforward, yet recovering the original input from the digest is computationally infeasible.

A cryptographic hash function produces a unique digest for each distinct input with extremely high probability. Any change to the input—even a single bit—produces a completely different digest. This sensitivity enables integrity verification: a system computes the hash of data at one point in time and later recomputes it; matching digests confirm that the data remains unaltered.

Common secure hash algorithms include SHA-256 and SHA-3. Older algorithms such as MD5 and SHA-1 are collision-resistant no longer and must not be used for security purposes. Hash functions are deterministic and do not use keys; the same input always yields the same digest.

Hashing supports multiple security functions:
- File and message integrity verification
- Password storage (combined with salting and key-stretching)
- Digital signature generation (the signature is applied to the hash rather than the full message)
- Blockchain and change-detection mechanisms

Because hashing is irreversible, it does not provide confidentiality. When confidentiality is required, encryption must be used instead of or in addition to hashing. Organizations rely on hashing whenever they need reliable, efficient proof that data has not been modified.

## Salting

Salting adds a unique, random value to a password (or other secret) before the system computes its hash. The salt is stored alongside the resulting hash so that the same password can be verified later.

Without a salt, identical passwords always produce identical hash values. An attacker can pre-compute hashes of common passwords (a rainbow table) and compare them against an entire stolen password file in a single pass. A unique salt for every password forces the attacker to recompute hashes for each individual entry, rendering pre-computed tables useless and dramatically increasing the cost of an offline attack.

The salt itself is not secret; it must be available at verification time. Security comes from its uniqueness and randomness. Systems generate a new cryptographically random salt for every password and store the pair (salt, hash). During authentication the system retrieves the salt, concatenates or otherwise combines it with the supplied password, hashes the result, and compares the digest to the stored value.

Salting is a mandatory companion to password hashing. Combined with a slow, memory-hard hashing algorithm (such as bcrypt, scrypt, or Argon2), it provides the primary defense against offline password-cracking attempts after a database breach.

## Digital signatures

A digital signature is a cryptographic value that binds a message or document to a specific private key, providing integrity, authentication of origin, and non-repudiation.

The signer computes a hash of the message and encrypts (or otherwise transforms) that hash with the signer’s private key. The resulting signature is transmitted with the message. Any recipient who possesses the corresponding public key can reverse the transformation and compare the recovered hash with a freshly computed hash of the received message. Matching hashes confirm that the message has not been altered and that the private-key holder produced the signature.

Digital signatures rely on asymmetric cryptography and a trustworthy binding of public keys to identities, normally supplied by digital certificates. Because only the private-key holder can create a valid signature, the signer cannot later deny having signed the message (non-repudiation), provided the private key remains under the signer’s exclusive control.

Common algorithms include RSA signatures, ECDSA, and EdDSA. Digital signatures protect software updates, email (S/MIME), documents, code, certificates, and any data whose origin and integrity must be verifiable. They form a foundational mechanism for authentication, integrity, and accountability across secure communications and public-key infrastructures.

## Key stretching

Key stretching deliberately slows the computation of a derived key or password hash so that brute-force and dictionary attacks become far more expensive. The technique repeatedly applies a cryptographic function or uses memory-hard algorithms to increase the time and resources required for each guess.

When a user supplies a password, the system feeds the password and a unique salt into a stretching function such as PBKDF2, bcrypt, scrypt, or Argon2. These functions iterate thousands or millions of times or consume substantial memory, producing a final derived key or hash that is stored for later verification. An attacker who obtains the stored value must perform the same expensive computation for every candidate password, making large-scale offline cracking impractical.

Key stretching is applied primarily to password-based key derivation and password storage. It does not replace salting; the two mechanisms work together. The salt ensures uniqueness; stretching multiplies the cost of each verification attempt.

Organizations configure iteration counts or memory parameters high enough to impose significant delay on attackers while remaining acceptable for legitimate authentication latency. As hardware improves, the work factor is increased to maintain the same relative security margin. Properly implemented key stretching converts weak or moderate human-chosen passwords into values that resist practical offline attack.

## Blockchain

A blockchain is a distributed, append-only ledger that records transactions in linked, cryptographically protected blocks. Each block contains a cryptographic hash of the previous block, a timestamp, and transaction data. Altering any historical record changes its hash and breaks the chain of subsequent blocks, making tampering evident.

Nodes in the network maintain identical copies of the ledger and reach agreement through a consensus mechanism before accepting new blocks. Because no single party controls the ledger and every participant can verify the entire history, blockchain provides integrity and transparency without a central trusted authority.

Hashing supplies the linkage and integrity protection. Digital signatures authenticate the parties that submit transactions. Once a block is confirmed and additional blocks are added after it, reversing or modifying earlier entries becomes computationally impractical.

Security applications of blockchain include secure logging, supply-chain provenance, certificate transparency, and decentralized identity systems. Organizations evaluate blockchain when they require a shared, immutable record among multiple parties that do not fully trust one another. The technology itself does not encrypt the data it stores; confidentiality must be provided by other means when needed.

## Open public ledger

An open public ledger is a blockchain or distributed ledger that any participant can read and, under the rules of the system, submit transactions to. The entire history of entries remains visible to all parties, and no central authority controls membership or access to the data.

Transparency is the defining characteristic. Every transaction and its associated cryptographic proofs can be independently verified by any observer. Consensus mechanisms ensure that only valid transactions are appended and that all honest participants converge on the same sequence of blocks.

Because the ledger is public and append-only, integrity is protected by the same hash-linked structure used in blockchain systems. Alteration of historical records is detectable and computationally impractical once subsequent blocks have been added. Confidentiality is not provided; sensitive data must be kept off-chain or encrypted before submission if privacy is required.

Open public ledgers support use cases that benefit from shared visibility and mutual distrust among participants, such as cryptocurrency networks, public certificate-transparency logs, and certain supply-chain or provenance systems. Organizations adopt them when the value of universal verifiability outweighs the loss of data privacy inherent in full public visibility.

## Certificates

Digital certificates bind public keys to verified identities and enable scalable trust across systems. Certificate authorities issue and sign certificates; revocation mechanisms (CRLs and OCSP) communicate when certificates are no longer valid. Certificates may be self-signed or issued by third parties, each with different trust implications. Roots of trust anchor the entire hierarchy. Certificate signing requests initiate issuance, and wildcard certificates extend a single credential across multiple subdomains. Together these elements form the operational foundation of public-key infrastructure.

### Certificate authorities

A certificate authority (CA) is a trusted entity that issues digital certificates binding public keys to identities. The CA verifies the identity of a subject, then signs a certificate containing the subject’s public key, identity information, validity period, and other attributes.

Relying parties trust certificates issued by a CA because they trust the CA’s root certificate, which is pre-installed in operating systems, browsers, and other trust stores. Intermediate CAs may operate under a root CA, forming a chain of trust. A certificate is validated by verifying the signatures up the chain until a trusted root is reached and by checking revocation status.

CAs follow documented registration and issuance practices. For public certificates, validation methods range from domain control checks to rigorous organizational identity verification. Private or enterprise CAs issue certificates for internal use and operate under organizational policy rather than public trust.

Compromise of a CA’s private key allows an attacker to issue fraudulent certificates that appear legitimate. Organizations therefore protect CA keys in hardware security modules, apply strict operational controls, and maintain the ability to revoke certificates rapidly. Certificate authorities form the trust anchor of public-key infrastructure and enable scalable authentication, encryption, and digital signatures across large environments.

### Certificate revocation lists (CRLs)

A certificate revocation list is a time-stamped, digitally signed inventory of certificates that a certificate authority has revoked before their scheduled expiration dates. Relying parties download and consult the CRL to determine whether a certificate presented to them remains valid.

The CA publishes the CRL at a well-known distribution point, typically listed inside each issued certificate. The list contains the serial numbers of revoked certificates and the revocation date. Because the CRL is signed by the CA, recipients can verify its authenticity and integrity. Clients cache CRLs for a defined period to reduce network traffic, then refresh them according to the next-update field.

Revocation occurs when a private key is compromised, an identity changes, or policy is violated. Until a certificate appears on a CRL (or is marked revoked by another mechanism), systems continue to treat it as valid. Latency between revocation decision and CRL publication creates a window of exposure; shorter publication intervals reduce that window.

CRLs scale poorly for very large environments because the list grows with every revocation and must be periodically redistributed. Many deployments therefore supplement or replace pure CRL checking with the Online Certificate Status Protocol (OCSP), which supplies real-time status for individual certificates. Nevertheless, CRLs remain a fundamental, standards-based method for distributing revocation information across public-key infrastructures.

### Online Certificate Status Protocol (OCSP)

The Online Certificate Status Protocol provides real-time verification of a digital certificate’s revocation status. A client queries an OCSP responder with the serial number of the certificate in question; the responder returns a signed reply indicating whether the certificate is good, revoked, or unknown.

OCSP eliminates the need to download and parse entire certificate revocation lists. The client obtains a current, authoritative answer for the specific certificate it is validating, reducing latency and bandwidth compared with periodic CRL retrieval. The responder’s reply is digitally signed so the client can confirm authenticity and integrity of the status information.

OCSP stapling improves privacy and performance. The certificate-presenting server periodically obtains an OCSP response for its own certificate and includes (“staples”) that response in the TLS handshake. Clients therefore receive revocation status without contacting the CA’s responder directly, preserving client privacy and reducing load on the responder infrastructure.

Reliable OCSP operation requires highly available responders and short validity intervals on responses so that revocation information remains fresh. When OCSP checking is enforced and responders are reachable, systems can reject certificates promptly after revocation, closing the exposure window that exists with infrequently updated CRLs.

### Self-signed

A self-signed certificate is a digital certificate signed by the same entity whose identity it certifies. The issuer and the subject are identical; no external certificate authority validates or attests to the binding between the public key and the claimed identity.

Self-signed certificates are generated and signed with the subject’s own private key. They provide cryptographic functionality—encryption, authentication of the key holder, and integrity protection—but they supply no independent third-party assurance of identity. Relying parties must explicitly trust the certificate through manual installation into a trust store or by accepting a one-time security exception.

Organizations commonly use self-signed certificates in laboratory environments, internal testing, and closed systems where a formal public-key infrastructure is unnecessary or unavailable. They also appear as the root certificates of private certificate authorities; in that case the self-signed root is deliberately distributed to all trusting parties as the trust anchor.

Because anyone can create a self-signed certificate claiming any identity, browsers and operating systems display warnings when they encounter one that is not already trusted. Production public-facing services therefore rely on certificates issued by recognized certificate authorities rather than self-signed certificates. When self-signed certificates are used, secure distribution and careful management of the associated trust anchors remain essential to prevent man-in-the-middle substitution.

### Third-party

A third-party certificate is a digital certificate issued by an external certificate authority that is independent of the organization relying on the certificate. The CA verifies the subject’s identity according to its published policies, then signs the certificate with its own private key.

Because operating systems, browsers, and devices already contain the root certificates of recognized public CAs, third-party certificates are trusted automatically by most clients without additional configuration. This universal trust makes third-party certificates the standard choice for public-facing websites, public APIs, and any service that must be validated by arbitrary external parties.

Organizations purchase or obtain third-party certificates through commercial CAs or free public CAs. The issuance process includes identity or domain validation whose rigor varies by certificate type (domain validation, organization validation, or extended validation). After issuance, the organization installs the certificate and its private key on the appropriate servers and monitors the certificate’s validity period and revocation status.

Third-party certificates shift the burden of identity proof and global trust distribution to the external CA. They eliminate the need for the organization to distribute its own root certificate to every potential client, at the cost of dependence on the CA’s security practices, availability, and pricing. For services that must be trusted by the general public, third-party certificates remain the practical and expected solution.

### Root of trust

A root of trust is a foundational component whose integrity is assumed rather than verified by other elements of the system. All subsequent security decisions and trust relationships derive from this root.

In public-key infrastructure the root of trust is the self-signed root certificate of a certificate authority. Operating systems and applications embed these root certificates in their trust stores. Any certificate that chains to a trusted root inherits that trust. Compromise of a root private key undermines every certificate issued under it.

In hardware the root of trust is typically a Trusted Platform Module, secure enclave, or immutable boot ROM that measures and attests to the integrity of later software stages. Because the hardware root cannot be altered by ordinary software, it supplies a reliable starting point for measured boot and remote attestation.

Organizations protect roots of trust with the highest level of physical, procedural, and cryptographic controls. Access to root keys is limited, operations occur under dual control, and hardware security modules or equivalent protections isolate the material. When a root is compromised, every dependent key, certificate, or measurement becomes suspect and must be replaced.

A system can have only a small number of roots of trust; expanding the set of trusted roots expands the attack surface. Careful selection, protection, and monitoring of roots of trust therefore determine the ultimate security of the entire trust hierarchy.

### Certificate signing request (CSR) generation

A certificate signing request is a digitally signed message that an applicant sends to a certificate authority to obtain a digital certificate. The CSR contains the public key that will appear in the certificate, identity information about the subject, and a signature proving possession of the corresponding private key.

The applicant first generates a public/private key pair. The private key remains securely stored and is never transmitted. The public key, together with requested subject attributes (common name, organization, locality, and optional subject-alternative names), is packaged into the CSR. The applicant signs the CSR with the private key so the CA can verify that the requester controls the key pair.

The completed CSR is submitted to the CA through a web portal, email, or automated protocol. The CA validates the identity claims according to its policies, then issues a certificate that binds the supplied public key to the verified identity and signs the certificate with the CA’s own private key.

Secure CSR generation requires that the private key be created in a protected environment (hardware security module, secure enclave, or properly access-controlled software store) and that the CSR itself be protected from tampering during submission. Organizations treat private-key generation and CSR creation as controlled steps in the certificate lifecycle so that the resulting certificate accurately represents a key pair that remains under the applicant’s sole control.

### Wildcard

A wildcard certificate is a digital certificate that secures a base domain and all of its first-level subdomains with a single certificate. The common name or subject-alternative name contains an asterisk followed by the domain (for example, *.example.com). The certificate is therefore valid for www.example.com, mail.example.com, api.example.com, and any other hostname that matches the pattern.

Wildcard certificates simplify administration when an organization operates many subdomains under one domain. Only one certificate and private key need to be managed, renewed, and installed. The same private key, however, is shared across every covered subdomain; compromise of that key affects all of them.

Most public certificate authorities issue wildcards only for a single level of subdomain. A certificate for *.example.com does not cover deeper names such as a.b.example.com or the apex domain example.com itself unless those names are explicitly included.

Organizations weigh convenience against risk. Wildcard certificates reduce operational overhead yet expand the blast radius of a private-key compromise and may complicate least-privilege key management. When subdomains have different security requirements or are managed by separate teams, individual certificates often provide better isolation than a single wildcard.

## Conclusion

Cryptographic solutions form a layered system of protection. Public-key infrastructure and certificates establish scalable trust. Encryption, hashing, and digital signatures safeguard data at rest and in transit. Hardware roots of trust and key-management systems protect the keys themselves. Obfuscation techniques further limit exposure of sensitive values. Blockchain and open ledgers supply shared, tamper-evident records. Together these mechanisms allow organizations to achieve confidentiality, integrity, authenticity, and non-repudiation while managing the practical constraints of performance, recovery, and operational complexity.
