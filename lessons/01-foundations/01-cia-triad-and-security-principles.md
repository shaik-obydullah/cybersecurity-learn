# Lesson 1: CIA Triad & Security Principles

*For: Shaik Obydullah | Focus: Building on Full-Stack Development Background*

## Learning Objectives

By the end of this lesson, you should be able to:
- Explain the CIA Triad (Confidentiality, Integrity, Availability) and apply it to web applications
- Understand common security principles (Least Privilege, Defense in Depth, Fail Securely)
- Identify real-world security issues in Laravel/WordPress applications
- Apply a security mindset to your existing ERP/MIS projects

## 1. The CIA Triad

The CIA Triad is the foundation of information security. As a full-stack developer building ERPs and MIS systems, you already deal with these concepts daily.

| Principle | Definition | Web App Example | How You Can Apply |
|---|---|---|---|
| **Confidentiality** | Ensuring only authorized users can access sensitive data | Customer PII, salary data, migration records in BRAC MIS | Use proper authentication, encryption (TLS/HTTPS), role-based access control |
| **Integrity** | Ensuring data is accurate and hasn't been tampered with | Financial transactions in ERP, invoice totals, inventory counts | Use CSRF protection, input validation, audit trails, database constraints |
| **Availability** | Ensuring systems are accessible when needed | Restaurant POS during peak hours, ISP billing system uptime | Rate limiting, backups, DDoS mitigation, proper error handling, caching |

## 2. Core Security Principles

| Principle | Explanation | Laravel/WordPress Application |
|---|---|---|
| **Least Privilege (PoLP)** | Users/processes should only have minimum permissions needed | In Laravel, use Policies/Gates properly. Don't give admin role to all users. In WordPress, use appropriate user roles/capabilities. |
| **Defense in Depth** | Multiple layers of security (no single point of failure) | Combine auth, validation, HTTPS, WAF, rate limiting, RBAC. Like securing your ERP with multiple controls. |
| **Fail Securely** | If something fails, it should fail in a secure state | Don't expose stack traces in production. Return generic errors. Handle auth failures without leaking info. |
| **Separation of Duties** | No single person should have control over all critical functions | In your ERP, separate cashier, manager, and admin permissions. Different roles for different operations. |
| **Secure by Default** | Systems should be secure out of the box | Laravel's default protections (CSRF, password hashing with bcrypt/Argon2) - use them! Don't disable security features. |
| **Economy of Mechanism** | Keep security simple and easy to understand | Avoid overcomplicating auth. Simple, well-tested Laravel auth is better than custom complex solutions. |

## 3. Connecting to Your Experience

Looking at your projects, here are security considerations:

- **ERP System**: Multi-vendor marketplace needs strong tenant isolation. Ensure vendors can only access their own data (authorization). Watch for IDOR vulnerabilities.
- **BRAC MIS**: Handles sensitive migrant worker data. Requires strict RBAC, audit logging (you have this!), and data encryption. Critical for confidentiality.
- **Restaurant POS Lite**: Financial transactions require integrity. Ensure order totals can't be manipulated, implement proper permissions.
- **Ollama AI Integration**: New attack surface - prompt injection, data leakage. Needs careful input sanitization.

## 4. Hands-On Exercise

**Task 1: Security Audit Mindset**
Pick one of your Laravel projects. Review a route/controller and ask:
1. Does this endpoint check authentication?
2. Does it check authorization (can this user access this resource)?
3. Is input validated?
4. Could a user access another user's data by changing IDs in URL?

**Task 2: Map CIA to a Feature**
Take "Create Invoice" in your ERP/POS:
- **Confidentiality:** Who can see invoices?
- **Integrity:** Can invoice amounts be tampered with?
- **Availability:** What if database goes down during checkout?

**Task 3: Identify Violations**
Look for these anti-patterns in your code:
- Using `find($id)` without checking ownership
- Exposing user IDs in URLs without authorization checks
- Returning all model data including hidden fields
- Trusting client-side validation only

## 5. Resources

- [OWASP - Security Fundamentals](https://owasp.org/www-community/controls/)
- [CISA - Cybersecurity Basics](https://www.cisa.gov/resources-tools/resources/cybersecurity-basics)
- [PortSwigger - Access Control](https://portswigger.net/web-security/access-control) (You'll revisit this later)
- [Laravel Security Best Practices](https://laravel.com/docs/security)

## Next Lesson

**Lesson 2:** Networking Basics for Web Application Security - HTTP, HTTPS, Headers, and how browsers communicate with your Laravel apps.
