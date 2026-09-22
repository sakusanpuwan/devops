# Trust & Security with Google Cloud
## Trust & Security in the Cloud
### Cloud Security Principles

**Privileged Access Security Model** grants specific users access to a broader set of resources than ordinary users. E.g. a system administrator may have privileged acces to perform tasks such as troubleshooting and data restoration. It's essential to frequently manage and monitor access levels.

**Least Privilege Security Model** advocates granting users only minimum access they need to perform their job functions and no more. This reduces the risk of unauthorised access to sensitive data. E.g. a sales rep only needs access to CRM system not systems like payroll. 

**Zero Trust Architecture** implements strict access controls and continously verifies user identity and device health before granting access to resources. It assumes that threats can exist both inside and outside the network, so it requires continuous authentication and authorization for all users and devices.

**Defense in Depth** is a security approach that involves implementing multiple layers of security controls (physcial, technical, procedural) throughout an organization's IT infrastructure. This strategy ensures that if one layer is compromised, other layers can still provide protection.

**Security by Default** emphasises integrating security measures into systems and apps from the initial stages of development. By prioritising security from the outset, organisations can reduce vulnerabilities and establish a strong security foundation in their cloud environments.

---
**Security Posture** refers to the overall security status of a cloud environment. It indicates how well and organisation is prepared to defend against cyber attacks by evaluating their security controls, policies and practices. 

**Cyber Resilience** refers to an organization's ability to withstand and recover quickly from cyber attacks. It involves identifying, assessing, and mitigating risks, responding to incidents effectively, and recovering from disruptions quickly.

**Firewall** is a network device that regulates traffic based on predefined security rules. These rules help keep unauthorized people or harmful things away from important cloud resources, such as servers, databases, and applications by checking incoming and outgoing traffic, only allowing the ones that are safe and authorised.

**Encryption** is the process of converting data into unreadable format by using an encryption algorithm. **Decryption** is the process of using an encryption key to convert encrypted data back into its original, readable format.

3 essential aspects of security (CIA Triad):
- Confidentiality: Keeping information safe and secret and is protected from unauthorized access and disclosure. Encryption is a crucial method in ensuring confidentiality.
- Integrity: Ensuring that data is accurate, trustworthy, complete, and unaltered during storage and transmission. Controls such as checksums, digital signatures, and access controls are used to maintain data integrity.
- Availability: Ensuring that data and services are accessible to authorized users when needed. Cloud environments must be designed with redundancy, failover mechanisms, and disaster recovery plans to maintain high availability.

Control refers to the measures and processes implemented to manage and mitigate security risks. These measures help organizations manage and mitigate security risks associated with cloud-based systems.

Compliance relates to adhering to industry regulations, legal requirements, and organizational policies. It involves ensuring that security practices and measures align with established standards and guidelines.

By integrating these principles into a comprehensive cloud security model, organizations can establish a strong foundation for protecting their data, maintaining data integrity, and ensuring continuous access to critical resources.

### Cloud Security vs On-Premises Security
Traditionally, orgs heavily relied on their own on-premises infrastructure to manage and secure their data and applications. They had complete control over their hardware, software and network components. Cloud security differs from on-premises security in several ways:
- Location: Cloud security involves hosting and managing data and applications in off-site data centers operated by cloud service providers. The responsibility for securing the infrastructure and underlying hardware lies with the cloud provider. Whereas, trad on premises security involves hosting and managing data and apps locally on an orgs own servers and infrastructure, granting direct control and responsibility for securing physical and virtual environment.
- Responsibility: In a cloud model, the cloud service provider is responsible for securing the infrastructure, network, and physical facilities. The customer is typically responsible for securing their data, applications, user access, and configurations. For on-premises setup, the organization is responsible for securing the entire infrastructure, including hardware, network, operating systems, applications, and data.
- Scalability: This allows organizations to easily scale their resources up or down based on demand. This flexibility is suitable for dynamic workloads and rapid growth. In contrast, on-premises security requires organizations to provision and maintain their own infrastructure, which can be more time-consuming and costly when they scale up or down.
- Maintenance and updates: Cloud service providers handle infrastructure maintenance, including security updates, patching, and software upgrades. On-premises environments require organizations to maintain and update their own infrastructure, involving regular tasks such as patching, software updates, and hardware upgrades.
- CapEx vs OpEx: Cloud security follows an operational expenditure (OpEx) model, where organizations pay for the services they consume on a subscription basis. This eliminates the need for large upfront capital investments in physical security infrastructure. 

