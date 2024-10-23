# Cloud-Infrastructure-Security-Incident-Response-and-Remediation
1. Project Title:
Cloud Infrastructure Security Incident Response and Remediation
________________________________________
2. Project Description:
This project demonstrates my role as a junior cloud security analyst during a critical security incident involving a large retail company. The company suffered a major breach, resulting in unauthorized access to sensitive customer data, including credit card information. The incident impacted multiple systems, including virtual machines, cloud storage buckets, and firewalls.
In this project, I identified and remediated the vulnerabilities that led to the breach. I implemented solutions such as shutting down compromised virtual machines, securing cloud storage, fixing misconfigured firewalls, and verifying compliance with PCI DSS 3.2.1 standards. This project showcases my technical problem-solving abilities, attention to detail, and adaptability to new security challenges. It also highlights my transferable skills in managing cloud infrastructure security and ensuring compliance with industry standards.
This project showcases my practical skills in cloud security, vulnerability remediation, and compliance verification. All steps are documented with detailed screenshots for a clear understanding of the process and technical solutions applied.
Through my efforts, I was able to support the security team in containing the breach and restoring the company's systems. This project demonstrates my ability to analyse security incidents, implement cloud security best practices, and ensure compliance with regulatory standards. Regular security audits and ongoing monitoring were recommended to maintain the environment's security posture and prevent future breaches.
Key Take Aways:

•	By systematically identifying, analysing, and prioritizing vulnerabilities, I was able to develop a clear remediation plan to restore system security.
•	While I primarily focused on cloud security, this project demonstrated my ability to quickly adapt and apply new skills to meet the challenge, such as configuring firewalls and securing cloud storage.
•	I ensured compliance with PCI DSS standards while addressing both technical vulnerabilities and broader security policies.
•	Although this project was an individual task, I understand the importance of working closely with the broader security team during incidents to share findings, validate remediation steps, and ensure system integrity.

3. Business Understanding:
KZM Retail, a global retail powerhouse with 170 physical stores and an extensive online platform, suffered a major data breach that compromised sensitive customer information, including credit card data. The company processes thousands of transactions daily, which means the security of its cloud environment is critical to maintaining customer trust and complying with legal regulations like PCI DSS.
The business problem addressed in this project was to mitigate the security risks in KZM Retail’s cloud infrastructure after the breach. The primary stakeholders included the security team, customers whose data was compromised, and senior management overseeing risk management and compliance. Failing to secure the cloud infrastructure could have led to severe financial losses, reputational damage, and legal repercussions.
The key goal was to quickly identify vulnerabilities, contain the breach, remediate compromised systems, and ensure that the company's cloud environment met compliance standards moving forward. This required not only technical solutions but also aligning with business objectives, such as maintaining customer trust and ensuring that the company could continue operating without further risk.
__________________________________________________
4. Tools and Frameworks:
Tools Used:
1.	Google Cloud Security Command Center: Used for identifying and analysing active vulnerabilities across various cloud resources (VMs, Cloud Storage, and Firewalls).
o	Key Learning: Gained hands-on experience in managing security incidents using a cloud-native security platform, including the ability to prioritize critical vulnerabilities.
2.	Google Cloud Compute Engine: Used to reconfigure and secure virtual machines after identifying the compromised VM.
o	Key Learning: Learned how to effectively manage VMs, including snapshot recovery, enabling Secure Boot, and controlling network access through firewall rules.
3.	Google Cloud Storage: This tool was used to secure the company’s cloud storage bucket by revoking public access and enabling uniform bucket-level access control.
o	Key Learning: Enhanced knowledge of managing bucket permissions and controlling public access to prevent data exfiltration.
4.	Google Cloud VPC (Virtual Private Cloud): Utilized to configure and update firewall rules to restrict access to sensitive ports (SSH and RDP) and enable firewall logging.
o	Key Learning: Learned how to implement secure and granular firewall rules to protect cloud resources and enable logging for enhanced network visibility.
Frameworks Followed:
•	Payment Card Industry Data Security Standard (PCI DSS 3.2.1): As a company handling credit card transactions, KZM Retail is required to comply with PCI DSS. All remediation efforts were designed to align with this framework, ensuring that the company's cloud infrastructure met industry standards for protecting cardholder data.
o	Key Learning: Gained experience in applying PCI DSS requirements to real-world security incidents, focusing on network segmentation, encryption, and audit logging.
__________________________________________________

