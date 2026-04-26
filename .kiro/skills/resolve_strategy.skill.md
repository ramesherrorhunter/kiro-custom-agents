---
name: resolve_strategy
description: Determine the Dockerfile build strategy (single-stage vs multi-stage) based on language and framework. Use after detecting language and framework.
---

# Skill: resolve_strategy

## Goal
Decide the appropriate Dockerfile build strategy.

## Instructions
- Use **multi-stage** when there is a compile/build step:
  - node with a `build` script in `package.json`
  - go (always compile)
  - java (always compile)
- Use **single-stage** for interpreted languages with no build step:
  - python
  - node without a build script

## Output
strategy: "multi-stage" | "single-stage"
