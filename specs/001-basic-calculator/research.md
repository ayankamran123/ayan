# Research: Expression Parsing for Basic Calculator

## Decision: Expression Parsing Method

### Rationale:
For a basic calculator, a robust and secure method for parsing mathematical expressions is crucial. Given the constraints and the need to handle various operators and parentheses, a custom parser or a well-vetted library is preferred over direct `eval()` due to security risks.

### Alternatives Considered:

1.  **`eval()`**:
    *   **Pros**: Simple to use, handles complex expressions directly.
    *   **Cons**: **Major security risk** as it can execute arbitrary code. Not suitable for user-provided input.
    *   **Trade-offs**: High convenience vs. unacceptable security vulnerability.

2.  **`ast.literal_eval()`**:
    *   **Pros**: Safer than `eval()` as it only evaluates literals (strings, numbers, tuples, lists, dicts, booleans, None).
    *   **Cons**: Cannot evaluate mathematical expressions directly (e.g., "2 + 3" would not work).
    *   **Trade-offs**: High security vs. limited functionality for this use case.

3.  **Custom Parser (e.g., using `pyparsing` or hand-rolled)**:
    *   **Pros**: Full control over parsing logic, can implement specific error handling, highly secure.
    *   **Cons**: More complex to implement, requires understanding of parsing techniques.
    *   **Trade-offs**: High control and security vs. increased development effort.

4.  **`numexpr` or similar scientific computing libraries**:
    *   **Pros**: Optimized for numerical expressions, often faster.
    *   **Cons**: Might be overkill for a "basic" calculator, adds external dependency.
    *   **Trade-offs**: Performance vs. simplicity and dependency management.

### Chosen Approach: Custom Parser (Shunting-yard algorithm or similar)

Given the "basic calculator" scope and the need for robust error handling (division by zero, invalid syntax) without external dependencies for core parsing, a custom parser based on an algorithm like Shunting-yard is the most appropriate. This allows for precise control over operator precedence and associativity, and enables detailed error reporting. This will be implemented within the `src/calculator/` module.

## Testing Strategy

### Unit Tests
*   **Scope**: Individual functions and classes within the `src/calculator/` module (e.g., tokenization, parsing, evaluation of expressions).
*   **Framework**: `pytest`.
*   **Acceptance Criteria Mapping**: Each functional requirement (FR-001 to FR-004) will have corresponding unit tests to verify the correctness of the core logic.
    *   FR-001: Test various combinations of arithmetic operations and parentheses.
    *   FR-002: Test operator precedence and associativity.
    *   FR-003: Test division by zero scenarios.
    *   FR-004: Test invalid input and syntax errors.
*   **Performance Testing**: SC-004 will be verified with unit tests that measure execution time for expressions up to 100 characters in the core logic.
