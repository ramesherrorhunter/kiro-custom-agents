---
name: scan_vulnerabilities
description: Scan source code for common security vulnerabilities. Use after analyze_project.
---

# Skill: scan_vulnerabilities

## Goal
Find security vulnerabilities in the codebase.

## Instructions
Scan all source files for the following vulnerability categories:

### Critical
- **Hardcoded secrets**: API keys, passwords, tokens, private keys in source files (not .env)
- **SQL injection**: string concatenation in DB queries instead of parameterized queries
- **Command injection**: user input passed to `exec`, `eval`, `subprocess`, `os.system`

### High
- **XSS**: unescaped user input rendered in HTML responses
- **Path traversal**: user-controlled file paths without sanitization
- **Insecure deserialization**: `pickle.loads`, `yaml.load` (without Loader), `unserialize`
- **Missing authentication**: routes/endpoints with no auth middleware

### Medium
- **Open redirects**: redirect URLs built from user input without validation
- **Sensitive data in logs**: logging passwords, tokens, or PII
- **Weak cryptography**: MD5/SHA1 for passwords, `Math.random()` for security tokens
- **Missing HTTPS enforcement**: HTTP-only configurations in production

### Low
- **Verbose error messages**: stack traces or internal paths exposed to users
- **Missing security headers**: no helmet/CSP/HSTS configuration
- **Outdated dependency versions**: check package.json / requirements.txt for known-vulnerable pinned versions

## Output
List of findings: { severity, file, line, issue, snippet }
