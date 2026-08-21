---
name: capacity-planning
description: Analyze application infrastructure, resource configuration, traffic assumptions, connection pools, data growth, and scaling configuration to produce an evidence-based capacity planning document.
---

# Capacity Planning Analysis Skill

## Purpose

Analyze the application's current capacity characteristics and produce an evidence-based capacity planning document.

The analysis MUST distinguish between configured, measured, estimated, and unknown values.

---

# 1. Infrastructure Discovery

Inspect:

- Dockerfile
- Docker Compose
- Kubernetes manifests
- Helm charts
- resource requests
- resource limits
- replica configuration
- HPA
- VPA
- node configuration
- environment variables
- application configuration

---

# 2. Application Resource Configuration

Identify:

- CPU request
- CPU limit
- memory request
- memory limit
- replica count
- autoscaling configuration

Example:

```text
CPU Request: 500m
CPU Limit: 1
Memory Request: 512Mi
Memory Limit: 1Gi
Replicas: 3
```

Classify these as:

```text
Configured
```

---

# 3. Connection Pool Analysis

Inspect application configuration for:

- maximum database connections
- minimum idle connections
- maximum idle connections
- connection lifetime
- connection idle lifetime
- Redis connections
- HTTP connection pools
- Kafka connections

For example:

```text
DB Max Open Connections = 50
Replicas = 3

Potential Maximum Connections =
50 × 3 = 150
```

Clearly label this as a calculated capacity.

---

# 4. Traffic Analysis

Look for actual traffic metrics from:

- load test results
- monitoring
- APM
- logs
- metrics
- production reports

Identify:

- RPS
- requests/day
- peak RPS
- average RPS
- concurrent users
- p50 latency
- p95 latency
- p99 latency

If unavailable:

```text
Unknown / Not Defined
```

---

# 5. Data Volume Analysis

Identify:

- records/day
- average record size
- database size
- storage size
- growth rate
- retention period

Calculate when sufficient information exists:

```text
Daily Storage Growth =
Records Per Day × Average Record Size
```

and:

```text
Annual Storage Growth =
Daily Storage Growth × 365
```

---

# 6. Database Capacity

Analyze:

- database type
- connection pool
- query patterns
- indexes
- storage
- replication
- read/write pattern

Identify potential bottlenecks.

---

# 7. Cache Capacity

If Redis or another cache exists, analyze:

- maximum clients
- connection pool
- memory
- TTL
- eviction policy
- expected key volume

Do not assume cache capacity without evidence.

---

# 8. Message Broker Capacity

If Kafka or another message broker exists, analyze:

- producer rate
- consumer rate
- partitions
- consumer count
- message size
- retention
- lag

If unavailable, mark as:

```text
Unknown / Not Defined
```

---

# 9. Scaling Analysis

Determine whether the application supports:

```text
Horizontal Scaling
Vertical Scaling
Autoscaling
Manual Scaling
```

Inspect:

- Kubernetes replicas
- HPA
- statelessness
- shared storage
- session management
- cache dependency
- database bottlenecks

---

# 10. Capacity Calculation

When data is available calculate:

## RPS

```text
RPS = Total Requests / Total Seconds
```

## Daily Requests

```text
Daily Requests = Average RPS × 86,400
```

## Connection Capacity

```text
Total DB Connections =
Replicas × DB Connections Per Replica
```

## Storage Growth

```text
Daily Storage Growth =
Records Per Day × Average Record Size
```

## Required Capacity

Use:

```text
Required Capacity =
Expected Load × Safety Factor
```

The safety factor MUST be explicitly stated.

---

# 11. Bottleneck Analysis

Identify potential bottlenecks in:

```text
Client
 ↓
Load Balancer
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

For each bottleneck describe:

- component
- evidence
- current capacity
- potential failure mode
- recommendation

---

# 12. Capacity Scenario

Where sufficient information exists, create scenarios:

| Scenario | Traffic | CPU | Memory | Replicas |
|---|---:|---:|---:|---:|
| Normal | X RPS | X | X | X |
| Peak | X RPS | X | X | X |
| Growth | X RPS | X | X | X |

Do not invent values.

Use `Unknown` or `Estimated` when necessary.

---

# 13. Capacity Threshold

Identify potential thresholds such as:

```text
CPU > 80%
Memory > 80%
DB Connections > 80%
Redis Clients > 80%
Kafka Consumer Lag increasing
p95 latency increasing
Error rate increasing
Storage > 80%
```

These thresholds are engineering guidelines unless explicitly configured by the project.

Mark them as:

```text
Recommended Threshold
```

rather than claiming they are actual production thresholds.

---

# 14. Capacity Validation Plan

If production measurements are unavailable, create a validation plan.

The plan SHOULD include:

1. Baseline test
2. Load test
3. Stress test
4. Spike test
5. Soak test
6. Resource monitoring
7. Database monitoring
8. Connection monitoring
9. Latency monitoring
10. Failure threshold identification

Measure:

```text
RPS
p50 latency
p95 latency
p99 latency
CPU
Memory
DB connections
DB CPU
Cache utilization
Network
Error rate
```

---

# 15. Output

Update:

```text
docs/06-capacity-planning.md
```

The document MUST clearly classify each value as:

```text
Measured
Configured
Calculated
Estimated
Unknown
```

Include:

- current capacity
- target capacity
- bottleneck
- scaling strategy
- resource recommendation
- growth projection
- validation plan

---

# 16. Final Analysis

At the end report:

```text
Capacity Planning Summary

Current Capacity:
- ...

Configured Resources:
- ...

Measured Performance:
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

Never present assumptions as production measurements.