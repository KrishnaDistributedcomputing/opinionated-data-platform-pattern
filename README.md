# Opinionated Delivery Pattern: Fabric, SQL, Data Management, and GitHub

**File purpose:** A one-page-to-execution pattern for sizing, pricing, and deploying a modern Microsoft data platform using **Spec-Driven Deployment**, **T-shirt sizing**, and **clear commercial models**.

**Scope:** Microsoft Fabric, Azure SQL / SQL platform, data management controls, and GitHub-based engineering delivery.

## Dedicated Component Pages

- [GitHub delivery pattern and pricing](docs/github.md)
- [Microsoft Fabric deployment pattern and pricing](docs/fabric.md)
- [SQL Platform deployment pattern and pricing](docs/sql-platform.md)
- [Data Management deployment pattern and pricing](docs/data-management.md)

---

## 1. Executive Pattern

The recommended pattern is to treat the data platform as a product, not a one-time infrastructure build.

The platform should be delivered using:

1. **Spec-Driven Deployment**
   - Every environment is defined through version-controlled specifications.
   - Architecture decisions, deployment parameters, security controls, and acceptance criteria are captured before implementation.
   - Infrastructure is generated and deployed from specs using GitHub workflows.

2. **T-shirt Sizing**
   - Customers are mapped to Small, Medium, Large, or Enterprise patterns.
   - Each size has predefined platform scope, deployment complexity, operating model, and pricing assumptions.
   - Sizing can be refined after discovery, but the first estimate should be fast and repeatable.

3. **Clear Pricing Models**
   - Pricing is separated into platform cost, engineering cost, support cost, and optional consumption growth.
   - Customers can understand what is fixed, what is variable, and what triggers a move to the next tier.

---

## 2. Opinionated Reference Architecture

```text
GitHub
 ├── Specs
 ├── Infrastructure-as-Code
 ├── CI/CD Workflows
 ├── Security Scanning
 └── Release Governance

Azure / Microsoft Cloud
 ├── Microsoft Fabric
 │   ├── OneLake
 │   ├── Lakehouse / Warehouse
 │   ├── Data Factory Pipelines
 │   ├── Power BI Semantic Models
 │   └── Capacity SKU
 │
 ├── SQL Platform
 │   ├── Azure SQL Database
 │   ├── Azure SQL Managed Instance
 │   ├── SQL Server on Azure VM, where required
 │   └── Backup / HA / DR
 │
 └── Data Management
   ├── Microsoft Purview
   ├── Data Catalog
   ├── Data Classification
   ├── Data Lineage
   ├── Data Quality Rules
   └── Retention / Compliance Controls
```

---

## 3. Spec-Driven Deployment Model

### 3.1 Required Repository Structure

```text
data-platform-pattern/
├── specs/
│   ├── customer-profile.yaml
│   ├── platform-sizing.yaml
│   ├── fabric-capacity.yaml
│   ├── sql-platform.yaml
│   ├── data-management.yaml
│   ├── security-controls.yaml
│   └── acceptance-criteria.md
│
├── infra/
│   ├── bicep/
│   ├── terraform/
│   └── modules/
│
├── pipelines/
│   ├── validate-specs.yml
│   ├── deploy-dev.yml
│   ├── deploy-test.yml
│   └── deploy-prod.yml
│
├── docs/
│   ├── architecture.md
│   ├── pricing-model.md
│   ├── operating-model.md
│   └── runbook.md
│
└── adr/
    ├── 001-platform-pattern.md
    ├── 002-fabric-capacity-selection.md
    └── 003-sql-deployment-model.md
```

### 3.2 Spec-Driven Workflow

| Step | Activity | Output |
|---|---|---|
| 1 | Customer intake | Customer profile spec |
| 2 | Workload classification | T-shirt size |
| 3 | Platform selection | Fabric + SQL deployment pattern |
| 4 | Security and governance mapping | RBAC, Purview, data classification |
| 5 | Cost model generation | Fixed + variable estimate |
| 6 | IaC deployment | Dev/Test/Prod environments |
| 7 | Validation | Acceptance checklist |
| 8 | Handover | Runbook and operating model |

---

## 4. T-shirt Sizing Model