3.Project Body
Cloud Infrastructure Security Incident Response and Remediation
As a junior cloud security analyst, I had the opportunity to work on a significant data breach incident for a large retail company. The incident affected multiple systems, including virtual machines, cloud storage, and network firewalls, leading to unauthorized access to sensitive customer data. Below is a detailed walkthrough of my thought process, problem-solving approach, and the technical solutions I implemented.
________________________________________
Incident Overview:
The company suffered a data breach where attackers gained unauthorized access to sensitive information, including credit card data and personal details. This breach involved compromised VMs, exposed storage buckets, and misconfigured firewalls. My task was to analyse the vulnerabilities, contain the breach, implement remediation actions, and verify compliance with the Payment Card Industry Data Security Standard (PCI DSS) 3.2.1 framework.
________________________________________
Steps Undertaken and Technical Solutions:
Step 1: Analysing the Data Breach
•	Objective: Identify the root cause of the breach and prioritize remediation.
•	Approach:
1.	Security Command Center: I began by reviewing the active vulnerabilities across multiple resources (Compute Engine, Cloud Storage, and Firewall) listed in the Google Cloud Security Command Center. This helped me understand which components were exposed and how attackers gained unauthorized access. By filtering the findings based on resource types such as Compute Engine virtual machine (VM), Cloud Storage bucket, and firewall, I identified several critical vulnerabilities.
	Key Findings: High-severity issues such as open SSH/RDP ports, public access to storage buckets, and insecure VMs were identified.
	Screenshots: Provided to highlight active vulnerabilities.
2.	PCI DSS Compliance Report: I examined the PCI DSS 3.2.1 compliance findings to ensure the company’s environment met the required security standards. The report flagged non-compliant firewall rules and unencrypted public storage buckets.
	Key Findings: Non-compliant firewall rules, public VM IPs, and open RDP/SSH ports
	Key Takeaway: These insights helped shape my strategy for securing the network and storage systems.
	Screenshots: PCI DSS report with non-compliant rules.
Step 2: Fixing Compute Engine Vulnerabilities
•	Objective: Restore system integrity by eliminating compromised virtual machines and ensuring secure configurations.
•	Technical Fixes: I identified the compromised VM cc-app-01 and followed the remediation steps:
1.	Shutting Down Compromised VM (cc-app-01): I shut down the VM to prevent further exploitation, ensuring no new malicious activities could occur.
	Technical Detail: The VM had public IP access, disabled Secure Boot, and was using a default service account with full API access.
	Screenshot: VM shutdown process.
2.	Creating a New VM (cc-app-02) from Snapshot: Using a snapshot taken before the malware infection, I created a new VM with enhanced security settings:
	Public IP Disabled: To prevent external access.
	Secure Boot Enabled: Ensuring that only authorized code could be loaded.
	Controlled Firewall Tags: Applied to limit access to SSH only from authorized networks.
	Screenshot: New VM configuration.
3.	Deleting the Compromised VM: I deleted cc-app-01 to ensure the infected machine was permanently removed.
	Screenshot: VM deletion confirmation.
Step 3: Securing Cloud Storage Bucket Permissions
•	Objective: Eliminate unauthorized access to the company’s sensitive data stored in the cloud. The Cloud Storage bucket was publicly accessible, which posed a major data exposure risk.
•	Technical Fixes:
1.	Revoking Public Access: I revoked public access to the storage bucket- disabled the public access control list (ACL)-, addressing a high-severity vulnerability that allowed anyone on the internet to view the stored files.
	Technical Detail: Enabled uniform bucket-level access control to enforce a single set of permissions for both the bucket and its objects.
	Screenshot: Bucket permissions before and after revoking public access.
2.	Removing User Permissions: I removed all user permissions (e.g., allUsers and allAuthenticatedUsers) to prevent unauthorized access.
	Key Outcome: This step effectively sealed off public access, drastically reducing the risk of data exposure.
	Screenshot: Updated permission settings.
