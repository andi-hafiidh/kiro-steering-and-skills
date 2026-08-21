---
name: documentation
description: Analyze a software repository and create or update standardized engineering documentation based on the project's source code, configuration, infrastructure, tests, dependencies, and environment variables.
---

# Documentation Analysis Skill

## Purpose

Analyze the current repository and generate or update engineering documentation according to the project's documentation steering standard.

The goal is to produce documentation that accurately represents the current implementation.

Do not invent information.

---

# 1. When to Use

Use this skill when:

- creating documentation for a new project
- documenting an existing project
- updating documentation after implementation changes
- performing documentation audit
- detecting documentation drift
- preparing a project for handover
- preparing technical documentation for review

---

# 2. Repository Discovery

Before generating documentation, inspect the repository.

Identify:

- programming language
- application framework
- project structure
- API endpoints
- database
- cache
- message broker
- external services
- environment variables
- infrastructure
- deployment configuration
- CI/CD
- tests
- observability
- storage

Inspect relevant files such as:

```text
README.md
.env
.env.example
Dockerfile
docker-compose.yml
Makefile
go.mod
package.json
requirements.txt
pom.xml
Jenkinsfile
deployment/
k8s/
helm/
terraform/
src/
cmd/
internal/
pkg/
tests/
```

Only inspect files that exist.

---

# 3. Documentation Assessment

Determine whether the following documents exist:

```text
docs/01-functional-description.md
docs/02-infrastructure.md
docs/03-technology-stack.md
docs/04-data-flow.md
docs/05-unit-test-plan.md
docs/06-capacity-planning.md
```

For each document determine:

```text
Exists
Missing
Outdated
Partially Complete
Current
```

---

# 4. Generate Documentation

Create missing documentation.

Update outdated documentation.

Do not rewrite documentation that is already accurate unless necessary.

Maintain the existing documentation style when possible.

---

# 5. Evidence Classification

Every significant piece of information should be classified as:

```text
Implemented
Configured
Measured
Estimated
Unknown
```

Examples:

```text
Go version:
Configured

CPU limit:
Configured

Production RPS:
Measured

Expected growth:
Estimated

Business requirement:
Unknown
```

---

# 6. Cross-Document Consistency

After generating documentation, compare the documents against each other.

Verify:

- technology stack matches infrastructure
- infrastructure matches environment variables
- data flow matches architecture
- unit test plan matches actual tests
- capacity planning matches infrastructure configuration
- external services are consistently documented
- database dependencies are consistently documented

---

# 7. Documentation Drift

Detect:

- obsolete components
- removed environment variables
- unused dependencies
- undocumented dependencies
- missing infrastructure
- outdated API documentation
- outdated Mermaid diagrams
- missing tests
- outdated capacity assumptions

Correct documentation when the actual implementation can be determined.

---

# 8. Sensitive Information

Never document:

- passwords
- API keys
- tokens
- private keys
- credentials
- secrets
- connection strings containing credentials

Replace sensitive values with:

```text
<REDACTED>
```

---

# 9. Final Validation

Before completing the task:

1. Verify all required documents exist.
2. Verify documents represent current implementation.
3. Verify Mermaid diagrams.
4. Verify environment variables.
5. Verify dependencies.
6. Verify tests.
7. Verify infrastructure.
8. Verify capacity assumptions.
9. Verify no secrets are exposed.

---

# 10. Output

After completing the documentation, report:

```text
Documentation Analysis

Functional Description: Created / Updated / Current
Infrastructure: Created / Updated / Current
Technology Stack: Created / Updated / Current
Data Flow: Created / Updated / Current
Unit Test Plan: Created / Updated / Current
Capacity Planning: Created / Updated / Current

Documentation Gaps:
- ...

Assumptions:
- ...

Unknown Information:
- ...

Potential Drift:
- ...
```