### 4.1 Sizing Summary

| Size | Best Fit | Data Volume | Users | Fabric Pattern | SQL Pattern | Delivery Complexity |
|---|---|---:|---:|---|---|---|
| Small | Departmental analytics / pilot | < 1 TB | < 50 | F2–F8 | Azure SQL Database | Low |
| Medium | Business-unit platform | 1–10 TB | 50–250 | F16–F32 | Azure SQL DB or SQL MI | Medium |
| Large | Enterprise data platform | 10–50 TB | 250–1,000 | F64–F128 | SQL MI / SQL VM | High |
| Enterprise | Regulated multi-domain platform | 50 TB+ | 1,000+ | F128+ | SQL MI pools / SQL VM / hybrid | Very High |

---

## 5. Opinionated Platform Patterns

### Pattern A — Small: Department Data Product

**Use when:**
- Customer needs a quick analytics platform.
- Data volume is limited.
- Simple SQL source systems.
- Limited governance requirements.

**Recommended services:**
- Microsoft Fabric F2–F8
- Azure SQL Database serverless or provisioned
- GitHub Team or GitHub Enterprise Cloud
- Basic data catalog and naming standards
- Azure Monitor and Cost Management

**Pricing model:**
- Fixed monthly platform baseline
- Low implementation cost
- Minimal support wrapper

**Commercial model:**
```text
Small = Fixed setup fee + monthly platform estimate + optional advisory support
```

---

### Pattern B — Medium: Business Unit Data Platform

**Use when:**
- Customer has multiple data sources.
- Requires repeatable pipelines.
- Needs governed reporting.
- Has departmental or business-unit scale.

**Recommended services:**
- Microsoft Fabric F16–F32
- Azure SQL Database or Azure SQL Managed Instance
- Microsoft Purview starter catalog
- GitHub Enterprise Cloud + Copilot Business
- CI/CD deployment gates
- Dev/Test/Prod separation

**Pricing model:**
- Fixed monthly baseline
- Variable Fabric capacity growth
- SQL compute and storage consumption
- GitHub per-user licensing

**Commercial model:**
```text
Medium = Foundation build + monthly managed platform + per-user GitHub/Copilot cost
```

---

### Pattern C — Large: Enterprise Data Platform

**Use when:**
- Customer has multiple business domains.
- Data estate includes SQL Server, files, APIs, SaaS platforms, and operational systems.
- Requires security, governance, lineage, and environment separation.
- Needs production-grade HA/DR.

**Recommended services:**
- Microsoft Fabric F64–F128
- Azure SQL Managed Instance or SQL Server on Azure VM
- Microsoft Purview enterprise catalog
- Private networking where required
- GitHub Enterprise Cloud
- GitHub Advanced Security
- GitHub Copilot Business or Enterprise
- Azure Monitor, Log Analytics, Key Vault, Policy

**Pricing model:**
- Platform capacity reservation where stable workloads exist
- Separate SQL cost model
- Separate data governance cost model
- Separate engineering and support retainer

**Commercial model:**
```text
Large = Enterprise foundation + capacity-based platform pricing + managed operations
```

---

### Pattern D — Enterprise: Regulated Multi-Domain Platform

**Use when:**
- Customer has multiple domains, legal entities, or regulated workloads.
- Requires full governance, auditability, retention, lineage, and RBAC.
- Needs platform product ownership and formal release governance.
- Requires multi-region, DR, or hybrid SQL patterns.

**Recommended services:**
- Microsoft Fabric F128+
- SQL Managed Instance pools, SQL VM, or hybrid SQL estate
- Microsoft Purview enterprise rollout
- GitHub Enterprise Cloud
- GitHub Advanced Security
- GitHub Copilot Enterprise
- Dedicated platform operations
- Formal FinOps and chargeback model

**Pricing model:**
- Committed capacity baseline
- Consumption-based growth model
- Dedicated support and operations model
- Chargeback or showback by domain

**Commercial model:**
```text
Enterprise = Platform program + landing zone + data governance + managed service + FinOps
```

---

## 6. Clear-Cut Pricing Model

### 6.1 Pricing Components

