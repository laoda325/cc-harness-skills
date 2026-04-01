# Release Plan

## Recommended Public Identity

- Repo name: `cc-harness-skills`
- GitHub subtitle: `Portable agent skills inspired by the public CC codebase patterns.`
- One-line pitch: `Memory, verification, coordination, compression, and proactive-agent skills for Claude Code, Codex, and OpenClaw.`
- GitHub release title: `v0.1.0: First Portable CC Harness Skills`

## Recommended GitHub Topics

- `ai-agent`
- `coding-agent`
- `agent-harness`
- `agent-memory`
- `multi-agent`
- `prompt-engineering`
- `context-compression`
- `developer-tools`
- `codex`
- `openclaw`

## Publish Order

Release order for the first batch:

1. `dream-memory`
2. `memory-extractor`
3. `structured-context-compressor`
4. `verification-gate`
5. `swarm-coordinator`
6. `kairos-lite`

Suggested first public tag:

- `v0.1.0`

## GitHub Release Copy

### Repo Intro

`CC Harness Skills` packages six portable skills extracted from a publicly mirrored `CC` agent codebase and rewritten for `Claude Code`, `Codex`, and `OpenClaw`. Each bundle ships with a host-agnostic `SKILL.md`, a prompt template, source notes, and a small helper script.

### v0.1.0 Release Notes

First public release of the `CC Harness Skills` pack.

Included in `v0.1.0`:

- `CC Dream Memory`
- `CC Memory Extractor`
- `CC Context Compressor`
- `CC Verification Gate`
- `CC Swarm Coordinator`
- `CC Kairos Lite`

This release focuses on portable prompts and scripts, not host-specific runtime hooks. The goal is to make the patterns usable across major coding-agent hosts before adding deeper platform integrations.

Recommended short repo description:

`Portable CC-inspired skills for memory, verification, multi-agent coordination, context compression, and proactive coding-agent workflows.`

## ClawHub Listing Copy

### `dream-memory`

`Consolidate recent sessions, logs, and topic memories into a short durable memory index without storing stale code facts.`

### `memory-extractor`

`Extract durable user, feedback, project, and reference memories from recent turns while avoiding fragile code-state details.`

### `structured-context-compressor`

`Compress a long coding session into a nine-part continuation summary that preserves request, files, errors, user messages, and the next step.`

### `verification-gate`

`Run a read-only verification pass after implementation so verified, unverified, and failed work are clearly separated.`

### `swarm-coordinator`

`Coordinate multiple agents through research, synthesis, implementation, and verification with bounded worker ownership.`

### `kairos-lite`

`Add lightweight proactive jobs with schedule, sleep, brief, and expiry rules without committing to a full daemon platform.`

## Release Checklist

1. Run `bash ./skills/check_all.sh`.
2. Confirm the latest smoke-test report in [TEST_REPORT.md](/Users/carl/Downloads/codegod/skills/TEST_REPORT.md).
3. Publish `v0.1.0` to GitHub.
4. Publish to ClawHub in the listed order.
5. Reuse the one-line listing copy above for each skill page.
