# Contributing

## Change Requirements
- Keep changes deterministic and auditable.
- Do not introduce ambiguous protocol language.
- Update affected specification files and `versions.json` together when protocol-facing behavior changes.

## Pull Request Checklist
- [ ] Updated relevant files under `spec/`, `protobuf/`, and/or `versions.json`.
- [ ] Preserved compatibility expectations for all GXQS repositories.
- [ ] Confirmed `global-lint.yml` checks pass.