| Cost Area | Pricing Driver | Fixed or Variable |
|---|---|---|
| Microsoft Fabric | F-SKU capacity size and runtime | Variable / reserved |
| SQL Platform | vCores, storage, backup, HA/DR | Variable |
| Data Management | Purview, cataloging, scanning, governance scope | Variable |
| GitHub | User licenses, Copilot, Advanced Security | Per user |
| Engineering | Discovery, build, migration, automation | Fixed project cost |
| Operations | Monitoring, support, change management | Monthly retainer |
| Security | RBAC, private endpoints, key management, policy | Fixed + variable |
| FinOps | Budgeting, tagging, reporting, optimization | Monthly or included |

---

## 7. Pricing T-shirt Model

> The values below are commercial modelling placeholders. Final pricing must be validated using the Azure Pricing Calculator, GitHub pricing, regional discounts, enterprise agreements, reservations, and actual customer consumption.

| Size | Setup Effort | Monthly Platform Cost | GitHub / Copilot | Support Model | Best Commercial Fit |
|---|---:|---:|---:|---|---|
| Small | 2–4 weeks | Low | Small team | Advisory | Fixed-price pilot |
| Medium | 4–8 weeks | Medium | Department team | Shared support | Fixed + monthly |
| Large | 8–16 weeks | High | Engineering org | Managed support | Program + retainer |
| Enterprise | 16+ weeks | Very High | Enterprise-wide | Dedicated ops | Platform program |

---

## 8. Pricing Formulas

### 8.1 Monthly Platform Estimate

```text
Monthly Platform Cost =
Fabric Capacity Cost
+ SQL Compute Cost
+ SQL Storage / Backup Cost
+ Data Management Cost
+ Monitoring / Logging Cost
+ Security / Networking Cost
+ GitHub Licensing Cost
+ Support Retainer
```

### 8.2 One-Time Delivery Estimate

```text
One-Time Delivery Cost =
Discovery and Assessment
+ Architecture and Design
+ Spec Creation
+ IaC Build
+ Data Migration / Integration
+ Security Configuration
+ Testing and Validation
+ Documentation and Handover
```

### 8.3 Growth Trigger Model

| Trigger | Recommended Action |
|---|---|
| Fabric capacity consistently throttled | Move to next F-SKU or reserve capacity |
| SQL CPU > 70% sustained | Increase vCores or optimize workload |
| Storage growth > 20% per month | Review lifecycle, compression, archiving |
| More than 3 business domains onboarded | Move from Medium to Large pattern |
| Regulated data introduced | Enable full Purview + security controls |
| More than 50 active developers | Standardize GitHub Enterprise + Copilot policy |

---

## 9. Opinionated Defaults

### 9.1 Fabric Defaults

| Area | Default |
|---|---|
| Capacity | Start with smallest practical F-SKU and scale based on telemetry |
| Workspaces | Separate by domain and environment |
| Environments | Dev, Test, Prod |
| Data Storage | OneLake-first |
| BI | Certified semantic models |
| Cost Control | Capacity monitoring, alerts, budget thresholds |

### 9.2 SQL Defaults

| Area | Default |
|---|---|
| New cloud-native workload | Azure SQL Database |
| SQL Server compatibility workload | Azure SQL Managed Instance |
| Legacy or unsupported dependency | SQL Server on Azure VM |
| Intermittent workload | Azure SQL serverless |
| Production workload | Provisioned compute or reserved capacity |
| HA/DR | Business critical or zone redundant where required |

### 9.3 Data Management Defaults

| Area | Default |
|---|---|
| Data catalog | Microsoft Purview |
| Classification | Mandatory for sensitive data |
| Lineage | Required for production data products |
| Ownership | Data product owner per domain |
| Retention | Defined by data class |
| Access | RBAC + least privilege |

### 9.4 GitHub Defaults

| Area | Default |
|---|---|
| Source control | GitHub Enterprise Cloud |
| Deployment | GitHub Actions |
| Security | Branch protection, code scanning, secret scanning |
| AI engineering | GitHub Copilot Business or Enterprise |
| Governance | Pull request approvals and environment gates |
| Specs | YAML + Markdown in repository |

---

## 10. Minimum Viable Spec

