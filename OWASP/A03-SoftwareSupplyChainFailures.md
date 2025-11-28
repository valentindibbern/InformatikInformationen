# Software Supply Chain Failures

### Overview:
This was top-ranked in the Top 1 0 community survey With exactly 50% respondents ranking it #1. Since initially appearing in the 2013 Top 10 as "A9 — Using Components With Known Vulnerabilities", the risk has grown in scope to include all supply chain failures, not just ones involving known vulnerabilities. Despite this increased scope, supply chain failures continue to be a challenge to identify With only 11 Common Vulnerability and Exposures (CVEs) having the related CWEs. However, when tested and reported in the contributed data, this category has the highest average incidence rate at 5.19%. The relevant CWEs are CWE-477: Use of Obsolete Function, CWE-1104: Use of Unmaintained Third Party Components, CWE-1329: Reliance on Component That is Not Updateable, and CWE-1395: Dependency on Vulnerable Third-Party Component.
### Description:
Software supply chain failures are breakdowns or other compromises in the process of building, distributing, or updating software. They are often caused by vulnerabilities or malicious changes in third-party code, tools, or other dependencies that the system relies on.
You are likely vulnerable if:
- If you do not carefully track the versions of all components that you use (both client-side and server-side). This includes components you directly use as well as nested (transitive) dependencies.
- If the software is vulnerable, unsupported, or out of date. This includes the OS, web/application server, database management system (DBMS), applications, APIs and all components, runtime environments, and libraries.
- If you do not scan for vulnerabilities regularly and subscribe to security bulletins related to the components you use.
- If you do not have a change management process or tracking of changes within your supply chain, including tracking IDEs, IDE extensions and updates, changes to your organization’s code repository, sandboxes, image and library repositories, the way artifacts are created and stored, etc. Every part of your supply chain should be documented, especially changes.
- If you have not hardened every part of your supply chain, with a special focus on access control and the application of least privilege.
- If your supply chain systems do not have any separation of duty. No single person should be able to write code and promote it all the way to production without oversight from another human being.
- If developers, DevOps, or infrastructure professionals are allowed to download and use components from untrusted sources, for use in production.
- If you do not fix or upgrade the underlying platform, frameworks, and dependencies in a risk-based, timely fashion. This commonly happens in environments when patching is a monthly or quarterly task under change control, leaving organizations open to days or months of unnecessary exposure before fixing vulnerabilities.
- If software developers do not test the compatibility of updated, upgraded, or patched libraries.
- If you do not secure the configurations of every part of your system (see [A02:2025-Security Misconfiguration](https://owasp.org/Top10/A05_2021-Security_Misconfiguration/)).
- If you have a complex CI/CD pipeline that uses many components but has weaker security than the rest of your application.
### How to Prevent:
There should be a patch management process in place to:
- Know your Software Bill of Materials (SBOM) of your entire software and manage the SBOM-dictionary centrally.
- Track not just your own dependencies, but their (transitive) dependencies, and so on.
- Remove unused dependencies, unnecessary features, components, files, and documentation. Attack surface reduction.
- Continuously inventory the versions of both client-side and server-side components (e.g., frameworks, libraries) and their dependencies using tools like versions, OWASP Dependency Check, retire.js, etc.
- Continuously monitor sources like Common Vulnerability and Exposures (CVE) and National Vulnerability Database (NVD) for vulnerabilities in the components you use. Use software composition analysis, software supply chain, or security-focused SBOM tools to automate the process. Subscribe to email alerts for security vulnerabilities related to components you use.
- Only obtain components from official (trusted) sources over secure links. Prefer signed packages to reduce the chance of including a modified, malicious component (see [A08:2025-Software and Data Integrity Failures](https://owasp.org/Top10/A08_2021-Software_and_Data_Integrity_Failures/)).
- Deliberately choosing which version of a dependency you use and upgrading only when there is need.
- Monitor for libraries and components that are unmaintained or do not create security patches for older versions. If patching is not possible, consider deploying a virtual patch to monitor, detect, or protect against the discovered issue.
- Update your CI/CD, IDE, and any other developer tooling regularly
- Treat components in your CI/CD pipeline as part of this process; harden them, monitor them, and document changes accordingly
There should be a change management process or tracking system in place to track changes to: * Your CI/CD settings (all build tools and pipeline) * Your code repository * Sandbox areas * Developer IDEs * Your SBOM tooling, and created artifacts * Your logging systems and logs * Third party integrations, such as SaaS * Artifact repository * Container registry
Harden the following systems, which includes enabling MFA and locking down IAM: * Your code repository (which includes not checking in secrets, protecting branches, backups) * Developer workstations (regular patching, MFA, monitoring, and more) * Your build server & CI/CD (separation of duties, access control, signed builds, environment-scoped secrets, tamper-evident logs, more) * Your artifacts (ensure integrity via providence, signing, and time stamping, promote artifacts rather than rebuilding for each environment, ensure builds are immutable) * Infrastructure as code is managed like all code, including use of PRs and version control
Every organization must ensure an ongoing plan for monitoring, triaging, and applying updates or configuration changes for the lifetime of the application or portfolio.
## EShop Lösungen
1. Überprüfung der NuGet-Abhängigkeiten (ASP.NET Core & API)
	- 
2. Absicherung der Docker-Container (App & SQL-Datenbank)
	- Nur offizielle und vertrauenswürdige MS Images
3. Transparenz durch SBOM (Software Bill of Materials)
	- SBOM für jeden Build automatisch generieren
4. Schutz der Build-Pipeline (CI/CD)
	- Minimalrechte: Der Build-Agent (Aufgaben wie Kompilieren, Testen und Verpacken) sollte nur die Rechte, die er wirklich braucht.
	- Branch Protection: Nimand darf direkt auf *main*/*master* pushen. Code muss per Pull-Request und Review freigegeben werden.