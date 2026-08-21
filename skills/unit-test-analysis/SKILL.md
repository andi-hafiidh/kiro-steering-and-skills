---
name: unit-test-analysis
description: Menganalisis Unit Test aktual, test coverage, testing gaps, dan memperbarui docs/05-unit-test-plan.md.
---

# Unit Test Analysis Skill

## Tujuan

Menganalisis test implementation aktual dan membuat Unit Test Plan yang sesuai dengan kondisi repository.

Seluruh dokumentasi MUST menggunakan Bahasa Indonesia.

## Prosedur

1. Baca steering documentation standard.
2. Identifikasi testing framework.
3. Temukan seluruh Unit Test.
4. Identifikasi unit/component yang diuji.
5. Identifikasi existing test cases.
6. Identifikasi mock dan fixture.
7. Identifikasi coverage jika tersedia.
8. Identifikasi critical path.
9. Identifikasi missing tests.
10. Klasifikasikan test.
11. Update `docs/05-unit-test-plan.md`.

## Klasifikasi

Gunakan:

```text
Implemented Test
Planned Test
Missing Test
```

Scenario SHOULD mencakup bila relevan:

- Positive
- Negative
- Boundary
- Validation
- Error Handling
- Dependency Failure
- Timeout
- Concurrency
- Authentication
- Authorization

## Prioritas Testing

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

## Coverage

Jika coverage dapat diverifikasi, dokumentasikan actual value.

Jika tidak:

```text
Coverage: Unknown / Not Defined
```

MUST NOT mengarang coverage.

## Output

Update:

```text
docs/05-unit-test-plan.md
```

Laporkan:

- testing framework
- test yang ditemukan
- critical testing gaps
- coverage status
- recommended tests
