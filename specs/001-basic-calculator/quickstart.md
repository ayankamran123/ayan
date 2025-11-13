# Quickstart Guide: Basic Calculator Core Library

This guide provides instructions on how to set up and test the Basic Calculator core library.

## 1. Setup

### Prerequisites
*   Python 3.12+ installed.
*   `uv` (a fast Python package installer and resolver) installed. If not installed, you can get it with `pip install uv`.

### Installation
1.  **Clone the repository** (if you haven't already):
    ```bash
    git clone <repository-url>
    cd calc
    ```
2.  **Create a virtual environment and install dependencies**:
    ```bash
    uv venv
    source .venv/bin/activate  # On Windows, use `.venv\Scripts\activate`
    uv pip install pytest
    ```

## 2. Running Tests

Ensure your virtual environment is activated before running tests.

### Run all tests

```bash
pytest tests/
```

### Run specific tests (e.g., unit tests)

```bash
pytest tests/unit/
```