Organizations must carefully evaluate their requirements and consider factors such as data sensitivity, compliance regulations, and scalability to determine the most effective security strategy for their business.

### Cybersecurity
Cybersecurity refers to the practice of protecting computer systems, networks, and data from unauthorized access, theft, damage, or disruption. It involves implementing measures to prevent cyber attacks and mitigate their impact on individuals and organizations.

Examples of cybersecurity threats faced by orgs:
- Deceptive Social Engineering: Attackers use phising attacks to collect personal details about you to craft tailored attacks. E.g. an attacker may send a phishing email pretending to be from a trusted source, such as a bank or a colleague, to trick the recipient into revealing sensitive information or clicking on malicious links.
- Physical damage: Damage to hardware components, power disruptions or natural disasters or even theft can lead to data loss and service disruption.
- Malware, viruses, and ransomware: Malicious software can infect systems, steal data, disrupt operations or held hostage until a ransom is paid. E.g. ransomware attacks encrypt a victim's data and demand payment for the decryption key.
- Vulnearable 3rd party software: Attackers can exploit vulnerabilities in third-party software or libraries used by organizations to gain unauthorized access or compromise systems. E.g. a vulnerability in a widely used software library can be exploited by attackers to gain access to sensitive data or disrupt services.
- Configuration errors: Misconfigurations in cloud environments can lead to security vulnerabilities and potential sensitive data exposure. E.g. an organization may accidentally leave a storage bucket publicly accessible, allowing unauthorized users to access sensitive data. 

## Google's Trusted Infrastructure
### Data Centers
Google's data centers are designed to deliver exceptional reliabilty, security, efficiency and availability. Google is also commited to to mimising the environmental impact of data centers by using cutting edge technologies and renewable energy sources to reduce their ecological footprint.

The benefits of Google's data centers include:
- Zero-trust architecture: Google's data centers are built on a zero-trust security model, which means that all access to resources is continuously verified and authenticated, regardless of the user's location or device. This approach helps to prevent unauthorized access and protect sensitive data with features like tamper-evident hardware, secure boot processes, and strict access controls to only allow authorised personnel access minimising risk of physical breaches maintaining a privileged access framework.
- Efficiency: Purpose built servers are optimised for specific tasks allowing them to perform at high speed with great efficiency. This reduces energy consumption, operational costs and environmental impact. The Power Usage Effectiveness (PUE) score measures the energy efficiency of a data center, with a lower score indicating better efficiency. Google's data centers have an average PUE of 1.1, which is significantly better than the industry average of 1.67.
- Scalability: Data center can quickly and seamlessly accommodate new hardware and servers allowing easy scaling up of computing resources on demand. Allowing Google to handle massive data volumes and traffic without any disruptions to services.

### Secure Storage
Google Cloud automatically encrypts data even at rest (data stored on physical devices like computers, servers or disks). Cloud Key Management Service (Cloud KMS) allows users to manage encryption keys keys for their data. When data is in transit (moving between devices or over the internet), Google Cloud uses Transport Layer Security (TLS) to encrypt the data, ensuring that the authenticty, integrity and privacy of data is maintained during transmission.

Data is encrypted and authenticated at multiple network layers. Data in use refers to data being actively processed by a computer. Encrypting data in use adds another layer of protection, against unauthorised users who might physically access the computer. Memory encryption is used which locks your data inside the computer's memory, making it unreadable to anyone without the proper decryption keys. This helps protect sensitive data even if an attacker gains physical access to the machine.

Advanced Encryption Standard (AES) is a widely used encryption algorithm that provides strong security for data. Google Cloud uses AES-256, which is a variant of AES that uses a 256-bit key length, providing a high level of security for data encryption

### Identity
- Authentication: Serves as the gatekeeper by verifying the identify of users or systems that seek access. Google Cloud supports various authentication methods, including passwords, physical tokens, biometric data and multi-factor (two-step) authentication (MFA). This ensures that only authorized users can access resources and data.
- Authorisation: Is the access control mechanism but granting different levels of permissions to individuals or groups based on their roles, reponsibilities and organisation hierarchy.
- Auditing: By collecting and analysing logs of user activity, system events helps organisation detect anomalies, security breaches and policy violations.

**Identity Access Management (IAM)** - With IAM, you can create and manage user accounts, assign roles to users, grant and revoke permissions. 

### Network Security
**Zero Trust Networks** - With Google Cloud's BeyondCorp Enterprise, orgs can implement a zero trsut security model, where every access request is verified through user identity, device health and context before granting access to resources. 