```yaml
customer:
  name: Contoso
  industry: Generic
  data_domains:
    - finance
    - operations
  environment_count: 3

sizing:
  tshirt_size: Medium
  expected_data_volume_tb: 5
  active_users: 150
  active_developers: 20

fabric:
  capacity_sku: F32
  workspaces:
    - dev
    - test
    - prod
  onelake_enabled: true

sql:
  deployment_model: Azure SQL Managed Instance
  vcores: 8
  storage_tb: 2
  ha_required: true

data_management:
  purview_enabled: true
  classification_required: true
  lineage_required: true
  retention_policy_required: true

github:
  plan: GitHub Enterprise Cloud
  copilot: Copilot Business
  advanced_security: true
  deployment_gates: true

operations:
  monitoring: Azure Monitor
  cost_management: enabled
  support_model: shared
```

---

## 11. Deployment Gates

| Gate | Requirement |
|---|---|
| Gate 1 | Customer profile completed |
| Gate 2 | T-shirt size approved |
| Gate 3 | Pricing model reviewed |
| Gate 4 | Security controls approved |
| Gate 5 | IaC validation passed |
| Gate 6 | Dev deployment completed |
| Gate 7 | Test validation completed |
| Gate 8 | Production release approved |
| Gate 9 | Runbook and handover completed |

---

## 12. Recommended Delivery Packages

### Package 1 — Rapid Assessment

**Duration:** 1–2 weeks  
**Output:** T-shirt sizing, target pattern, high-level cost estimate

### Package 2 — Platform Foundation

**Duration:** 4–8 weeks  
**Output:** Fabric, SQL, GitHub, governance baseline, CI/CD

### Package 3 — Data Product Buildout

**Duration:** 6–12 weeks  
**Output:** Pipelines, lakehouse/warehouse, semantic models, dashboards

### Package 4 — Enterprise Governance

**Duration:** 8–16 weeks  
**Output:** Purview, lineage, controls, operating model, chargeback/showback

### Package 5 — Managed Optimization

**Duration:** Monthly  
**Output:** FinOps, performance tuning, backlog, support, governance updates

---

## 13. Recommended Decision Rules

| Question | Default Answer |
|---|---|
| Should every customer start with Enterprise architecture? | No. Start with T-shirt sizing. |
| Should Fabric be deployed without cost controls? | No. Capacity monitoring is mandatory. |
| Should SQL always move to PaaS? | Prefer PaaS, but use SQL VM when compatibility requires it. |
| Should GitHub be optional? | No. It is the control plane for specs, code, deployment, and governance. |
| Should pricing be a single blended number? | No. Separate platform, engineering, support, and consumption. |
| Should governance wait until later? | No. Minimum governance starts on day one. |

---

## 14. Source References

- Microsoft Fabric pricing: https://azure.microsoft.com/en-us/pricing/details/microsoft-fabric/
- Microsoft Fabric licensing and capacities: https://learn.microsoft.com/en-us/fabric/enterprise/licenses
- Azure SQL Database pricing: https://azure.microsoft.com/en-us/pricing/details/azure-sql-database/single/
- Azure SQL serverless overview: https://learn.microsoft.com/en-us/azure/azure-sql/database/serverless-tier-overview
- Azure SQL Managed Instance pricing: https://azure.microsoft.com/en-us/pricing/details/azure-sql-managed-instance/single/
- GitHub Copilot plans and pricing: https://github.com/features/copilot/plans
- GitHub Copilot Business / Enterprise pricing update: https://github.blog/news-insights/company-news/github-copilot-is-moving-to-usage-based-billing/
- GitHub Copilot plans documentation: https://docs.github.com/en/copilot/get-started/plans

---

## 15. Bottom Line

This pattern creates a repeatable way to sell, size, deploy, and operate a Microsoft data platform. The key is to avoid open-ended architecture discussions and move customers into a clear delivery lane:

```text
Customer Profile → T-shirt Size → Spec → Price Model → Deployment → Governance → Operations
```

The recommended default is:

```text
Microsoft Fabric + Azure SQL + Microsoft Purview + GitHub Enterprise + Copilot + Spec-Driven Deployment
```
