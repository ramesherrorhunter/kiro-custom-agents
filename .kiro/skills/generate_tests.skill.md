---
name: generate_tests
description: Generate unit tests for untested functions. Use after find_untested_code.
---

# Skill: generate_tests

## Goal
Write meaningful unit tests for identified untested code.

## Instructions
- Use the existing test framework — never introduce a new one:
  - node: jest, vitest, mocha (check package.json devDependencies)
  - python: pytest or unittest (check pyproject.toml / requirements)
  - go: standard `testing` package
  - java: JUnit 5
  - rust: built-in `#[test]`
  - ruby: RSpec or minitest
- For each untested function, write tests covering:
  1. Happy path — expected input → expected output
  2. Edge cases — empty input, zero, null/nil, boundary values
  3. Error cases — invalid input, exceptions/panics
- Mock external dependencies (DB calls, HTTP requests, filesystem I/O)
- Follow the existing test file naming convention and directory structure
- Place test files next to source files or in the existing test directory

## Output
Test files written alongside source files or in the test directory
