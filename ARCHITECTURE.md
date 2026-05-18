# GXQS Manifest Architecture

This repository is the source of truth for cross-repository protocol alignment in the GXQS ecosystem.

## Responsibility Boundaries

1. **Global Prompt Anchor**
   - `system-alignment-god-prompt.txt` defines non-negotiable implementation and security constraints for agents and contributors.

2. **Canonical Serialization**
   - `protobuf/v1/quantum_api.proto` defines shared message contracts consumed by downstream repositories.

3. **Normative Specifications**
   - `spec/` contains consensus, gas, and PQC memory requirements referenced by implementation repositories.

4. **Version Coordination**
   - `versions.json` pins module versions to prevent drift.

5. **Automated Drift Detection**
   - `.github/workflows/global-lint.yml` validates required manifest artifacts on each change.
