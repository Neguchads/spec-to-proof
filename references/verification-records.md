# Verification records

Honor the repository's designated verification directory. Otherwise use:

```text
logs/verification/
  YYYY-MM-DD-task-slug/
    verification.md
    artifacts/
      C01-viewport-desktop.png
      C02-api-response.json
      C03-symbols.txt
```

Use an ISO date and a lowercase kebab-case slug. Add a short task or run identifier if a directory already belongs to a different task. Create the artifacts directory only when there is evidence to store. Prefix artifact names with the criterion ID and name the scenario or state. Keep links relative to the record. Use stable IDs within the task and update the same record when repeating a check. Preserve material failures and retries with timestamps or attempt numbers.

## Record structure

- **Scope:** task, acceptance criteria, tested commit and relevant worktree changes. Identify the changed files or the tested artifact hash when the commit alone cannot identify what ran. Record environment, tool versions, configuration, and fixture identifiers where they affect reproduction.
- **Architecture:** identify the affected entry point, components, boundaries, and data flow. Name the modules or subsystems actually exercised. Include a short diagram when it clarifies the path.
- **Checks:** ID, criterion, prerequisites, command or scenario, expected result, observed result, status, and artifact links. Use passed, failed, or unverified.
- **Findings:** symptom, reproduction steps, impact, affected component or symbol, and supporting evidence. Mark the root cause as confirmed or suspected. Name the fix and rerun where applicable.
- **Limitations:** missing tools, environments, fixtures, or reviewers and the checks they prevented.

## Evidence by domain

| Domain | Capture when relevant |
| --- | --- |
| Frontend | Screenshot or recording with route, interaction state, viewport, browser, and build. Capture before and after for visual changes. Use a screenshot diff for fixed-state comparisons and a recording for time-dependent behavior. Record console errors or accessibility findings separately. |
| Backend | Service, route or job, HTTP method and status or exit code, sanitized request and response, error class or code, and relevant stack frames. For state changes, record fixture identifiers and assertions on persistence or emitted events. Use a sanitized trace ID when it helps correlate events. |
| Binary, firmware, or recompilation | Artifact name, build or SHA-256, executable format, CPU architecture, bitness, endianness, and tool version. Record relevant sections, symbols, instruction bytes and mnemonics, registers, or structure field offsets and sizes with provenance. Distinguish file offset, RVA, and runtime virtual address. State the load base if needed to reproduce address translation. Mark inferred symbols and reconstructed layouts as such. Prefer an annotated excerpt or metadata over copying the binary or dump. |
| Performance | Workload, configuration, sample count, timing unit, baseline and candidate, and relevant statistics. Capture sanitized raw samples when useful for reproduction. |

Use established names and exact identifiers from the project. Distinguish a defect (behavior), a failure (check result), and an error (runtime or tool signal). Use Markdown for interpretation and a native format for supporting evidence, such as PNG for screenshots, JSON for structured responses, CSV for measurements, and TXT for tool excerpts. Preserve units and numeric bases. Redact sensitive information before saving the record or its artifacts. If an artifact cannot be safely sanitized, record a safe summary and explain the omission.
