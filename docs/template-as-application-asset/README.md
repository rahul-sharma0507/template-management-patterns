# Template as Application Asset (Docker Embedded)

## Overview
Templates are embedded directly into Docker images and treated as 
application assets.

Azure Blob Storage is used only for generated reports.

## When to Use
- Strong coupling between code and templates
- Immutable runtime environments
- Willingness to redeploy for template changes

## Architecture
![Architecture](TemplateAsAsset.png)

## Detailed Design
See full document:
- Template_as_Application_Asset.pdf
