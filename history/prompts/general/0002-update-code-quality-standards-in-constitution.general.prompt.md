---
ID: 0002
TITLE: "Update Code Quality Standards in Constitution"
STAGE: "general"
DATE_ISO: "2025-11-12"
SURFACE: "agent"
MODEL: "gemini"
FEATURE: "none"
BRANCH: "main"
USER: "Ayan"
COMMAND: "Update @.specify/memory/constitution.md to improve Code Quality Standards"
LABELS: ["constitution", "code-quality"]
LINKS:
  SPEC: "null"
  TICKET: "null"
  ADR: "null"
  PR: "null"
FILES_YAML:
  - ".specify/memory/constitution.md"
TESTS_YAML: []
PROMPT_TEXT: |
  Update @.specify/memory/constitution.md to improve Code Quality Standards

  - All functions must include type hints on parameters and return types
    - Example: `def add(a: float, b: float) -> float:`
  - All functions must include docstrings explaining what they do
    - Example: `"""Add two numbers and return the sum."""`
  - Follow PEP 8 naming conventions (lowercase_with_underscores for functions)
  - Lines must be under 100 characters
  - No magic numbers; use named constants
    - Bad: `if x > 10:`
    - Good: `if x > MAX_POWER_EXPONENT:`
RESPONSE_TEXT: |
  The `.specify/memory/constitution.md` file has been updated with the new code quality standards and the version information.
OUTCOME: "Success"
EVALUATION: "The constitution file was updated as requested, including new code quality standards and version bump."
---
