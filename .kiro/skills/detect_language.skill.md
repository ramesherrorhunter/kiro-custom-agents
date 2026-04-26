---
name: detect_language
description: Detect the primary programming language of a project by inspecting its files. Use when analyzing a codebase to determine language before generating a Dockerfile.
---

# Skill: detect_language

## Goal
Detect the primary programming language of the project.

## Instructions
- Inspect files in the project directory provided by the user (or current directory if not specified)
- If `package.json` exists → language = node
- If `requirements.txt` or `pyproject.toml` exists → language = python
- If `go.mod` exists → language = go
- If `pom.xml` or `build.gradle` exists → language = java
- Otherwise → language = generic

## Output
language