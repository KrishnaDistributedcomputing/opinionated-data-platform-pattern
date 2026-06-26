# GitHub Delivery Pattern and Pricing

## Purpose

GitHub is the engineering control plane for the data platform. It stores deployment specs, infrastructure code, workflow automation, pull request approvals, security checks, and release evidence.

## Recommended Pattern

| Area | Recommendation |
| --- | --- |
| Source control | GitHub Enterprise Cloud for customer-facing or enterprise delivery |
| Specs | YAML and Markdown specs stored in version control |
| CI/CD | GitHub Actions with environment gates for dev, test, and prod |
| Security | Branch protection, required reviews, secret scanning, code scanning, dependency review |
| AI engineering | GitHub Copilot Business or Enterprise based on customer governance needs |
| Release governance | Pull requests, approvals, environment protection rules, release notes |

## T-Shirt Sizing

| Size | GitHub Pattern | Typical Users | Security Pattern |
| --- | --- | ---: | --- |
| Small | Team repository with basic branch protection | 2-10 | Secret scanning and required reviews |
| Medium | Department repositories with reusable workflows | 10-50 | Code scanning, environment gates, required reviewers |
| Large | Organization-level standards and shared workflow templates | 50-250 | Advanced Security, policy-driven reviews, audit requirements |
| Enterprise | Enterprise account standards and federated platform teams | 250+ | Enterprise governance, audit, Advanced Security, Copilot policy |

## Pricing Components

| Component | Pricing Driver | Notes |
| --- | --- | --- |
| GitHub Enterprise Cloud | Licensed users | Required for enterprise governance and organization controls |
| GitHub Copilot Business | Licensed Copilot users | Best fit for team and business-unit delivery |
| GitHub Copilot Enterprise | Licensed Copilot users | Best fit for enterprise knowledge, policy, and governance scenarios |
| GitHub Advanced Security | Licensed active committers | Consider for code scanning, secret scanning, and dependency protection at scale |
| GitHub Actions | Included minutes plus additional usage | Private repo usage and larger runners may add cost |
| Storage and packages | Usage-based | Depends on artifacts, packages, and retention |

## Pricing Formula

```text
GitHub Monthly Estimate =
  GitHub Plan Licenses
+ Copilot Licenses
+ Advanced Security Licenses
+ GitHub Actions Overage
+ Storage / Package Overage
```

## Pricing References

- GitHub pricing: https://github.com/pricing
- GitHub Copilot plans: https://github.com/features/copilot/plans
- GitHub Advanced Security billing: https://docs.github.com/en/billing/managing-billing-for-your-products/managing-billing-for-github-advanced-security
- GitHub Actions billing: https://docs.github.com/en/billing/managing-billing-for-your-products/managing-billing-for-github-actions
