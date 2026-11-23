# Quick audit

Use this mode for a fast review of an existing system or change. Start with the requested area or the highest-impact changed entry point. Inspect one representative flow and the boundaries it crosses. Review the relevant project rules and runnable checks before deciding what to inspect. Keep product files unchanged unless fixes were requested. Write verification records only when the task permits it.

## Inspect the chosen flow

- **Architecture and organization.** Follow the flow from entry point to the state change or result. Check responsibility, dependency direction, and naming against the project's rules. Compare documentation with the code that actually runs. Where a rule has an automated check, confirm that the scanner found the expected files or cases before accepting a green result.
- **Code and tests.** Look for a concrete failure risk in the path, such as unchecked input, invalid state, swallowed errors, or duplicated rules that can diverge. Verify a representative success and failure path when practical. Prefer existing checks against the mechanism that ships. Confirm discovery and rebuild when stale output could explain a pass.
- **Security.** Inspect the trust boundary touched by the flow. Where relevant, check input validation, authorization, or whether logs expose sensitive data. Prefer safe local rejection checks. Use sanitized fixtures and follow task authorization for live or sensitive systems.
- **Licensing.** Include this check when publishing, redistributing, or adding third-party material. Inspect the declared license, the license file, and applicable third-party notices. Report gaps or conflicts with their sources. MIT is one possible choice for original material when the owner authorizes it. Preserve upstream notices and escalate unclear licensing to the owner.

## Report and stop

Report findings with impact, file or symbol, supporting evidence, and the smallest correction or next check. List the actual scope, executed checks, and anything left unverified. Use the [verification record guide](verification-records.md) when writing a record. If there are no findings, report the scope tested. Escalate to a specialist review when a concrete finding or an explicit request warrants it.

For shareable repositories, write paths, headings, identifiers, and primary documentation in English unless a project convention requires another language. When the user needs important findings or decisions in Brazilian Portuguese, add a short PT-BR summary alongside the English record. Keep canonical evidence and identifiers consistent across languages.
