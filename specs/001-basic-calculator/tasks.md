# Tasks: Basic Calculator

**Input**: Design documents from `/specs/001-basic-calculator/`
**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, data-model.md, contracts/

**Tests**: The examples below include test tasks. Tests are OPTIONAL - only include them if explicitly requested in the feature specification.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- **Single project**: `src/`, `tests/` at repository root
- **Web app**: `backend/src/`, `frontend/src/`
- **Mobile**: `api/src/`, `ios/src/` or `android/src/`
- Paths shown below assume single project - adjust based on plan.md structure

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Project initialization and basic structure

- [ ] T001 Initialize Python project with `uv init`
- [ ] T002 Create `src/calculator/` directory
- [ ] T003 Create `tests/unit/` directory
- [ ] T004 Create `src/calculator/__init__.py` (for package)
- [ ] T005 Create `tests/unit/__init__.py` (for package)
- [ ] T006 Install `pytest` using `uv pip install pytest`

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [ ] T006 Define `TokenType` enum in `src/calculator/tokens.py`
- [ ] T007 Define `Associativity` enum in `src/calculator/operators.py`
- [ ] T008 Define `Operator` dataclass in `src/calculator/operators.py`
- [ ] T009 Define base `Node` class and `NumberNode`, `BinaryOpNode` dataclasses in `src/calculator/ast.py`
- [ ] T010 Define custom exception classes (`CalculatorError`, `DivisionByZeroError`, `InvalidSyntaxError`) in `src/calculator/exceptions.py`

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - Perform Basic Arithmetic (Priority: P1) 🎯 MVP

**Goal**: Implement core arithmetic operations and correct evaluation of expressions.

**Independent Test**: Can be fully tested by providing various valid expressions and verifying the output.

### Tests for User Story 1 ⚠️

> **NOTE: Write these tests FIRST, ensure they FAIL before implementation**

- [ ] T011 [US1] Write unit tests for tokenization in `tests/unit/test_tokenizer.py`
- [ ] T012 [US1] Write unit tests for parsing (Shunting-yard) in `tests/unit/test_parser.py`
- [ ] T013 [US1] Write unit tests for expression evaluation in `tests/unit/test_evaluator.py`

### Implementation for User Story 1

- [ ] T014 [US1] Implement `Tokenizer` class for expression tokenization in `src/calculator/tokenizer.py`
- [ ] T015 [US1] Implement `Parser` class using Shunting-yard algorithm in `src/calculator/parser.py`
- [ ] T016 [US1] Implement `Evaluator` class for AST traversal and calculation in `src/calculator/evaluator.py`
- [ ] T017 [US1] Create `calculate` function as the main entry point in `src/calculator/calculator.py`

**Checkpoint**: At this point, User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - Handle Division by Zero (Priority: P1)

**Goal**: Gracefully handle division by zero errors and provide clear feedback.

**Independent Test**: Can be fully tested by providing expressions that include division by zero and verifying the error message.

### Tests for User Story 2 ⚠️

- [ ] T018 [US2] Write unit tests for division by zero handling in `tests/unit/test_evaluator.py`

### Implementation for User Story 2

- [ ] T019 [US2] Integrate division by zero error handling into `Evaluator` class in `src/calculator/evaluator.py`

**Checkpoint**: At this point, User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - Handle Invalid Input (Priority: P2)

**Goal**: Detect and report invalid input or syntax errors.

**Independent Test**: Can be fully tested by providing various invalid expressions and verifying the error messages.

### Tests for User Story 3 ⚠️

- [ ] T020 [US3] Write unit tests for invalid input/syntax handling in `tests/unit/test_tokenizer.py` and `tests/unit/test_parser.py`

### Implementation for User Story 3

- [ ] T021 [US3] Integrate invalid input error handling into `Tokenizer` and `Parser` classes in `src/calculator/tokenizer.py` and `src/calculator/parser.py`

**Checkpoint**: All user stories should now be independently functional

---

## Phase N: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [ ] T022 Ensure all code adheres to PEP 8, type hints, and docstring requirements in `src/calculator/`
- [ ] T023 Achieve 80% test coverage for `src/calculator/` (run `pytest --cov=src/calculator`)
- [ ] T024 Implement performance test for expressions up to 100 characters in `tests/unit/test_performance.py`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
  - User stories can then proceed in parallel (if staffed)
  - Or sequentially in priority order (P1 → P2 → P3)
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P1)**: Can start after Foundational (Phase 2) - May integrate with US1 but should be independently testable
- **User Story 3 (P2)**: Can start after Foundational (Phase 2) - May integrate with US1/US2 but should be independently testable

### Within Each User Story

- Tests (if included) MUST be written and FAIL before implementation
- Models before services
- Services before endpoints
- Core implementation before integration
- Story complete before moving to next priority

### Parallel Opportunities

- All Setup tasks marked [P] can run in parallel
- All Foundational tasks marked [P] can run in parallel (within Phase 2)
- Once Foundational phase completes, all user stories can start in parallel (if team capacity allows)
- All tests for a user story marked [P] can run in parallel
- Models within a story marked [P] can run in parallel
- Different user stories can be worked on in parallel by different team members

---

## Parallel Example: User Story 1

```bash
# Launch all tests for User Story 1 together (if tests requested):
Task: "Write unit tests for tokenization in tests/unit/test_tokenizer.py"
Task: "Write unit tests for parsing (Shunting-yard) in tests/unit/test_parser.py"
Task: "Write unit tests for expression evaluation in tests/unit/test_evaluator.py"

# Launch all models for User Story 1 together:
Task: "Implement Tokenizer class for expression tokenization in src/calculator/tokenizer.py"
Task: "Implement Parser class using Shunting-yard algorithm in src/calculator/parser.py"
Task: "Implement Evaluator class for AST traversal and calculation in src/calculator/evaluator.py"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (CRITICAL - blocks all stories)
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Test User Story 1 independently
5. Deploy/demo if ready

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Test independently → Deploy/Demo (MVP!)
3. Add User Story 2 → Test independently → Deploy/Demo
4. Add User Story 3 → Test independently → Deploy/Demo
5. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
3. Stories complete and integrate independently

---

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and testable
- Verify tests fail before implementing
- Commit after each task or logical group
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence
- **Human Review**: After each phase, pause for human review and approval before proceeding to the next phase.
