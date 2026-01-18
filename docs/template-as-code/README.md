# Template as Code (TAAC)

## Overview

**Template as Code (TAAC)** is an architectural pattern where Excel templates are treated as
**version-controlled configuration artifacts**.

Templates are:
- Stored in GitHub
- Reviewed via Pull Requests
- Validated through CI/CD
- Deployed automatically to Azure Blob Storage

At runtime, .NET microservices load templates directly from Blob Storage and generate reports.

---

## When Should You Use This Pattern?

This pattern is ideal when:

- You manage a large number of Excel templates (100s)
- Templates change **infrequently**
- Template-only fixes should **not require service redeployment**
- Multiple services consume the same templates
- Operations teams want fast rollback without redeploy

---

## Architecture Summary

**Key characteristics:**
- GitHub is the source of truth
- Azure Blob Storage is the runtime store
- CI/CD synchronizes templates (add / update / delete)
- Microservices always read the latest template

![Template as Code Architecture](TemplateAsCode.png)

---

## Developer Responsibilities

- Modify templates only inside the Git repository
- Follow naming and structural conventions
- Validate templates locally before commit
- Submit changes via Pull Requests

Developers **must never** edit templates directly in Azure Blob Storage.

---

## DevOps Responsibilities

- Maintain GitHub Actions pipelines
- Secure Azure Blob access
- Enable Blob soft delete
- Control environment-specific deployments

---

## CI/CD Flow

1. Template change committed to GitHub
2. PR reviewed and approved
3. CI/CD pipeline triggered
4. Templates validated (Aspose / .NET)
5. Azure Blob Storage synchronized
6. Runtime services immediately use updated templates

---

## Runtime Behavior

- Templates are read from Blob Storage
- Reports are written back to Blob Storage
- No application redeploy required for template changes

---

## Rollback Strategy

Rollback is achieved by:
1. Reverting the Git commit
2. Re-running the pipeline
3. Restoring the previous template version from Blob

Typical rollback time: **minutes**

---

## Trade-offs

### Advantages
- No redeploys for template changes
- Fast rollback
- Strong auditability
- Clean separation of concerns

### Disadvantages
- External runtime dependency on Blob Storage
- Requires robust CI/CD discipline

---

## Full Design Document

📄 **Detailed technical document:**  
`Template_as_Code_TAAC.pdf`

---

## Pattern Classification

This approach aligns with:
> **Configuration as Code / Template as Code**
