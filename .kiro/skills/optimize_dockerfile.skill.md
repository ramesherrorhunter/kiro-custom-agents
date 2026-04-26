---
name: optimize_dockerfile
description: Enhance a Dockerfile with best practices including non-root user, minimal layers, and production-only dependencies. Use after generating a Dockerfile to improve it.
---

# Skill: optimize_dockerfile

## Goal
Enhance Dockerfile with best practices.

## Instructions
- Ensure non-root user is used
- Minimize layers where possible
- Use production dependency install only
- Remove unnecessary files (cache, dev deps)
- Add comments for clarity

## Output
dockerfile_optimized