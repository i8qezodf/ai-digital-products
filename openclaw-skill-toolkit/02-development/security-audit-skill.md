# Security Audit Skill

Find and fix security issues in code or infrastructure.

## When to Use

Auditing code for vulnerabilities, reviewing infrastructure config, or investigating a potential breach.

## The Skill

```
Security audit this system/code:

TYPE: [code / infrastructure / web app / API]
LANGUAGE/STACK: [what it's built with]
CODE/CONFIG:
[paste code or describe system]

REVIEW SCOPE:
- [ ] OWASP Top 10 check
- [ ] Authentication/Authorization
- [ ] Input validation
- [ ] Data exposure
- [ ] Dependency vulnerabilities
- [ ] Configuration issues
- [ ] Logging and monitoring

For each finding:
VULNERABILITY: [name]
LOCATION: [file/function/endpoint]
SEVERITY: [Critical / High / Medium / Low]
DESCRIPTION: [what the issue is]
PROOF: [how to demonstrate it]
IMPACT: [what a bad actor could do]
REMEDIATION: [how to fix it, with code if applicable]
PRIORITY: [order to fix in]
```

## Common Issues Checklist

### Injection
- SQL injection (parameterized queries)
- Command injection (avoid shell calls with user input)
- XSS (output encoding)
- LDAP injection
- XXE (disable XML external entities)

### Authentication
- Weak password policies
- Session fixation/hijacking
- Missing logout / token expiration
- Hardcoded credentials
- Insecure password reset

### Data Exposure
- Sensitive data in logs
- Exposed debugging endpoints
- Missing rate limiting
- Information in error messages
- Unencrypted data in transit (no HTTPS)

### Access Control
- Missing authorization checks
- IDOR (Insecure Direct Object References)
- Privilege escalation
- CORS misconfiguration

### Cryptography
- Weak or custom crypto
- Hardcoded keys
- Insecure random number generation
- No encryption for sensitive data

## Example Finding

```
VULNERABILITY: SQL Injection in User Search
LOCATION: src/users/search.ts, line 23
SEVERITY: Critical
DESCRIPTION: User-supplied 'query' parameter concatenated directly into SQL
PROOF: Request with query=admin' OR '1'='1 returns all users
IMPACT: Attacker can read/modify/delete any user data
REMEDIATION:
```javascript
// BEFORE (vulnerable)
const results = db.query("SELECT * FROM users WHERE name LIKE '%" + query + "%'");

// AFTER (safe)
const results = db.query("SELECT * FROM users WHERE name LIKE ?", [`%${query}%`]);
```
PRIORITY: 1
```

## Tips

- Focus on data you would want to protect
- Rate the severity honestly — not everything is critical
- Always provide working fixes, not just "this is wrong"
- Document findings even if you can't fix immediately

## Variations

**Quick scan:** Focus on Critical/High only, skip detailed proofs
**Compliance review:** Add PCI-DSS, GDPR, or other framework checks
**Infrastructure:** Focus on IAM, networking, encryption at rest
