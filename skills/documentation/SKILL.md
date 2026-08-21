---
name: documentation
description: Menganalisis repository dan membuat atau memperbarui seluruh dokumentasi engineering wajib berdasarkan steering documentation-standard.
---

# Documentation Skill

## Tujuan

Gunakan skill ini untuk membuat atau memperbarui seluruh dokumentasi engineering project.

Seluruh output dokumentasi MUST menggunakan Bahasa Indonesia sesuai steering.

## Input

Gunakan repository aktif sebagai sumber utama.

Optional user arguments dapat menentukan scope, misalnya:

- full
- changed-only
- infrastructure-only
- existing-docs
- release-review

## Prosedur

1. Baca dan patuhi `.kiro/steering/documentation-standard.md`.
2. Lakukan repository discovery.
3. Identifikasi implementation, configuration, infrastructure, dependencies, tests, dan integrations.
4. Periksa keberadaan dokumen wajib.
5. Generate dokumen yang belum ada.
6. Update dokumen yang outdated atau terdampak perubahan.
7. Jangan mengarang informasi.
8. Mask seluruh secret.
9. Pastikan seluruh isi naratif menggunakan Bahasa Indonesia.
10. Jalankan cross-document consistency validation.
11. Jalankan documentation drift check.
12. Laporkan hasil akhir.

## Dokumen Wajib

```text
docs/
├── 01-functional-description.md
├── 02-infrastructure.md
├── 03-technology-stack.md
├── 04-data-flow.md
├── 05-unit-test-plan.md
└── 06-capacity-planning.md
```

## Evidence

Klasifikasikan informasi sebagai:

```text
Measured
Configured
Calculated
Estimated
Unknown / Not Defined
```

## Output Summary

```text
Documentation Analysis

Deskripsi Fungsional: Created / Updated / Current
Infrastruktur: Created / Updated / Current
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

Documentation Drift:
- ...

Validation Required:
- ...
```