**Secure connections to on-prem and multi-cloud environments** - Cloud VPN and Cloud Interconnect provide private access methods to establish secure connections between on-prem and Google Cloud resources. 

**Protect perimeter** - Google Cloud offers firewalls and Virtual Private Cloud (VPC) Service Controls to divide cloud into secure zones and control traffic between them. Shared VPC acts as a large fence that separates Google Cloud Project. 

**Web application firewall** - Google Cloud Armor protects against DDos (Distributed Denial of Service) attacks and other web-based threats by filtering and blocking malicious flood of malicious traffic before it reaches applications to prevent denial of service to legitimate users.

**Automate infrastructure** - by adopting tools like Terraform, Jenkins and Cloud Build, you create an immutable infrastructure ensuring a secure and reliable cloud environment. This approach allows you to define and manage your infrastructure as code, making it easier to maintain consistency, track changes, and quickly recover from any issues that may arise. By automating the provisioning and configuration of your infrastructure, you can reduce the risk of human error and ensure that your cloud environment remains secure and compliant with industry standards.

### Cloud Armour
Google Cloud Armour is a security service that protects applications and services from various types of cyber threats, including Distributed Denial of Service (DDoS) attacks, web application attacks, and other malicious traffic. It provides a set of security features and capabilities to help organizations safeguard their applications and maintain availability for legitimate users.


### Security Operations
SecOps protects your organisation's data and systems in the cloud by reducing the risk of data breaches, system outages and other security incidents. 
- Vulnerability management: Regularly scanning for vulnerabilities in your cloud environment and applying patches and updates to address them. This helps to prevent attackers from exploiting known weaknesses in your systems. Google Cloud's Security Command Center (SCC) provides an overview of your security posture. 
- Log management: Cloud Logging collects and analyses security logs from entire Google Cloud environment, allowing you to monitor and investigate security events. 
- Incident response: Expert incident responders can tackle security incidents quickly with equipped tools
- Education: Train employees on security best practices. 

Benfits:
- Reduced risk of data breaches
- Increased uptime minimises impact of outages
- Improved compliance such as General Data Protection Regulation (GDPR)
- Enhanced employee productivity

### Google Cloud's Trust Principles and Compliance
**Google Cloud's Trust Principles**
- You own your data not Google: You have control over access,export, delete and permissions
- Google does not sell customer data to 3rd parties: Data is safegaurded from advertising and marketing purposes
- Google does not use customer data for advertising: Data is not used to target ads or create user profiles as it is confidential
- All customer data is encrypted
- No insider access to your data: Prevents unauthorised employee access to customer data
- No backdoor access: Google does not create backdoors for law enforcement or government agencies to access customer data
- Google privacy policies are audited against international standards: Transparency Reports and Independent Audits Transparency provide valuable insights and accountability regarding the privacy, security and access to info. Google participates in EU Cloud Code of Conduct to further demonstrate accountability, compliance support and robust data protection practices.

**Data sovereignty** - refers to the legal concept that data is subject to laws and regulations of the country it resides. General Data Protection Regulation (GDPR) in the European UNion requires companies to comply with data protection laws when processing or storing personal data of EU citizens.
**Data residency** - refers to the physical location where data is stored and processed. It is important for compliance and legal reasons, as different jurisdictions may have varying data protection laws and regulations.

Google Cloud allows you to:
- Choose the physical location of data through regions: Ensuring data is only stored within the selected region as in Service Specific Terms. Google cloud provides Organisation Policy constraints coupled with IAM configuration to prevent accidental data storage in wrong region.
- Virtual Private Cloud (VPC) Service Controls: Lets you restrict network access to data. Limits user access through IP address filtering. 
- Google CLoud Armor lets you restrict traffic locations for your external load balancer by adding an extra layer of protection. 

**Google Cloud compliance resource center** is a hub for info on certifications and compliance standards. You can find mappings of Google CLoud's security, privacy and compliance controls to global standards. Also offers documentation on regional and sector specific regulations. 

**Compliance Reports Manager** is a powerful tool which offers easy, on-demand access to critical compliance resources at no extra cost. Within the Compliance Reports Manager, you'll discover our latest ISO/IEC certificates, SOC reports and self-assessments. These resources provide evidence of our adherence to rigorous compliance standards and help streamline your own reporting and compliance efforts.

**Confidential Computing** allows you to protect data while it being processed. Ensures data soverignty because data is encrypted and Google cannot access it. 