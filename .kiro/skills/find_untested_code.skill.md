---
name: find_untested_code
description: Identify functions and modules with no corresponding tests. Use after analyze_project.
---

# Skill: find_untested_code

## Goal
Find source code that has no test coverage.

## Instructions
- Locate test files using naming conventions:
  - node/ts: `*.test.*`, `*.spec.*`, `__tests__/`
  - python: `test_*.py`, `*_test.py`, `tests/`
  - go: `*_test.go`
  - java: `*Test.java`, `src/test/`
  - rust: `#[cfg(test)]` blocks, `tests/`
  - ruby: `*_spec.rb`, `spec/`, `test/`
- List all exported/public functions and classes in source files
- Cross-reference against test files to find untested ones
- Prioritize: exported functions > utility functions > internal helpers

## Output
List of untested functions/classes: { file, function_name, line }
