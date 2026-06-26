# Data Management Pattern Work

## Purpose

This page defines the repeatable work pattern for implementing data management controls across Fabric, SQL, and related data products.

## Workstreams

| Workstream | Scope | Primary Output |
| --- | --- | --- |
| Governance model | Domains, ownership, stewardship, decision rights, operating cadence | Data governance model |
| Catalog and discovery | Microsoft Purview catalog, source registration, scanning, metadata | Catalog baseline |
| Classification | Sensitivity labels, data classes, regulated data mapping | Classification standard |
| Lineage | Pipeline, dataset, report, and source lineage | Lineage model |
| Data quality | Rules, thresholds, issue management, ownership | Data quality framework |
| Retention and compliance | Retention by data class, audit evidence, policy exceptions | Compliance control set |
| Access governance | RBAC, Entra ID groups, access reviews, least privilege | Access control model |

## Required Inputs

- Business domains and data product ownership
- Data source inventory and critical data elements
- Regulatory, privacy, retention, and audit requirements
- Sensitivity label and classification requirements
- Existing catalog, glossary, lineage, and quality processes
- Access model and Microsoft Entra ID group strategy
- Reporting and executive data-product scope
- Operating model for stewards, platform team, and domain owners

## Delivery Steps

| Step | Activity | Deliverable |
| --- | --- | --- |
| 1 | Define data domains, owners, and stewardship roles | Governance RACI |
| 2 | Define classification and sensitivity model | Data classification standard |
| 3 | Register priority sources and data products in catalog | Catalog baseline |
| 4 | Configure scan and metadata collection pattern | Scan schedule and source map |
| 5 | Define lineage requirements for production data products | Lineage requirements |
| 6 | Define data quality rules and issue workflow | Data quality rulebook |
| 7 | Define retention, audit, and access review controls | Compliance control matrix |
| 8 | Validate governance controls during release gates | Governance acceptance evidence |
| 9 | Handover stewardship and operating cadence | Governance operating model |

## T-Shirt Pattern Work

| Size | Pattern Work |
| --- | --- |
| Small | Basic ownership, naming, catalog starter, simple classification |
| Medium | Purview starter catalog, source scans, sensitivity labels, access reviews |
| Large | Multi-domain governance, lineage, data quality rules, compliance evidence |
| Enterprise | Federated stewardship, regulated-data controls, formal issue management, chargeback/showback alignment |

## Control Checklist

- Every production data product has a business owner and technical owner.
- Sensitive data is classified before production use.
- Production lineage is available for critical reports and data products.
- Access is granted through Microsoft Entra ID groups and reviewed regularly.
- Retention and audit requirements are mapped to data classes.
- Data quality issues have owners, severity, and remediation workflow.
- Governance controls are part of deployment gates, not after-the-fact cleanup.

## Acceptance Criteria

- Governance model and ownership are approved.
- Catalog and classification baseline is implemented for in-scope data products.
- Lineage and quality controls are implemented for critical production paths.
- Retention, audit, and access review controls are documented.
- Stewardship cadence and operating model are active.
