---
name: detect_runtime
description: Detect runtime configuration such as the exposed port from project files. Use when generating a Dockerfile to determine the correct port to expose.
---

# Skill: detect_runtime

## Goal
Detect runtime configuration such as port.

## Instructions
- Search project files for PORT usage
- Extract numeric port if found
- If not found → port = 3000

## Output
port