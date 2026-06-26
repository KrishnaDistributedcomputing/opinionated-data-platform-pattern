# Microsoft Fabric Deployment Pattern and Pricing

## Purpose

Microsoft Fabric provides the analytics platform layer for OneLake, lakehouse, warehouse, Data Factory pipelines, semantic models, and Power BI reporting.

## Recommended Pattern

| Area | Recommendation |
| --- | --- |
| Storage | OneLake-first design with shortcuts where they reduce duplicate data |
| Workspaces | Separate by domain and environment |
| Environments | Dev, test, and prod for governed workloads |
| Deployment | Fabric Git integration and deployment pipelines where supported |
| Capacity | Start with the smallest practical F-SKU and scale using telemetry |
| Governance | Sensitivity labels, workspace ownership, endorsement, lineage, and access reviews |
| Operations | Capacity metrics, refresh monitoring, pipeline monitoring, and budget alerts |

## T-Shirt Sizing

| Size | Fabric Pattern | Typical Capacity Planning Start | Notes |
| --- | --- | --- | --- |
| Small | Department pilot or single data product | F2-F8 | Validate feature fit and usage pattern |
| Medium | Business-unit platform | F16-F32 | Separate dev/test/prod and measure concurrency |
| Large | Enterprise data platform | F64-F128 | Use capacity metrics, workload segmentation, and release gates |
| Enterprise | Regulated multi-domain platform | F128+ | Use enterprise governance, chargeback/showback, and operating model |

## Pricing Components

| Component | Pricing Driver | Notes |
| --- | --- | --- |
| Fabric capacity | F-SKU size and runtime hours | Primary platform cost driver |
| Reservation | Reserved capacity commitment | Consider when workloads are stable |
| Power BI licensing | User licensing where required | Depends on user roles and capacity model |
| OneLake storage | Stored data volume | Include raw, curated, retained, and duplicated data |
| Data movement and engineering | Pipeline and compute usage | Validate with PoC telemetry |
| Monitoring and operations | Support and operational tooling | Include runbooks, alerts, and platform support |

## Pricing Formula

```text
Fabric Monthly Estimate =
  Fabric Capacity Cost
+ Power BI Licensing Cost
+ OneLake Storage Cost
+ Data Movement / Engineering Cost
+ Monitoring and Operations Cost
```

## Pricing References

- Microsoft Fabric pricing: https://azure.microsoft.com/pricing/details/microsoft-fabric/
- Microsoft Fabric licenses and capacities: https://learn.microsoft.com/fabric/enterprise/licenses
- Microsoft Fabric capacity metrics app: https://learn.microsoft.com/fabric/enterprise/metrics-app
- Azure pricing calculator: https://azure.microsoft.com/pricing/calculator/
