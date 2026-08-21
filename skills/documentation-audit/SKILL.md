---
name: documentation-audit
description: Audit engineering documentation against the current source code, configuration, infrastructure, dependencies, tests, environment variables, and architecture to detect documentation drift, inconsistencies, missing documentation, and unsupported claims.
---

# Documentation Audit Skill

## Purpose

Perform a read-only audit of the project's engineering documentation.

The objective is to determine whether the documentation accurately represents the current implementation.

This skill MUST prioritize accuracy over completeness.

This skill MUST NOT modify source code.

Documentation MAY be updated only when explicitly requested by the user.

---

# 1. Audit Scope

Audit the following documentation:

```text
docs/
├── 01-functional-description.md
├── 02-infrastructure.md
├── 03-technology-stack.md
├── 04-data-flow.md
├── 05-unit-test-plan.md
└── 06-capacity-planning.md
```

Also inspect:

```text
Source Code
Configuration
Environment Variables
Dependencies
Docker
Docker Compose
Kubernetes
Helm
Terraform
CI/CD
Tests
Database Configuration
External Integrations
Observability
```

Only inspect files that exist.

---

# 2. Audit Principles

The source code and actual project configuration are the primary source of truth.

Documentation MUST be considered incorrect when:

- it describes something that no longer exists
- it omits a critical implemented component
- it contains an unsupported technical claim
- it contains outdated configuration
- it contains outdated infrastructure
- it contains outdated capacity information
- its architecture diagram does not match the implementation

---

# 3. Documentation Existence Check

Verify that all mandatory documentation exists:

```text
docs/01-functional-description.md
docs/02-infrastructure.md
docs/03-technology-stack.md
docs/04-data-flow.md
docs/05-unit-test-plan.md
docs/06-capacity-planning.md
```

Classify each document:

```text
Current
Partially Complete
Outdated
Missing
Unknown
```

---

# 4. Functional Documentation Audit

Compare:

```text
docs/01-functional-description.md
```

against:

- application entry points
- API handlers
- services
- business logic
- validation
- error handling
- external integrations

Check for:

- undocumented functionality
- documented functionality that no longer exists
- incorrect business flow
- missing error handling
- outdated external integrations
- unsupported business rules

Report discrepancies.

---

# 5. Infrastructure Audit

Compare:

```text
docs/02-infrastructure.md
```

against:

- `.env`
- `.env.example`
- Dockerfile
- Docker Compose
- Kubernetes
- Helm
- Terraform
- deployment configuration
- application configuration

Check:

- environment variables
- databases
- caches
- message brokers
- external APIs
- storage
- replicas
- CPU
- memory
- health checks
- ports
- network dependencies

---

# 6. Environment Variable Audit

Build an inventory of environment variables from the source code.

Compare it with the documented variables.

Classify:

```text
Documented and Used
Used but Not Documented
Documented but Not Used
Required but Missing
Environment Specific
Potential Secret
```

Example:

| Variable | Source | Documentation | Status |
|---|---|---|---|
| DB_HOST | Used | Yes | OK |
| REDIS_HOST | Used | No | Drift |
| OLD_API_URL | Not Used | Yes | Obsolete |

Never display actual secret values.

---

# 7. Technology Stack Audit

Compare:

```text
docs/03-technology-stack.md
```

against:

- dependency manifests
- imports
- build files
- Dockerfile
- infrastructure
- configuration

Check:

- programming language
- framework
- libraries
- database
- cache
- message broker
- API protocol
- authentication
- observability
- testing framework
- containerization
- deployment platform
- CI/CD

Identify:

```text
Documented and Verified
Implemented but Undocumented
Documented but Not Found
Version Mismatch
```

---

# 8. Data Flow Audit

Compare:

```text
docs/04-data-flow.md
```

against the actual implementation.

Verify:

- entry points
- services
- repositories
- databases
- caches
- message brokers
- external APIs
- synchronous communication
- asynchronous communication

For every Mermaid component ask:

```text
Does this component actually exist?
```

For every important implementation component ask:

```text
Is this component represented in the data flow?
```

Identify:

```text
Missing Component
Obsolete Component
Incorrect Connection
Incorrect Direction
Missing External Dependency
```

---

# 9. Mermaid Validation

Inspect all Mermaid diagrams.

Verify:

- syntax
- node consistency
- connection consistency
- architecture accuracy
- naming consistency

Example issue:

```text
Documentation:

Service --> Redis

Implementation:

Service does not use Redis.

Result:

Documentation Drift
```

---

# 10. Unit Test Documentation Audit

Compare:

```text
docs/05-unit-test-plan.md
```

against actual tests.

Verify:

- test framework
- test files
- test suites
- mocks
- fixtures
- critical paths
- negative cases
- boundary cases
- error scenarios
- coverage

Identify:

```text
Test Documented and Exists
Test Exists but Not Documented
Test Documented but Missing
Coverage Outdated
Testing Gap
```

