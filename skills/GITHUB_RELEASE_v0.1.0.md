# v0.1.0: First Portable CC Harness Skills

First public release of `CC Harness Skills`.

This repo packages six portable skills extracted from a publicly mirrored `CC` coding-agent codebase and rewritten so they can be installed in `Claude Code`, `Codex`, and `OpenClaw` without relying on private runtime internals.

Included in `v0.1.0`:

- `CC Dream Memory`
- `CC Memory Extractor`
- `CC Context Compressor`
- `CC Verification Gate`
- `CC Swarm Coordinator`
- `CC Kairos Lite`

What ships in each bundle:

- portable `SKILL.md`
- source-derived prompt template
- source notes
- host-agnostic helper script

Smoke-test status for this release:

- `Claude Code`: verified locally for all six skills
- `OpenClaw`: verified locally for all six skills
- `Codex`: bundle structure verified; end-to-end runtime smoke test still pending valid local auth

Start here:

- Publisher guide: `skills/README.md`
- Release order: `skills/RELEASE_PLAN.md`
- Smoke-test report: `skills/TEST_REPORT.md`
