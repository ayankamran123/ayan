# Calc Constitution

<!-- 
Sync Impact Report:
- Version change: 1.0.0 → 1.1.0
- List of modified principles: 
  - V. Adherence to OOP Principles → V. Object-Oriented Programming (OOP) Principles
- Added sections: Detailed explanations for OOP concepts (SOLID, DRY, KISS, Encapsulation, Inheritance, Polymorphism).
- Removed sections: None
- Templates requiring updates: None
- Follow-up TODOs: None
-->

## 1. Core Principles

### I. Test-First Development (TDD)
**Rule**: All new functionality must be preceded by a failing test. The Red-Green-Refactor cycle is to be strictly followed.
**Rationale**: This ensures that all code is testable by design, reduces bugs, and provides a safety net for future refactoring.

### II. Python 3.12+ with Strict Type Hints
**Rule**: All code must be written for Python 3.12+ and include type hints for all function signatures, class members, and variables.
**Rationale**: Type hints improve code clarity, allow for static analysis, and help prevent common runtime errors.

### III. Clean and Readable Code
**Rule**: Code should be self-documenting, with clear naming conventions and logical structure. Complexity should be minimized.
**Rationale**: Maintainable code is easy to understand, modify, and debug, reducing long-term development costs.

#### Code Quality Standards:
*   All functions must include type hints on parameters and return types.
    *   Example: `def add(a: float, b: float) -> float:`
*   All functions must include docstrings explaining what they do.
    *   Example: `"""Add two numbers and return the sum."""`
*   Follow PEP 8 naming conventions (lowercase_with_underscores for functions).
*   Lines must be under 100 characters.
*   No magic numbers; use named constants.
    *   Bad: `if x > 10:`
    *   Good: `if x > MAX_POWER_EXPONENT:`

### IV. Document Decisions with ADRs
**Rule**: Significant architectural or technical decisions must be documented in an Architecture Decision Record (ADR).
**Rationale**: ADRs provide a historical record of key decisions, their context, and their trade-offs, which is invaluable for onboarding and future architectural evolution.

### V. Object-Oriented Programming (OOP) Principles
**Rule**: The design of classes and objects must adhere to established OOP principles to ensure a modular, maintainable, and scalable architecture.
**Rationale**: Following these principles leads to a system that is easier to extend, less prone to bugs, and more resilient to change.

#### Key OOP Concepts to Adhere To:

*   **SOLID**:
    *   **S**ingle Responsibility Principle: A class should have only one reason to change.
    *   **O**pen/Closed Principle: Software entities should be open for extension, but closed for modification.
    *   **L**iskov Substitution Principle: Subtypes must be substitutable for their base types.
    *   **I**nterface Segregation Principle: Clients should not be forced to depend on interfaces they do not use.
    *   **D**ependency Inversion Principle: High-level modules should not depend on low-level modules. Both should depend on abstractions.

*   **DRY (Don't Repeat Yourself)**: Avoid duplication of code. Abstract out common functionality into reusable components.

*   **KISS (Keep It Simple, Stupid)**: Favor simple, straightforward solutions over complex ones. Avoid unnecessary complexity.

*   **Encapsulation**: Bundle the data (attributes) and the methods that operate on the data into a single unit (a class). Restrict direct access to some of an object's components.

*   **Inheritance**: Allow a new class (subclass) to inherit properties and methods from an existing class (superclass). This promotes code reuse.

*   **Polymorphism**: Allow objects of different classes to be treated as objects of a common superclass. This enables writing flexible and decoupled code.

## 2. Technical Stack

- **Language**: Python 3.12+
- **Package Manager**: UV
- **Testing Framework**: pytest
- **Version Control**: Git

## 3. Quality Requirements

- **Test Coverage**: A minimum of 80% code coverage is required.
- **Test Pass Rate**: 100% of tests must pass for a build to be considered successful.
- **Data Structures**: Use dataclasses for plain data structures to ensure immutability and clarity.

## 4. Governance

- **Code Reviews**: All pull requests require at least one approving review from another team member before merging.
- **Compliance**: All code must adhere to the principles and standards outlined in this constitution.

**Version**: 1.2.0 | **Ratified**: 2025-11-12 | **Last Amended**: 2025-11-12
