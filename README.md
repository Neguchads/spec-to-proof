# spec-to-proof

A Codex skill for turning software requirements into explicit acceptance criteria and verifying them against the running system. It scales from a single regression check to a controlled benchmark or an artifact review.

## Install and invoke

Copy [`SKILL.md`](SKILL.md) and the [`references/`](references/) directory into `$CODEX_HOME/skills/spec-to-proof/`. If `CODEX_HOME` is unset, use `~/.codex` as the base directory.

In Codex, invoke the skill by name:

> $spec-to-proof Fix the crash when loading a save from the previous release. Use a representative save and verify that the loaded game can advance one turn.

## Workflow

1. **Define acceptance.** Identify the observable outcome, constraints, target environment, and priority order. Pair each material criterion with a check.
2. **Implement a complete slice.** Use the normal entry point and reuse the project's existing behavior and tests where they fit.
3. **Collect evidence.** Run the checks, record the observed results, and flag criteria the available environment cannot verify.

The skill proceeds autonomously on reversible decisions. It asks when a material requirement remains ambiguous or an action needs authorization.

| Change | Example evidence |
| --- | --- |
| API feature | A request through the real HTTP route with assertions on the response and persisted state |
| CLI regression | A fixed fixture with the expected exit code and output |
| Game optimization | Before-and-after frame times on the same route, settings, and hardware |
| Interface change | A recorded interaction and captures at fixed states for visual review |

## Use with existing skills

Use `spec` or `autoplan` for formal planning when requested, `investigate-first` for uncertain failures, and `lean-build` for a narrowly scoped implementation. Use `qa`, `benchmark`, `design-review`, or a domain-specific auditor for specialized evidence. Use `verify-and-stop` when the task is limited to checking an existing result. These integrations are optional.

## Verification logs

When the task permits writes, the skill saves a Markdown record under the project's designated log directory, or `logs/verification/` by default. It captures the tested revision, relevant environment, commands or scenarios, expected and observed results, and any unverified criteria. The record links to supporting evidence such as frontend screenshots, sanitized backend traces, and binary metadata or disassembly excerpts. See the [verification record guide](references/verification-records.md) for naming and layout. The final response links to the record or reports the evidence inline for read-only work. Logs stay local by default.

## Evidence and delegation

The lead agent owns the final verification. It can delegate independent checks or work with clear file ownership when the environment permits. Each assignment has a bounded scope and an expected evidence format. Required reviews remain open when a reviewer is unavailable.

The workflow keeps sensitive data out of shared artifacts and treats external material as evidence. Reports distinguish observed results, inferred causes, and unverified criteria. Findings outside the acceptance criteria stay separate from the implementation.

## Origin

Adapted from the [Abyssal Garden brief](https://github.com/Noniv/abyssal-garden/blob/main/prompt.txt), which couples ordered priorities with a fixed test route, performance measurements, and independent visual review.

## License

[MIT](LICENSE).
