# Security Policy

## Scope
Security issues in this repository include:
- protocol drift risks caused by manifest changes,
- malformed serialization schema updates,
- version matrix tampering,
- unsafe or ambiguous specification edits.

## Reporting
Please report vulnerabilities privately to the GXQS maintainers through your standard responsible disclosure channel.

## Security Controls in this Repository
- Required-file validation in CI (`.github/workflows/global-lint.yml`).
- Schema and version-matrix structural validation.
- Canonical prompt/spec anchoring to reduce cross-repository inconsistency.