Never claim coverage without evidence.

---

# 11. Capacity Planning Audit

Compare:

```text
docs/06-capacity-planning.md
```

against:

- Kubernetes resources
- Docker configuration
- replicas
- HPA
- connection pools
- database configuration
- Redis configuration
- Kafka configuration
- load test results
- monitoring metrics

Verify that every capacity value has an evidence classification:

```text
Measured
Configured
Calculated
Estimated
Unknown
```

Flag:

```text
Estimated value presented as measured
Outdated replica count
Outdated CPU configuration
Outdated memory configuration
Outdated database connection limit
Outdated traffic assumption
Missing capacity metric
Unsupported capacity claim
```

---

# 12. Infrastructure-to-Capacity Consistency

Check that infrastructure and capacity planning agree.

For example:

```text
Infrastructure:

Replicas = 3

Capacity Planning:

Replicas = 5
```

Result:

```text
Critical Documentation Drift
```

Other examples:

```text
CPU limit mismatch
Memory limit mismatch
DB connection mismatch
Redis connection mismatch
Storage mismatch
HPA mismatch
```

---

# 13. Cross-Document Consistency

Check consistency between all documents.

Examples:

```text
Infrastructure
      ↕
Technology Stack

Infrastructure
      ↕
Data Flow

Infrastructure
      ↕
Capacity Planning

Technology Stack
      ↕
Data Flow

Unit Test Plan
      ↕
Technology Stack
```

Flag conflicting information.

---

# 14. Source Traceability Audit

Important documentation claims SHOULD be traceable to implementation evidence.

For example:

```text
Claim:
Application uses Redis.

Evidence:
REDIS_HOST
Redis client initialization
Redis dependency
```

If evidence cannot be found:

```text
Unsupported Claim
```

---

# 15. Documentation Quality Classification

Classify each issue using:

## Critical

Documentation could cause an incorrect engineering or operational decision.

Examples:

- wrong database
- wrong deployment architecture
- wrong security mechanism
- wrong capacity
- wrong production dependency

## High

Important documentation is significantly outdated.

Examples:

- outdated API flow
- missing external service
- incorrect infrastructure

## Medium

Documentation is incomplete but does not immediately affect operation.

Examples:

- missing test scenario
- missing dependency description

## Low

Minor consistency or formatting issue.

Examples:

- naming inconsistency
- outdated example

---

# 16. Drift Score

Calculate a documentation health score.

Use:

```text
Documentation Score =
Verified Items / Total Audited Items × 100
```

Classify:

```text
90–100  Excellent
80–89   Good
70–79   Needs Improvement
<70     Poor
```

The score MUST be based on actual audit findings.

Do not fabricate the score.

---

# 17. Audit Report

The final audit report MUST follow this structure:

```markdown
# Documentation Audit Report

## Overall Status

PASS / PASS WITH WARNINGS / FAIL

## Documentation Score

XX%

## Summary

- Documents audited: X
- Critical issues: X
- High issues: X
- Medium issues: X
- Low issues: X

## Document Status

| Document | Status | Issues |
|---|---|---|
| Functional Description | Current | 0 |
| Infrastructure | Outdated | 2 |
| Technology Stack | Current | 0 |
| Data Flow | Partially Complete | 1 |
| Unit Test Plan | Current | 0 |
| Capacity Planning | Outdated | 3 |

## Critical Findings

- ...

## High Findings

- ...

## Medium Findings

- ...

## Low Findings

- ...

## Documentation Drift

- ...

## Missing Documentation

- ...

## Unsupported Claims

- ...

## Recommended Actions

1. ...
2. ...
3. ...

## Evidence

- ...
```

---

# 18. Pass / Fail Criteria

Return:

```text
PASS
```

when:

- no critical issues exist
- no high-priority documentation drift exists
- mandatory documents exist
- architecture is consistent
- infrastructure is consistent
- capacity information is properly classified

Return:

```text
PASS WITH WARNINGS
```

when:

- no critical issues exist
- medium or low issues exist
- documentation is usable but improvements are recommended

Return:

```text
FAIL
```

when:

- critical issues exist
- major infrastructure mismatch exists
- production architecture is incorrectly documented
- capacity information could lead to an unsafe engineering decision
- mandatory documentation is significantly missing

---

# 19. Read-Only Rule

This skill is an audit skill.

By default:

- DO NOT modify source code.
- DO NOT modify infrastructure.
- DO NOT modify tests.
- DO NOT automatically modify documentation.

Report issues first.

If the user explicitly asks to fix documentation, update only the affected documentation and rerun the audit.

---

# 20. Final Principle

The purpose of this skill is not to determine whether the documentation looks good.

The purpose is to determine whether the documentation is:

```text
Accurate
     +
Traceable
     +
Current
     +
Consistent
     +
Evidence-Based
```

A document that is complete but incorrect MUST be considered worse than a document that explicitly states:

```text
Unknown / Not Defined
```