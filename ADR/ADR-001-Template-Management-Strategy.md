# ADR-001: Template Management Strategy

## Context
Client requiurement is manage 400+ Excel templates used by .NET microservices.

## Options Considered
1. Template as Code (Blob-based)
2. Template as Application Asset (Docker-based)

## Decision
Both patterns are valid and documented.
Choice depends on operational priorities.

## Consequences
- Docker approach increases redeploy frequency
- Blob approach increases infra dependency
