# FA Local GNAT Dispatch Target Role

## Status

Target role opened; runtime and schema not promoted.

## Source Authority

The local-system proving repo at
`/home/charlie/Forge/ecosystem/local-systems/fa-local-operator` owns the current
GNAT dispatch contract, validator, and proof.

Current source authority evidence:

- `schemas/gnat-dispatch-envelope.schema.json`
- `tests/gnat_dispatch.rs`
- `src/integrations/cortex/mod.rs`
- `src/bin/fa_local_run.rs`
- `ci_gate.sh`

## Target Role

FA Local app support may receive a future GNAT dispatch promotion only as the
bounded execution-routing side of the Cortex GNAT surface.

The support target role is limited to:

- validating a Cortex-originated `GnatDispatchEnvelope.v1`
- enforcing that FA Local owns execution routing
- clamping effective concurrency to admitted local capability
- making serial fallback explicit when the contract permits it
- denying unsupported worker types, unsupported contract versions, and malformed
  shard plans
- preserving Cortex ownership of source eligibility and receipt validation

## Explicit Non-Goals

This target role does not authorize:

- copying GNAT dispatch runtime code into support in this slice
- copying `gnat-dispatch-envelope.schema.json` into support in this slice
- changing execution service behavior
- adding queue, watcher, retry, or scheduler ownership
- letting Cortex own integrated execution routing
- storing durable GNAT records in FA Local
- emitting semantic labels or candidate meaning

## Promotion Gate

Before any GNAT dispatch file is promoted into app support, the promotion slice
must name:

- exact files to promote
- source proof command
- support proof command
- support service contract or adapter target
- post-promotion drift report
- rollback path

Until that gate exists, GNAT dispatch remains `source_local_hold` in the
promotion ledger.
