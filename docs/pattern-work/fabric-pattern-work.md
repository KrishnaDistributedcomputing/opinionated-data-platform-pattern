# Fabric Pattern Work

## Purpose

This page defines the repeatable work pattern for deploying Microsoft Fabric as part of the opinionated data platform. Use it to move from sizing and pricing into executable delivery work.

## Workstreams

| Workstream | Scope | Primary Output |
| --- | --- | --- |
| Tenant and capacity | Tenant setting review, capacity selection, capacity assignment, capacity monitoring | Fabric capacity and tenant baseline |
| Workspace model | Domain and environment workspace design | Workspace standards and workspace map |
| OneLake and storage | Lakehouse, warehouse, shortcut, retention, and data-zone patterns | OneLake architecture |
| Data engineering | Pipelines, notebooks, orchestration, data validation, and refresh windows | Data ingestion and transformation pattern |
| BI and semantic layer | Semantic models, reports, certification, endorsement, and refresh rules | Governed analytics consumption pattern |
| Security and governance | Entra ID groups, workspace roles, sensitivity labels, access reviews | Fabric security model |
| Deployment and operations | Git integration, deployment pipelines, monitoring, runbooks, rollback | Fabric release and operations model |

## Required Inputs

- Customer profile and T-shirt size
- Business domains and workspace ownership model
- Data source inventory and ingestion frequency
- Data volume, retention, and growth assumptions
- User roles: admins, engineers, report authors, consumers
- Security requirements: sensitivity labels, RLS/OLS, external sharing, audit
- Environment requirements: dev, test, prod, sandbox, DR if required
- Cost target and capacity planning assumptions

## Delivery Steps

| Step | Activity | Deliverable |
| --- | --- | --- |
| 1 | Confirm Fabric tenant settings and admin groups | Tenant settings decision log |
| 2 | Select starting capacity by size and workload | Capacity recommendation |
| 3 | Define domain and environment workspace standards | Workspace naming and ownership standard |
| 4 | Design OneLake, lakehouse, warehouse, and shortcut pattern | Data architecture pattern |
| 5 | Define data pipeline and refresh model | Pipeline orchestration pattern |
| 6 | Define semantic model and report lifecycle | BI delivery standard |
| 7 | Configure Git integration and deployment pipelines | Promotion path |
| 8 | Validate security, performance, monitoring, and cost | Acceptance evidence |
| 9 | Handover runbook and operating model | Operations handover |

## T-Shirt Pattern Work

| Size | Pattern Work |
| --- | --- |
| Small | One domain, basic workspace set, one lakehouse or warehouse, limited reports, basic monitoring |
| Medium | Dev/test/prod workspaces, governed semantic models, repeatable pipelines, Git integration |
| Large | Multi-domain workspace factory, deployment gates, capacity review, formal security and support model |
| Enterprise | Federated domains, chargeback/showback, enterprise governance, formal release and operating model |

## Acceptance Criteria

- Fabric capacity and workspace model are approved.
- Workspace access uses Microsoft Entra ID groups.
- Data products follow the agreed OneLake, lakehouse, warehouse, and semantic model standards.
- Deployment uses approved Git and promotion controls where supported.
- Monitoring, cost review, and operational runbook are in place.
- Production release has business, security, and platform sign-off.
