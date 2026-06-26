# SQL Platform Deployment Pattern and Pricing

## Purpose

The SQL Platform layer supports operational, transactional, migration, compatibility, and curated relational workloads that complement Microsoft Fabric.

## Recommended Pattern

| Workload Type | Default Recommendation |
| --- | --- |
| New cloud-native SQL workload | Azure SQL Database |
| SQL Server compatibility workload | Azure SQL Managed Instance |
| Legacy dependency or unsupported feature | SQL Server on Azure VM |
| Intermittent workload | Azure SQL Database serverless |
| Production critical workload | Provisioned compute, zone redundancy, backups, and DR as required |
| Regulated workload | Private networking, auditing, encryption, RBAC, and key management |

## T-Shirt Sizing

| Size | SQL Pattern | Typical Scope | Notes |
| --- | --- | --- | --- |
| Small | Azure SQL Database serverless or provisioned | 1-3 databases | Simple departmental or pilot workloads |
| Medium | Azure SQL Database or SQL Managed Instance | 3-10 databases or one business unit | Requires HA, backups, monitoring, and cost controls |
| Large | SQL Managed Instance or SQL Server on Azure VM | Multi-domain SQL estate | Requires migration planning, compatibility checks, and DR |
| Enterprise | SQL MI pools, SQL VM, or hybrid SQL estate | Regulated or multi-region platform | Requires enterprise operations and governance |

## Pricing Components

| Component | Pricing Driver | Notes |
| --- | --- | --- |
| Compute | vCores, DTUs, or VM size | Main SQL runtime cost |
| Storage | Allocated data storage | Include growth assumptions |
| Backup storage | Retention and backup size | Longer retention increases cost |
| HA/DR | Zone redundancy, replicas, failover, geo-replication | Required for production resilience |
| Licensing | License included or Azure Hybrid Benefit | Validate customer entitlement |
| Networking and security | Private endpoints, firewall, audit, Defender, Key Vault | Depends on security requirements |
| Operations | Monitoring, tuning, patching, incident response | Include support model |

## Pricing Formula

```text
SQL Monthly Estimate =
  SQL Compute Cost
+ SQL Storage Cost
+ Backup / Retention Cost
+ HA / DR Cost
+ Security / Networking Cost
+ Operations Support Cost
- Azure Hybrid Benefit Savings, if applicable
```

## Pricing References

- Azure SQL Database pricing: https://azure.microsoft.com/pricing/details/azure-sql-database/single/
- Azure SQL Managed Instance pricing: https://azure.microsoft.com/pricing/details/azure-sql-managed-instance/single/
- SQL Server on Azure VM pricing: https://azure.microsoft.com/pricing/details/virtual-machines/sql-server-enterprise/
- Azure SQL serverless overview: https://learn.microsoft.com/azure/azure-sql/database/serverless-tier-overview
- Azure Hybrid Benefit: https://azure.microsoft.com/pricing/hybrid-benefit/
- Azure pricing calculator: https://azure.microsoft.com/pricing/calculator/
