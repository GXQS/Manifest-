# PQC Memory Boundaries and Handling Rules

## Objective
Define strict memory constraints for ML-DSA and ML-KEM operations across GXQS components.

## Required Properties
- Constant-time cryptographic operations.
- mlock-protected key material buffers.
- Explicit zeroization on every error and success path.
- No secret material in logs, telemetry, or panic output.

## Runtime Allocation Limits
- Max ML-DSA verify buffer: 128 KiB per verification context.
- Max ML-KEM encapsulation buffer: 64 KiB.
- Max ML-KEM decapsulation buffer: 64 KiB.
- Max concurrent PQC worker contexts per process: `min(cpu_count, 32)`.

## Streaming and Chunking
Payloads over 8 KiB must be verified in bounded chunks.
Each chunk must be authenticated as part of a deterministic transcript.

## Replay and Transcript Binding
Every signed payload must include:
- chain ID
- epoch
- nonce
- domain separator

Missing fields or mismatched domain separators must result in deterministic rejection.
