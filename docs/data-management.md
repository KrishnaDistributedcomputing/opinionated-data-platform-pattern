# Data Management Deployment Pattern and Pricing

## Purpose

Data Management provides the governance layer for cataloging, classification, lineage, data quality, retention, compliance, ownership, and access controls across Fabric, SQL, and related data products.

## Recommended Pattern

| Area | Recommendation |
| --- | --- |
| Catalog | Microsoft Purview for catalog and discovery |
| Classification | Mandatory classification for sensitive and regulated data |
| Lineage | Required for production data products and executive reporting |
| Ownership | Named data product owner and technical owner per domain |
| Access | RBAC, Microsoft Entra ID groups, and least privilege |
| Retention | Retention policy by data class and regulatory requirement |
| Quality | Data quality rules for critical datasets and report inputs |
| Audit | Evidence for access, classification, deployments, and policy exceptions |

## T-Shirt Sizing

| Size | Data Management Pattern | Typical Scope | Notes |
| --- | --- | --- | --- |
| Small | Basic naming, ownership, and catalog starter | 1 domain | Lightweight controls for pilot or department use |
| Medium | Purview starter catalog with classification | 1-2 domains | Add lineage, ownership, and access reviews |
| Large | Enterprise catalog and governance framework | 3-5 domains | Add operating model, audit evidence, and policy gates |
| Enterprise | Full governance rollout with federated ownership | 5+ domains | Add chargeback/showback, compliance workflow, and domain onboarding |

## Pricing Components

| Component | Pricing Driver | Notes |
| --- | --- | --- |
| Microsoft Purview | Governance capabilities and usage | Depends on selected Purview capabilities and scale |
| Data map / scanning | Number of sources, scan frequency, and data estate size | Drives catalog and classification effort |
| Data quality | Rule count, execution frequency, and tooling | Include design and operations effort |
| Lineage | Number of pipelines, systems, and data products | Include integration and validation effort |
| Compliance controls | Audit, retention, labels, policy exceptions | Depends on regulatory requirements |
| Operations | Stewardship, access reviews, issue management | Usually a recurring operating cost |

## Pricing Formula

```text
Data Management Monthly Estimate =
  Purview / Governance Platform Cost
+ Scan and Classification Cost
+ Data Quality Cost
+ Lineage and Catalog Operations Cost
+ Stewardship and Compliance Operations Cost
```

## Pricing References

- Microsoft Purview pricing: https://azure.microsoft.com/pricing/details/purview/
- Microsoft Purview documentation: https://learn.microsoft.com/purview/
- Microsoft Purview data governance: https://learn.microsoft.com/purview/data-governance-overview
- Microsoft Purview data map: https://learn.microsoft.com/purview/concept-data-map
- Azure pricing calculator: https://azure.microsoft.com/pricing/calculator/
