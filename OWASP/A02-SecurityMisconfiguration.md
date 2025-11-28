# Security Misconfiguration
### Overview:
Moving up from #5 in the previous edition, 100% of the applications tested were found to have some form of misconfiguration, With an average incidence rate of 3.0096, and over 719k occurrences of a Common Weakness Enumeration (CWE) in this risk category. With more shifts into highly configurable software, itls not surprising to see this category moving up. Notable CWEs included are CWE-16 Configuration and CWE-611 Improper Restriction of XML External Entity
Reference (XXE).
### Description:
Security misconfiguration is when a system, application, or cloud service is set up incorrectly from a security perspective, creating vulnerabilities.
The application might be vulnerable if:
- It is missing appropriate security hardening across any part of the application stack or improperly configured permissions on cloud services.
- Unnecessary features are enabled or installed (e.g., unnecessary ports, services, pages, accounts, testing frameworks, or privileges).
- Default accounts and their passwords are still enabled and unchanged.
- A lack of central configuration for intercepting excessive error messages. Error handling reveals stack traces or other overly informative error messages to users.
- For upgraded systems, the latest security features are disabled or not configured securely.
- Excessive prioritization of backward compatibility leading to insecure configuration.
- The security settings in the application servers, application frameworks (e.g., Struts, Spring, ASP.NET), libraries, databases, etc., are not set to secure values.
- The server does not send security headers or directives, or they are not set to secure values.
Without a concerted, repeatable application security configuration hardening process, systems are at a higher risk.
### How to Prevent:
Secure installation processes should be implemented, including:
- A repeatable hardening process enabling the fast and easy deployment of another environment that is appropriately locked down. Development, QA, and production environments should all be configured identically, with different credentials used in each environment. This process should be automated to minimize the effort required to set up a new secure environment.
- A minimal platform without any unnecessary features, components, documentation, or samples. Remove or do not install unused features and frameworks.
- A task to review and update the configurations appropriate to all security notes, updates, and patches as part of the patch management process (see [A03:2025-](https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/)Software Supply Chain Failures). Review cloud storage permissions (e.g., S3 bucket permissions).
- A segmented application architecture provides effective and secure separation between components or tenants, with segmentation, containerization, or cloud security groups (ACLs).
- Sending security directives to clients, e.g., Security Headers.
- An automated process to verify the effectiveness of the configurations and settings in all environments.
- Proactively add a central configuration to intercept excessive error messages as a backup.
- If these varifications are not automated, they should be manually verified annually at a minimum.
## EShop Probleme
## EShop Lösungen
- Applikationsweite Fehlerhandhabung
- Defenition of Done anpassen:
	- Alles ausser dem was in requirements.txt festgelegt ist deinstallieren.
	- Debugmode abstellen
	- Keine Default-Passwörter, Überprüfungen