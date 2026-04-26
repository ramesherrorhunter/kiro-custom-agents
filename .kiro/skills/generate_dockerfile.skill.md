---
name: generate_dockerfile
description: Generate an optimized, production-ready Dockerfile with best practices applied. Use after analyze_project and resolve_strategy.
---

# Skill: generate_dockerfile

## Goal
Generate a complete, optimized, production-ready Dockerfile in one step.

## Instructions
- Use the language, framework, port, and strategy from previous steps
- Use minimal base images: `alpine` or `slim` variants
- For multi-stage builds: separate build and runtime stages
- Install only production dependencies
- Copy only necessary files
- Expose the detected port
- Always run as a non-root user (create and switch to a dedicated user)
- Minimize layers: chain related RUN commands with `&&`
- Clean package manager caches in the same RUN layer they are created
- Add a brief comment above each major section (deps, build, runtime)

### Language-specific guidance
- **node**: `node:lts-alpine`; multi-stage if `build` script exists; `npm ci --omit=dev` for production
- **python**: `python:3.12-slim`; use `pip install --no-cache-dir`; single-stage
- **go**: `golang:alpine` builder → `gcr.io/distroless/static` or `alpine` runtime; always multi-stage
- **java**: `eclipse-temurin:21-jdk-alpine` builder → `eclipse-temurin:21-jre-alpine` runtime; always multi-stage
- **rust**: `rust:alpine` builder → `alpine` runtime; always multi-stage; copy only the compiled binary
- **ruby**: `ruby:3-alpine`; `bundle install --without development test`; single-stage unless asset pipeline present
- **generic**: `alpine:latest`; copy files, expose port, set non-root user

## Output
Dockerfile written to the project directory
