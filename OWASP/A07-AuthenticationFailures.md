# Authentication Failures
## Overview:
Authentication Failures maintains its position at #7 With a slight name change to more accurately reflect the 36 CWEs in this category. Despite benefits from standardized frameworks, this category has kept its #7 rank from 2021. Notable CWEs included are CWE-259 Use of Hard-coded Password, CWE-297: Improper Validation of Certificate With Host Mismatch, CWE-287: Improper Authentication, CWE-384: Session Fixation, and CWE-798 Use of Hard-coded Credentials.
## Description:
When an attacker is able to trick a system into recognizing an invalid or incorrect user as legitimate, this vulnerability is present. There may be authentication weaknesses if the application it:
- Permits automated attacks such as credential stuffing, where the attacker has a breached list of valid usernames and passwords. More recently this type of attack has been expanded to include hybrid password attacks credential stuffing (also known as password spray attacks), where the attacker uses variations or increments of spilled credentials to gain access, for instance trying Password1!, Password2!, Password3! and so on. 
- Permits brute force or other automated, scripted attacks that are not quickly blocked.
- Permits default, weak, or well-known passwords, such as "Password1" or "admin" username with an "admin" password.
- Allows users to create new accounts with already known-breached credentials.
- Allows use of weak or ineffective credential recovery and forgot-password processes, such as "knowledge-based answers," which cannot be made safe.
- Uses plain text, encrypted, or weakly hashed passwords data stores (see [A02:2021-Cryptographic Failures](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/)).
- Has missing or ineffective multi-factor authentication.
- Allows use of weak or ineffective fallbacks if multi-factor authentication is not available.
- Exposes session identifier in the URL, a hidden field, or another insecure location that is accessible to the client.
- Reuses the same session identifier after successful login.
- Does not correctly invalidate user sessions or authentication tokens (mainly single sign-on (SSO) tokens) during logout or a period of inactivity.
## How to Prevent:
- Where possible, implement and enforce use of multi-factor authentication to prevent automated credential stuffing, brute force, and stolen credential reuse attacks.
- Where possible, encourage and enable the use of password managers, to help users make better choices.
- Do not ship or deploy with any default credentials, particularly for admin users.
- Implement weak password checks, such as testing new or changed passwords against the top 10,000 worst passwords list.
- During new account creation and password changes validate against lists of known breached credentials (eg: using [haveibeenpwned.com](https://haveibeenpwned.com)).
- Align password length, complexity, and rotation policies with [National Institute of Standards and Technology (NIST) 800-63b's guidelines in section 5.1.1](https://pages.nist.gov/800-63-3/sp800-63b.html#:~:text=5.1.1%20Memorized%20Secrets) for Memorized Secrets or other modern, evidence-based password policies.
- Do not force human beings to rotate passwords unless you suspect breach. If you suspect breach, force password resets immediately.
- Ensure registration, credential recovery, and API pathways are hardened against account enumeration attacks by using the same messages for all outcomes (“Invalid username or password.”).
- Limit or increasingly delay failed login attempts but be careful not to create a denial of service scenario. Log all failures and alert administrators when credential stuffing, brute force, or other attacks are detected or suspected.
- Use a server-side, secure, built-in session manager that generates a new random session ID with high entropy after login. Session identifiers should not be in the URL, be securely stored in a secure cookie, and invalidated after logout, idle, and absolute timeouts.
- Ideally, use a premade, well-trusted system to handle authentication, identity, and session management. Transfer this risk whenever possible by buying and utilizing a hardened and well tested system.
## EShop Probleme
## EShop Lösungen
1. Logging und Monitoring