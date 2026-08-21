---
name: documentation-audit
description: Melakukan audit read-only terhadap dokumentasi engineering dengan membandingkannya terhadap source code, configuration, infrastructure, dependencies, tests, dan capacity evidence.
---

# Documentation Audit Skill

## Tujuan

Menentukan apakah dokumentasi akurat, current, consistent, traceable, dan evidence-based.

Audit bersifat read-only secara default.

## Scope

Audit:

```text
docs/01-functional-description.md
docs/02-infrastructure.md
docs/03-technology-stack.md
docs/04-data-flow.md
docs/05-unit-test-plan.md
docs/06-capacity-planning.md
```

Bandingkan terhadap:

- Source Code
- Configuration
- Environment Variables
- Dependencies
- Docker
- Kubernetes/OpenShift
- Helm
- CI/CD
- Tests
- Database Configuration
- Cache Configuration
- Message Broker Configuration
- External Integrations
- Observability
- Capacity Configuration

## Prosedur

1. Baca steering documentation standard.
2. Verifikasi seluruh mandatory documents.
3. Audit Functional Description.
4. Audit Infrastructure.
5. Audit Environment Variables.
6. Audit Technology Stack.
7. Audit Data Flow dan Mermaid.
8. Audit Unit Test Plan.
9. Audit Capacity Planning.
10. Lakukan cross-document consistency check.
11. Identifikasi unsupported claims.
12. Identifikasi documentation drift.
13. Klasifikasikan severity.
14. Tentukan PASS / PASS WITH WARNINGS / FAIL.
15. Jangan mengubah source code.
16. Jangan mengubah dokumentasi kecuali diminta eksplisit.

## Severity

### Critical
Berpotensi menyebabkan keputusan engineering/operational yang salah.

### High
Mismatch dokumentasi yang signifikan.

### Medium
Informasi belum lengkap tetapi tidak langsung mengganggu operation.

### Low
Naming, formatting, example, atau consistency minor.

## Output

Gunakan format:

```markdown
# Laporan Audit Dokumentasi

## Status Keseluruhan

PASS / PASS WITH WARNINGS / FAIL

## Ringkasan

- Dokumen diaudit: X
- Critical: X
- High: X
- Medium: X
- Low: X

## Status Dokumen

| Dokumen | Status | Jumlah Temuan |
|---|---|---:|
| Deskripsi Fungsional | Current | 0 |
| Infrastruktur | Outdated | 0 |
| Technology Stack | Current | 0 |
| Data Flow | Current | 0 |
| Unit Test Plan | Current | 0 |
| Capacity Planning | Current | 0 |

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

## Evidence

- ...
```

## Result Rules

`PASS` jika tidak ada Critical dan High drift serta mandatory documentation konsisten.

`PASS WITH WARNINGS` jika hanya Medium/Low issue.

`FAIL` jika ada Critical issue, major architecture/infrastructure mismatch, unsafe capacity information, atau mandatory documentation secara signifikan hilang.
