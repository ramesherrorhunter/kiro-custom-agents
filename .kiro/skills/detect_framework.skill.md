---
name: detect_framework
description: Detect the web framework or build tool used in a project. Use after detecting language to choose the right Dockerfile base image and build commands.
---

# Skill: detect_framework

## Goal
Detect the framework or build tool used in the project.

## Instructions
- For node: check `package.json` dependencies for express, fastify, next, nest, etc.
- For python: check `requirements.txt` or `pyproject.toml` for django, flask, fastapi, etc.
- For go: check `go.mod` for gin, echo, fiber, etc.
- For java: check `pom.xml` or `build.gradle` for spring-boot, quarkus, etc.
- If none detected → framework = generic

## Output
framework
