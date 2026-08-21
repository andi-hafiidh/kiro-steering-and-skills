---
name: capacity-planning
description: Menganalisis resource, traffic, connection pool, storage, database, cache, message broker, scaling, dan bottleneck untuk memperbarui docs/06-capacity-planning.md.
---

# Capacity Planning Skill

## Tujuan

Menghasilkan Capacity Planning berbasis evidence, bukan asumsi tanpa label.

Seluruh penjelasan MUST menggunakan Bahasa Indonesia.

## Prosedur

1. Baca steering documentation standard.
2. Inspect container/deployment configuration.
3. Identifikasi CPU request/limit.
4. Identifikasi memory request/limit.
5. Identifikasi replica count.
6. Identifikasi HPA/VPA.
7. Identifikasi DB connection pool.
8. Identifikasi Redis/cache connection.
9. Identifikasi Kafka/message broker configuration.
10. Cari load test/monitoring/APM metrics jika tersedia.
11. Analisis storage growth jika data tersedia.
12. Analisis scaling capability.
13. Analisis bottleneck.
14. Hitung capacity jika input cukup.
15. Klasifikasikan seluruh value.
16. Update `docs/06-capacity-planning.md`.

## Evidence Classification

Gunakan:

```text
Measured
Configured
Calculated
Estimated
Unknown / Not Defined
```

## Calculation

Jika data tersedia:

```text
RPS = Total Requests / Total Seconds
```

```text
Daily Requests = Average RPS × 86,400
```

```text
Total DB Connections =
Application Replicas × DB Connections Per Replica
```

```text
Daily Storage Growth =
Records Per Day × Average Record Size
```

```text
Annual Storage Growth =
Daily Storage Growth × 365
```

```text
Required Capacity =
Expected Load × Safety Factor
```

Safety factor MUST dijelaskan.

## Bottleneck

Analisis bila applicable:

```text
Client
   ↓
Load Balancer / Ingress
   ↓
Application
   ↓
Connection Pool
   ↓
Cache
   ↓
Database
   ↓
External Services
```

## Validation Plan

Jika production metrics tidak tersedia, buat:

- Baseline Test
- Load Test
- Stress Test
- Spike Test
- Soak Test

Measure bila applicable:

- RPS
- p50
- p95
- p99
- CPU
- Memory
- DB CPU
- DB Connections
- Cache Utilization
- Kafka Consumer Lag
- Error Rate
- Network
- Storage

## Output

Update:

```text
docs/06-capacity-planning.md
```

Laporkan:

```text
Capacity Planning Summary

Current Capacity:
- ...

Configured Resources:
- ...

Measured Performance:
- ...

Calculated Capacity:
- ...

Estimated Capacity:
- ...

Potential Bottlenecks:
- ...

Scaling Recommendation:
- ...

Missing Metrics:
- ...

Validation Required:
- ...
```
