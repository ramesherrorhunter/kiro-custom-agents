---
name: analyze_structure
description: Analyze project directory structure, entry points, API routes, and available scripts. Use before generating a README.
---

# Skill: analyze_structure

## Goal
Understand the project layout to produce accurate documentation.

## Instructions
- List top-level directories and files (exclude node_modules, .git, dist, build)
- Identify entry point:
  - node: `main` field in package.json, or `src/index.*`, `app.*`, `server.*`
  - python: `main.py`, `app.py`, `manage.py`, `wsgi.py`
  - go: `main.go` or `cmd/*/main.go`
  - java: class with `public static void main`
  - rust: `src/main.rs`
  - ruby: `config.ru`, `app.rb`
- Extract available scripts from:
  - `package.json` → `scripts` field
  - `Makefile` → targets
  - `pyproject.toml` → `[tool.taskipy.tasks]` or similar
- Extract env vars from `.env.example` or `.env.sample` (keys only)
- Detect API routes if present (Express routes, Flask blueprints, FastAPI routers, etc.)

## Output
entry_point, scripts, env_vars, routes, directory_summary
