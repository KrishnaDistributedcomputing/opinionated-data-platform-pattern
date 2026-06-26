# SQL Platform Pattern Work

## Purpose

This page defines the repeatable work pattern for selecting, deploying, migrating, securing, and operating the SQL platform layer that supports the data platform.

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
