# Data Model: Basic Calculator

This document outlines the key data entities and their relationships for the Basic Calculator feature.

## 1. External Entities (User-facing)

### 1.1. Expression
*   **Description**: A string representing a mathematical calculation provided by the user.
*   **Type**: `str`
*   **Validation Rules**: Must conform to valid mathematical syntax, contain supported operators, and numeric operands.

### 1.2. Result
*   **Description**: The numerical outcome of a successfully evaluated mathematical expression.
*   **Type**: `float`
*   **Validation Rules**: None (derived from calculation).

### 1.3. Error Message
*   **Description**: A string providing feedback to the user about an invalid operation (e.g., division by zero) or malformed input.
*   **Type**: `str`
*   **Possible Values**: "Error: Division by zero", "Error: Invalid input or syntax"

## 2. Internal Entities (Calculator Logic)

### 2.1. Token
*   **Description**: Represents a lexical unit of the input expression (e.g., number, operator, parenthesis).
*   **Fields**:
    *   `type`: `TokenType` (enum: NUMBER, OPERATOR, PAREN_OPEN, PAREN_CLOSE)
    *   `value`: `str` (e.g., "2", "+", "(")
*   **Relationships**: Tokens are generated from an `Expression` during the tokenization phase.

### 2.2. Operator
*   **Description**: Represents a mathematical operator with its properties.
*   **Fields**:
    *   `symbol`: `str` (e.g., "+", "-", "*", "/", "^")
    *   `precedence`: `int` (e.g., 1 for +, -, 2 for *, /, 3 for ^)
    *   `associativity`: `Associativity` (enum: LEFT, RIGHT)

### 2.3. Node (Abstract Syntax Tree - AST)
*   **Description**: Represents a node in the Abstract Syntax Tree, forming a hierarchical representation of the mathematical expression.
*   **Types of Nodes**:
    *   **NumberNode**:
        *   `value`: `float`
    *   **BinaryOpNode**:
        *   `operator`: `Operator`
        *   `left`: `Node`
        *   `right`: `Node`
*   **Relationships**: Nodes are constructed from `Tokens` during the parsing phase and form a tree structure that is then evaluated.
