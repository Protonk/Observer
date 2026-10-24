# PolicyWitness unified-log observer — historical archive

This is historical, unmaintained code. It previously provided best-effort
supplementary sandbox-denial observations for PolicyWitness. Neither complete
log delivery nor definitive attribution of a failed operation was guaranteed.
PID, time-window and path matches were candidates, not causal explanations;
missing records did not establish allowance.

The implementation is supplied for inspection, reproduction or independent
adaptation, without an ongoing compatibility commitment. It is not a component
of current PolicyWitness. Current PolicyWitness neither invokes this archive
nor requires it to remain available or compatible.

## Snapshot and provenance

The `source/` directory is the complete tracked PolicyWitness tree at revision
`9e091d9c2134c5a83e58374561177e555ec12fb8`. Its bytes, executable bits and symlinks come directly from `git archive`.
A full snapshot deliberately preserves the connecting equipment, native
protocols, generated contracts, fixtures, build/signing instructions and test
harness together; reviving it does not require reconstructing integration from
commit history. No build outputs, local credentials or untracked evidence are
included. `SOURCE-MANIFEST.json` records SHA-256 for each regular source file
and targets for symlinks, so the snapshot can be checked independently.

`ORIGIN.txt` records the original commit. `AUTHORS.txt` retains author attribution.
The original MIT license (Copyright (c) 2025 Adam Hyland) is retained at `LICENSE`
and `source/LICENSE`; vendored license notices remain at their original paths.
The original README and all former operating instructions are historical
material under `source/`, not promises about current PolicyWitness or macOS.

## Integration map and removal boundary

- Executable: `source/controller/src/bin/sandbox-log-observer.rs`, declared in
  `source/controller/Cargo.toml`, launched `log show` for the requested window.
- Collector: `controller/src/log_capture.rs` supervised subprocesses and pipes,
  monotonic deadlines, output/derived-data bounds and owned process cleanup;
  `log_show.rs` built queries and parsed records. These modules served this
  subsystem exclusively. Other process supervision remains separately owned.
- Controller: `controller/src/sandbox_log.rs` admitted reports and associated
  events with submitted attempts; `run_flow.rs` attached capture and diagnostic
  fields after completing execution. `cli.rs` exposed the two collection flags.
- Wire contract: `docs/contract.json`, `docs/CONTRACT.md`, `docs/PolicyWitness.md`,
  `tests/fixtures/contract/envelope_shape.json`, and `tests/lib/consumer.py`
  preserve envelope 7, observer report 2, and their interpretation. Request 5
  and runner response 23 are independent of collection.
- Integration controls: `controller/src/log_replay_tests.rs`, inline Rust tests,
  `controller/integration/cli_contract.rs`, `tests/lib/log_capture_contract.py`,
  `tests/suites/unit/observer_admission.sh` and the log cases in
  `tests/suites/witness_contract/`. `tests/fixtures/deny_capture/` includes the
  committed logarchive, its checksum manifest and generation sources.
- Build and distribution: `build.sh`, `docs/build.json`, the provenance/artifact
  readers under `tests/lib/`, and `tests/build-evidence.py` preserve compilation,
  bundle placement, signing and evidence inventory, including standalone signing.
- Limits and architecture: `docs/limits.json`, `docs/architecture.json`, their
  generators and rendered accounts document budgets, boundaries and limitations.
- Research: `records/performance/log-observer/` and associated evidence retain
  the cost and delayed-retrieval investigations as historical records.

Paths after the first bullet are relative to `source/`. Worker PID extraction
was located in `sandbox_log.rs` but also supports execution disposition; it is
an independent capability to retain in PolicyWitness. Worker identity, client
execution timestamps, query/attempt ordering, phase handling, sandbox
extensions, fallback compilation, host/worker/validator/issuer supervision,
process observers and worker disposal are not part of the removal boundary.

## Reproduction

Read `source/README.md`, `source/docs/DEPENDENCIES.md`, `source/docs/BUILD.md`
and `source/tests/README.md` for the original toolchain and commands. The
snapshot targeted macOS 26 on Apple Silicon and required local signing and
XPC/log access for live verification. Historical code may no longer build or
operate with later tools or OS releases. There is no new compatibility layer
or standalone adaptation here.
