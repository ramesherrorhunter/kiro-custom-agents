---
name: generate_dockerfile
description: Generate a production-ready Dockerfile based on detected language, framework, and runtime. Use after all detection steps are complete.
---

# Skill: generate_dockerfile

## Goal
Generate an optimized, production-ready Dockerfile.

## Instructions
- Use detected language, framework, and port
- Use multi-stage build when there is a build step (node, java, go)
- Use minimal base images: `alpine` or `slim` variants
- Install only production dependencies
- Copy only necessary files
- Expose the detected port
- Set a non-root user (handled by optimize_dockerfile)

## Output
dockerfile
