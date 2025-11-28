# Injection
## Overview:
Injection falls two spots from #3 to #5 in the ranking, maintaining its position relative to A04:2025-Cryptographic Failures and A06:2025-lnsecure Design. Injection is one of the most tested categories With 100% of applications tested for some form of injection. lt had the greatest number of CVEs for any category, With 37 CWEs in this category. Injection includes Cross-site Scripting (high frequency/low impact) With more than 30k CVEs and SQL Injection (Iow frequency/high impact) With more than 14k CVEs. The massive number of reported CVEs for CWE-79 Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting') brings down the average weighted impact of this category.
## Description:
An injection vulnerability is a system flaw that allows an attacker to insert malicious code or commands (such as SQL or shell code) into a program’s input fields, tricking the system into executing the code or commands as if it were part of the system. This can lead to truly dire consequences.
An application is vulnerable to attack when:
- User-supplied data is not validated, filtered, or sanitized by the application.
- Dynamic queries or non-parameterized calls without context-aware escaping are used directly in the interpreter.
- Unsanitized data is used within object-relational mapping (ORM) search parameters to extract additional, sensitive records.
- Potentially hostile data is directly used or concatenated. The SQL or command contains the structure and malicious data in dynamic queries, commands, or stored procedures.
Some of the more common injections are SQL, NoSQL, OS command, Object Relational Mapping (ORM), LDAP, and Expression Language (EL) or Object Graph Navigation Library (OGNL) injection. The concept is identical among all interpreters. Detection is best achieved by a combinatino of source code review along with automated testing (including fuzzing) of all parameters, headers, URL, cookies, JSON, SOAP, and XML data inputs. The addition of static (SAST), dynamic (DAST), and interactive (IAST) application security testing tools into the CI/CD pipeline can also be helpful to identify injection flaws before production deployment.
A related class of injection vulnerabilities has become common in LLMs. These are discussed separately in the [OWASP LLM Top 10](https://genai.owasp.org/llm-top-10/), specifically [LLM01:2025 Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/).
## How to Prevent:
The best means to prevent injection requires keeping data separate from commands and queries:
- The preferred option is to use a safe API, which avoids using the interpreter entirely, provides a parameterized interface, or migrates to Object Relational Mapping Tools (ORMs). **Note:** Even when parameterized, stored procedures can still introduce SQL injection if PL/SQL or T-SQL concatenates queries and data or executes hostile data with EXECUTE IMMEDIATE or exec().
When it is not possible to separate the data from commands, you can reduce threats using the following techniques.
- Use positive server-side input validation. This is not a complete defense as many applications require special characters, such as text areas or APIs for mobile applications.
- For any residual dynamic queries, escape special characters using the specific escape syntax for that interpreter. **Note:** SQL structures such as table names, column names, and so on cannot be escaped, and thus user-supplied structure names are dangerous. This is a common issue in report-writing software.
**Warning:** These techniques involve parsing and escaping complex strings, making them error-prone and not robust in the face of minor changes to the underlying system.
## EShop Probleme
## EShop Lösungen