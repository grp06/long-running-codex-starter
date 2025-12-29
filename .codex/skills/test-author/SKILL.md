---
name: test-author
description: Generate an extensive, runnable, intentionally failing test suite from a PRD so the tests become the executable spec.
license: MIT
compatibility: "OpenCode / Agent Skills. Requires pytest. Tests must run offline; avoid network dependencies."
metadata:
  short-description: Write failing tests from a PRD
  category: testing
  artifact: failing-test-suite
  output: repo-files
  audience: engineering
---

# Test Author

## Purpose
Produce a large, runnable, intentionally failing test suite that encodes the PRD as the executable spec.

## Inputs
- PRD path (default `prd/PRD.md`)
- Use pytest test framework and conventions

## Outputs
- Test files following pytest conventions (`test_*.py` files in `tests/` directory)
- `tests/catalog.yaml` (or `tests/catalog.json` if YAML is not used in repo)
- `tests/README.md` with pytest run instructions and failure summary

## Rules
- Do not implement features or make tests pass.
- Tests must execute deterministically and offline.
- Use pytest as the test framework.
- Prefer black-box assertions over internal details.
- Minimal scaffolding is allowed only to make tests runnable and must not satisfy assertions.

## Workflow
1. Use pytest as the test framework.
2. Parse the PRD into a requirement matrix (FR/NFR, acceptance criteria, constraints, edge cases).
3. Write tests top-down: acceptance, integration, unit, contract, and NFR where stable.
4. Ensure failures map to missing behavior, not setup issues.
5. Run tests and document failure categories and assumptions in `tests/README.md`.
6. Emit the test catalog mapping tests to requirements.

## Test IDs and mapping
- Use stable IDs: AT-###, IT-###, UT-###, CT-###, NFT-###.
- Include the ID in the test name (e.g., `test_AT_001_user_can_create`).
- Map each test to FR/NFR IDs in `tests/catalog.yaml`.

## Pytest Best Practices

### Test Structure and Organization
- Place tests in `tests/` directory with files named `test_*.py`
- Use descriptive test function names starting with `test_` (e.g., `test_user_can_create_account`)
- Separate unit and integration tests using markers and directories:
  ```
  tests/
    unit/
      test_utils.py
      test_models.py
    integration/
      test_api_endpoints.py
      test_database_operations.py
  ```

### Unit Test Best Practices
- Keep tests isolated and independent - each test runs standalone
- Test one behavior per test function
- Use fixtures for shared setup/teardown in `conftest.py` or test modules:
  ```python
  @pytest.fixture
  def sample_data():
      return {"key": "value"}
  ```
- Parametrize tests for multiple input cases:
  ```python
  @pytest.mark.parametrize("input,expected", [(1, 2), (3, 4), (-1, 0)])
  def test_increment(input, expected):
      assert increment(input) == expected
  ```
- Mock external dependencies using `unittest.mock` or `pytest.monkeypatch`
- Follow AAA pattern: Arrange (setup), Act (call code), Assert (check results)
- Test edge cases and failure scenarios

### Integration Test Best Practices
- Mark integration tests: `@pytest.mark.integration`
- Use fixtures for setting up test databases, API clients, etc.
- Run integration tests separately: `pytest -m integration`
- Isolate external services with mocks where possible
- Use in-memory/test databases when feasible
- Keep integration tests reliable and reasonably fast (<30 seconds total)

### General Guidelines
- Use plain `assert` statements (no `self.assertEqual()`)
- Aim for meaningful test coverage over 100% coverage
- Write fast tests - avoid real network/database calls
- Run units on every change, integration tests on schedule
- Follow testing pyramid: many units, moderate integration, few end-to-end

## Validation checklist
- Tests run with `pytest` command and documented in `tests/README.md`.
- Failures indicate missing behavior, not environment issues.
- Each requirement maps to at least one test in the catalog.
- No production implementation added beyond minimal compilation stubs.
