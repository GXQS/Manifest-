# GXQS Manifest

Central manifest repository for GXQS protocol alignment and cross-repository drift prevention.

## Repository layout

- `.github/workflows/global-lint.yml`: protocol drift verification workflow.
- `system-alignment-god-prompt.txt`: authoritative master prompt used for agent/runtime alignment.
- `versions.json`: hard-pinned module version matrix.
- `protobuf/v1/quantum_api.proto`: canonical serialization contract for shared transaction and block structures.
- `spec/`: normative protocol documents for consensus, GXVM gas rules, and PQC memory bounds.
