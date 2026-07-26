 # OWASP Top 10 — First Impressions

  **Date:** 2025-07-26
  **Type:** Notes
  **Status:** Beginner — terminology is still new to me.

  ## What is the OWASP Top 10?

  It is a list of the most common and impactful security risks in web applications. It does not cover every vulnerability, but it tells developers and security reviewers where to focus first.

  ## The ten categories

  1. **Broken Access Control** — Users can do things they should not be allowed todo, like accessing another user's data.
  2. **Cryptographic Failures** — Sensitive data is not protected properly, e.g., weak encryption or exposed secrets.
  3. **Injection** — Untrusted user input is passed into an interpreter, like SQL or a command shell.                                                                                                      
  4. **Insecure Design** — The application was not built with security in mind from the start.                                                                                                             
  5. **Security Misconfiguration** — Default passwords, unnecessary features, or exposed debug info.                                                                                                       
  6. **Vulnerable and Outdated Components** — Using libraries with known security flaws.                                                                                                                   
  7. **Identification and Authentication Failures** — Weak login, session, or password handling.                                                                                                           
  8. **Software and Data Integrity Failures** — Untrusted updates or unsafe deserialization.                                                                                                               
  9. **Security Logging and Monitoring Failures** — Missing logs makes it hard to detect or respond to attacks.                                                                                            
  10. **Server-Side Request Forgery (SSRF)** — The server can be tricked into making requests it should not.                                                                                               
                                                                                                                                                                                                           
  ## What I still need to learn

  - What each category looks like in real Python code
  - How to spot each one during a code review
  - The difference between authentication and authorization in practice

  ## Next step

  I will focus on **Injection** first, starting with SQL injection, because I can reproduce it quickly in a small Python/Flask app.