Step 4: Limiting Firewall Port Access
•	Objective: Reduce the attack surface by restricting access to critical ports (SSH and RDP). The firewall was configured to allow unrestricted access via RDP and SSH from the internet, exposing the network to unauthorized access.
•	Technical Fixes:
1.	Creating a Limited Firewall Rule: I created a new firewall rule to restrict SSH access (TCP port 22) only to authorized IP addresses (Google Cloud’s IAP range), significantly reducing the risk of unauthorized external access.
	Technical Detail: Specified target tags to ensure that only machines tagged with "cc" could be accessed via SSH.
	Screenshot: New firewall rule configuration.
2.	Deleting Overly Permissive Firewall Rules: I removed the default rules that allowed unrestricted access to ICMP, RDP, and SSH ports from any source. This greatly reduced the attack surface for the compromised network.
	Screenshot: Deletion of default firewall rules.
Step 5: Fixing Firewall Configuration
•	Objective: Improve network visibility by enabling logging for firewall rules. Several broad firewall rules were allowing unauthorized access to the network, contributing to the breach.
•	Technical Fixes:
1.	Deleting Overly Permissive Rules: I removed firewall rules that allowed open access to ICMP, RDP, and SSH ports from any source.
	Screenshot: Deletion of default-allow-icmp, default-allow-rdp, and default-allow-ssh rules.
2.	Enabling Logging for New Firewall Rules: I enabled logging for the remaining firewall rules, ensuring that all traffic allowed or denied could be audited for future investigation.
	Key Outcome: 
•	Customized firewall rules for controlled traffic.
•	Enabled logging for better network visibility allowing the team to monitor access attempts and potential threats.
	Screenshot: Firewall rule logging enabled.
________________________________________
Step 6: Verifying Compliance
•	Objective: Ensure the environment meets PCI DSS 3.2.1 compliance standards after remediation.
•	Approach:
1.	Re-running PCI DSS Compliance Report: I confirmed that the high and medium severity vulnerabilities identified earlier were successfully remediated, with only lab-specific issues remaining.
	Key Insight: This demonstrated the effectiveness of the remediation efforts.
	Screenshot: PCI DSS report post-remediation.
________________________________________

Conclusion:
The Security Incident Response and Remediation project was a success in terms of restoring the integrity and security of KZM Retail's cloud infrastructure. By identifying and remediating critical vulnerabilities such as open SSH/RDP ports, public storage access, and insecure VM configurations, we were able to halt the attack, prevent further data exfiltration, and bring the company back into compliance with PCI DSS standards.
Some of the project successes include:
•	Containment and Eradication: Quickly shutting down compromised VMs, fixing cloud storage bucket permissions, and tightening firewall rules successfully contained the breach and eradicated the attacker’s access.
•	Compliance Restoration: All critical vulnerabilities were resolved, restoring the company's compliance with PCI DSS.
•	Enhanced Security Posture: The organization’s cloud environment was left more secure with controlled access to sensitive resources, active logging, and monitoring for real-time threat detection.
Future Steps:
•	Automated Security Audits: Implement automated tools to regularly audit cloud configurations, firewall rules, and access logs to ensure security settings remain compliant and up to date.
•	Continuous Monitoring: Establish a continuous monitoring system to track access attempts and potential vulnerabilities in real-time, ensuring that future attacks can be detected and mitigated quickly.
•	Training and Awareness: Provide ongoing training to the security team to ensure that they are up to date with the latest security threats and best practices for incident response.
Recommendations for Future Projects:
1.	Proactive Threat Detection: Implement machine learning-driven threat detection systems to identify suspicious behaviour before an actual breach occurs.
2.	Enhanced Data Encryption: Ensure all sensitive data is encrypted at rest and in transit, so that even if data is exfiltrated, it cannot be exploited.
3.	Least Privilege Access: Continue to enforce the principle of least privilege to minimize the attack surface by ensuring that users and services have only the necessary permissions required for their functions.
By focusing on these steps, KZM Retail can significantly reduce the risk of future breaches and continue to protect their business operations and customer data.


