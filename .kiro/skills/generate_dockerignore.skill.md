---
name: generate_dockerignore
description: Generate a .dockerignore file to exclude unnecessary files from the Docker build context. Use after generating the Dockerfile.
---

# Skill: generate_dockerignore

## Goal
Generate a `.dockerignore` file appropriate for the detected language.

## Instructions
- Always exclude: `.git`, `*.md`, `.env*`, `*.log`
- For node: exclude `node_modules`, `.npm`, `coverage`, `dist` (if rebuilt in Docker)
- For python: exclude `__pycache__`, `*.pyc`, `.venv`, `*.egg-info`
- For go: exclude `vendor` if modules are used
- For java: exclude `target/`, `.gradle/`, `build/`

## Output
.dockerignore file content
