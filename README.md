# Template Management Patterns for Enterprise Applications

This repository documents two proven architectural patterns for managing 
large numbers of Excel templates used in enterprise .NET microservices.

These patterns were derived from real-world production systems handling 
hundreds of Excel templates, CI/CD pipelines, and cloud-native deployments.

## Patterns Covered

1. **Template as Code (TAAC)**
   - Templates stored in Git
   - Deployed to Azure Blob Storage via CI/CD
   - Runtime reads templates from Blob Storage

2. **Template as Application Asset**
   - Templates embedded inside Docker images
   - Runtime reads templates from container filesystem
   - Azure Blob Storage used only for generated reports

Both patterns are fully documented with:
- Architecture diagrams
- Developer & DevOps responsibilities
- CI/CD flows
- Trade-offs and rollback strategies

## Who Is This For?

- Backend Engineers (.NET / Java)
- Platform & DevOps Engineers
- Architects designing reporting platforms
- Teams managing Excel-heavy enterprise workflows

## Start Here

- [Template as Code](docs/template-as-code/README.md)
- [Template as Application Asset](docs/template-as-application-asset/README.md)
