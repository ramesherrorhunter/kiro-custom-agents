---
name: generate_readme
description: Generate a comprehensive README.md from analyzed project data. Use after analyze_project and analyze_structure.
---

# Skill: generate_readme

## Goal
Write a clear, complete README.md for the project.

## Instructions
Generate a README.md with these sections (skip any section where data is unavailable):

1. **Title + description** — project name and one-line description inferred from code/config
2. **Features** — bullet list of key capabilities inferred from routes, dependencies, and code
3. **Tech Stack** — language, framework, major dependencies
4. **Prerequisites** — runtime version requirements (Node >=X, Python >=X, etc.)
5. **Installation**
   ```
   git clone ...
   cd <project>
   <install command>
   ```
6. **Environment Variables** — table of keys from .env.example with description column (leave blank if unknown)
7. **Available Scripts** — table of script name → what it does
8. **Usage** — how to start the app (dev and production commands)
9. **API Routes** — table of method, path, description (only if routes detected)
10. **License** — infer from LICENSE file if present

## Rules
- Keep each section concise
- Use tables where appropriate
- Do not invent features — only document what is found in the code

## Output
README.md written to project root
