---
name: data-flow-analysis
description: Menganalisis data flow dan architecture aktual lalu membuat atau memperbarui Mermaid diagram dalam docs/04-data-flow.md.
---

# Data Flow Analysis Skill

## Tujuan

Menganalisis aliran data aktual berdasarkan source code, configuration, dan integration.

Seluruh penjelasan MUST menggunakan Bahasa Indonesia.

## Prosedur

1. Baca steering documentation standard.
2. Identifikasi application entry point.
3. Identifikasi HTTP/gRPC endpoint.
4. Identifikasi middleware/authentication.
5. Trace Handler/Controller → Service/Use Case → Repository.
6. Identifikasi Database.
7. Identifikasi Cache.
8. Identifikasi Message Broker.
9. Identifikasi External Service.
10. Identifikasi Worker/Scheduler.
11. Tentukan synchronous dan asynchronous flow.
12. Generate Mermaid berdasarkan evidence.
13. Validasi setiap component dan connection.
14. Update `docs/04-data-flow.md`.

## Diagram Level

Jika relevan, buat:

### Level 1 — System Context

Menampilkan:

- Client
- Application
- External System
- Database

### Level 2 — Application Flow

Menampilkan:

- API
- Authentication
- Handler
- Service
- Repository
- Cache
- Database

### Level 3 — Detailed Flow

Gunakan hanya untuk business flow penting.

## Rule

MUST NOT menambahkan component yang tidak dapat diverifikasi.

Untuk setiap component penting, identifikasi evidence.

Contoh:

```text
Redis

Evidence:
- REDIS_HOST
- Redis client initialization
- dependency Redis
```

## Output

Update:

```text
docs/04-data-flow.md
```

Laporkan:

- diagram yang dibuat/diubah
- component yang diverifikasi
- unknown architecture
- potential documentation drift
