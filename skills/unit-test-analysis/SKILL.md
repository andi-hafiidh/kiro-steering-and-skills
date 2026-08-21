---
name: unit-test-analysis
description: Analyze existing unit tests, identify test coverage and gaps, and generate a standardized unit test plan based on actual application behavior.
---

# Unit Test Analysis Skill

## Purpose

Analyze the application's existing unit tests and identify coverage, testing strategy, critical paths, and testing gaps.

Do not claim that a test exists unless it can be found in the repository.

---

# 1. Identify Testing Framework

Determine the testing framework from the repository.

Examples:

```text
Go:
testing
testify
gomock
mockery

JavaScript:
Jest
Vitest
Mocha

Python:
pytest
unittest

Java:
JUnit
Mockito
```

Only report frameworks actually used.

---

# 2. Identify Test Files

Search for:

```text
*_test.go
*.test.ts
*.test.tsx
*.spec.ts
*.spec.tsx
test_*.py
*_test.py
```

Adapt based on the language.

---

# 3. Identify Testable Components

Analyze:

- handlers
- controllers
- services
- use cases
- repositories
- utilities
- validators
- business logic
- workers
- consumers

Prioritize business-critical logic.

---

# 4. Test Scenario Classification

Classify scenarios as:

```text
Positive
Negative
Boundary
Error Handling
Dependency Failure
Timeout
Concurrency
Validation
Authorization
```

---

# 5. Identify Existing Tests

For each component determine:

```text
Test Exists
Test Partial
Test Missing
```

Never assume coverage.

---

# 6. Mocking Analysis

Identify:

- database mocks
- HTTP mocks
- Redis mocks
- Kafka mocks
- filesystem mocks
- external service mocks

Document the actual mocking strategy.

---

# 7. Coverage

If coverage reports or configuration exist, inspect them.

Document:

- overall coverage
- package coverage
- critical-path coverage
- uncovered areas

If coverage is unavailable:

```text
Coverage: Unknown / Not Defined
```

---

# 8. Test Gap Analysis

Identify high-risk missing tests.

Prioritize:

```text
Critical Business Logic
        ↓
External Integration
        ↓
Error Handling
        ↓
Validation
        ↓
Boundary Conditions
        ↓
Low-Risk Utilities
```

---

# 9. Output

Update:

```text
docs/05-unit-test-plan.md
```

Include:

- testing objective
- scope
- strategy
- test scenarios
- mocking strategy
- coverage
- test gaps
- recommended tests

Clearly distinguish:

```text
Implemented Test
Planned Test
Missing Test
```