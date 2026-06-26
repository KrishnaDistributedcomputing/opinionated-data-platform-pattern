# SQL Platform Pattern Work

## Purpose

This page defines the repeatable work pattern for selecting, deploying, migrating, securing, and operating the SQL platform layer that supports the data platform.

## Prerequisites

| Prerequisite | Details Needed | Owner |
| --- | --- | --- |
| Source estate inventory | Server, database, size, version, compatibility level, dependencies, jobs, linked servers | DBA / App Owner |
| Workload profile | CPU, memory, IO, DTU/vCore usage, query concurrency, peak windows, growth | DBA / Platform |
| Target constraints | PaaS preference, SQL compatibility requirements, region, subscription, resource group | Architecture |
| Availability needs | RPO, RTO, HA, DR, zone redundancy, geo-replication, backup retention | Business / Platform |
| Security model | Microsoft Entra auth, SQL auth exceptions, RBAC, audit, encryption, private endpoint needs | Security |
| Network model | VNet, subnet, DNS, firewall rules, private endpoint, source connectivity | Network |
| Licensing | Azure Hybrid Benefit eligibility, existing SQL licenses, reservation assumptions | FinOps / Licensing |
| Migration tooling | DMA/Azure Migrate approach, DMS needs, backup/restore, replication, rollback plan | DBA / Engineering |
| Acceptance criteria | Performance baseline, failover validation, restore validation, cutover window | Product Owner |

## Architecture Diagram

```mermaid
flowchart LR
    Sources[Existing SQL Estate] --> Assess[Assess Compatibility and Sizing]
    Assess --> Select[Select SQL Deployment Pattern]
    Select --> Target[Azure SQL Database / SQL MI / SQL VM]
    Target --> Secure[Apply Identity, Network, and Encryption Controls]
    Secure --> Protect[Configure Backup, HA, DR, and Retention]
    Protect --> Operate[Monitor, Tune, and Optimize Cost]
    Operate --> Consumers[Fabric Pipelines, Applications, and Reports]
```

## Workstreams

| Workstream | Scope | Primary Output |
| --- | --- | --- |
| SQL placement | Choose Azure SQL Database, Azure SQL Managed Instance, SQL Server on Azure VM, or hybrid | SQL deployment decision |
| Migration readiness | Compatibility, dependencies, performance profile, HA/DR needs | Migration assessment |
| Database architecture | Compute tier, storage, backup, retention, HA, DR, scaling | SQL target architecture |
| Security | RBAC, Microsoft Entra authentication, firewall/private endpoints, auditing, encryption | SQL security baseline |
| Operations | Monitoring, maintenance, backup validation, performance tuning, incident response | SQL runbook |
| Cost control | vCore sizing, storage growth, backup retention, reservations, Azure Hybrid Benefit | SQL cost model |

## Required Inputs

- Source SQL estate inventory
- Database size, growth, and transaction profile
- Compatibility and feature dependency assessment
- Availability, RPO, and RTO requirements
- Security, audit, encryption, and network requirements
- Licensing position and Azure Hybrid Benefit eligibility
- Migration window and rollback requirements
- Integration requirements with Fabric, pipelines, and reporting workloads

## Implementation Details Needed

| Area | Detail To Capture | Why It Matters |
| --- | --- | --- |
| Target service | Azure SQL Database, SQL Managed Instance, SQL VM, or hybrid | Determines feature support, operations, and cost model |
| Compute | vCores/DTU, tier, serverless/provisioned, reserved capacity | Drives performance and monthly cost |
| Storage | Data size, log size, tempdb needs, growth rate, max size | Prevents capacity and performance surprises |
| HA/DR | Zone redundancy, failover group, geo-replication, backup retention | Meets production resilience requirements |
| Security | Authentication mode, RBAC, firewall/private endpoint, audit, TDE, Defender | Establishes baseline controls |
| Migration | Method, downtime, validation scripts, rollback plan, cutover owner | Reduces migration risk |
| Operations | Maintenance, index tuning, monitoring alerts, backup restore tests | Makes the service supportable |
| Integration | Fabric pipeline connection, app connection strings, reporting dependencies | Prevents downstream breakage |
| Cost controls | Azure Hybrid Benefit, reservations, budget alerts, right-sizing cadence | Keeps SQL cost visible and optimized |

## Delivery Steps

| Step | Activity | Deliverable |
| --- | --- | --- |
| 1 | Classify SQL workloads and compatibility needs | SQL workload classification |
| 2 | Select target deployment model | SQL platform decision record |
| 3 | Size compute, storage, backup, and HA/DR | SQL sizing model |
| 4 | Design networking and security controls | SQL security architecture |
| 5 | Define migration and validation approach | Migration runbook |
| 6 | Configure monitoring, alerts, backups, and maintenance | Operations baseline |
| 7 | Validate performance, failover, backup restore, and cost | Acceptance evidence |
| 8 | Handover support model and optimization backlog | Operations handover |

## T-Shirt Pattern Work

| Size | Pattern Work |
| --- | --- |
| Small | Azure SQL Database, limited databases, basic backup and monitoring, simple connectivity |
| Medium | Azure SQL Database or SQL Managed Instance, dev/test/prod, private connectivity where required |
| Large | SQL Managed Instance or SQL VM, HA/DR, migration factory, performance tuning, formal support |
| Enterprise | Multi-region, regulated, hybrid, or large estate migration with enterprise operations and governance |

## Decision Rules

| Question | Default Decision |
| --- | --- |
| Is the workload cloud-native and compatible with PaaS? | Use Azure SQL Database |
| Does the workload need broad SQL Server compatibility? | Use Azure SQL Managed Instance |
| Does the workload require unsupported legacy features or OS-level control? | Use SQL Server on Azure VM |
| Is the workload intermittent? | Consider Azure SQL Database serverless |
| Is the workload production critical? | Use provisioned compute, HA/DR, backup validation, and monitoring |

## Acceptance Criteria

- SQL target platform is selected and documented.
- Compute, storage, backup, HA/DR, and licensing assumptions are validated.
- Security and network controls are approved.
- Migration plan includes rollback and validation steps.
- Monitoring, backup restore testing, and operational runbooks are complete.
- Cost model includes compute, storage, backup, HA/DR, licensing, and operations.
