---
name: generate_audit_report
description: Generate a prioritized security audit report with remediation steps. Use after scan_vulnerabilities.
---

# Skill: generate_audit_report

## Goal
Produce a clear, actionable security audit report.

## Instructions
Write `SECURITY_AUDIT.md` with the following structure:

1. **Summary** — total findings by severity (Critical / High / Medium / Low)
2. **Findings** — one section per finding:
   - Severity badge
   - File and line number
   - Description of the issue
   - Vulnerable code snippet
   - Recommended fix with corrected code example
3. **Quick Wins** — list of Low-effort / High-impact fixes to do first
4. **Dependencies** — note any known-vulnerable packages found

## Rules
- Sort findings: Critical → High → Medium → Low
- Be specific — always include file path and line number
- Provide concrete fix examples, not just generic advice
- Do NOT modify any source files

## Output
SECURITY_AUDIT.md written to project root
