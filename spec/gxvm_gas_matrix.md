# GXVM Gas Matrix

## Deterministic Metering Principles
- All opcodes are metered before execution.
- Metering uses integer arithmetic only.
- No floating point operations are allowed.

## Memory Expansion Formula
For memory growth from `m_prev` to `m_new` words (`m_new >= m_prev`), where one word is exactly 32 bytes:

`mem_cost(m) = G_memory * m + ((m * m) / Q_memory)` using integer division with truncation toward zero.

Expansion charge:

`delta_mem_cost = mem_cost(m_new) - mem_cost(m_prev)`

Constants:
- `G_memory = 3`
- `Q_memory = 512`

## Cold/Warm Access Pricing
- First access in transaction context: cold cost
- Subsequent accesses: warm cost

| Access type | Cold | Warm |
| --- | ---: | ---: |
| Account read | 2600 | 100 |
| Storage read | 2100 | 100 |
| Storage write (non-zero change) | 5000 | 5000 |

## PQC Verification Weighting
ML-DSA verification is charged by payload size buckets to mitigate DoS via oversized signatures.

| Payload bytes | Gas |
| ---: | ---: |
| 0 - 4096 | 50_000 |
| 4097 - 16384 | 90_000 |
| >16384 | reject transaction with `ERR_PQC_PAYLOAD_TOO_LARGE` |
