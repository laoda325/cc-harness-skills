# CC Harness Skills

Portable agent skills distilled from a publicly mirrored `CC` coding-agent codebase, then rewritten so they can be installed in `Claude Code`, `Codex`, and `OpenClaw` without depending on private runtime internals.

This repo is not a source dump. It is a cleaned skill pack:

- prompts extracted into reusable templates
- host-agnostic helper scripts
- portable `SKILL.md` bundles
- release and smoke-test docs for public distribution

If you are building with coding agents, these are the parts that usually separate a fun demo from a stable toolchain:

- memory that stays useful instead of rotting
- compression that preserves user corrections
- verification that does not trust "done"
- multi-agent routing that does not pollute the main context
- proactive jobs with explicit limits

This repo packages those patterns into six installable skills.

## Why This Exists

Most agent repos share the same hard problems:

- how to keep memory useful without storing stale code facts
- how to compress long conversations without losing user corrections
- how to verify claimed completion instead of trusting it
- how to coordinate multiple agents without turning the main context into garbage
- how to add lightweight proactive behavior without building a dangerous daemon

The six skills in this repo package those patterns into download-ready bundles.

## Who This Is For

- builders who want better agent behavior without forking a full agent product
- teams using `Claude Code`, `Codex`, or `OpenClaw` and wanting a shared skill layer
- people studying `CC`-style harness design but needing something publishable and portable
- anyone who wants prompts plus scripts, not prompts alone

## Skill Pack

| Public name | Slug | What it does | Best hosts |
| --- | --- | --- | --- |
| CC Dream Memory | `dream-memory` | Consolidates logs, recent sessions, and topic memories into a short durable memory index. | Claude Code, Codex, OpenClaw |
| CC Memory Extractor | `memory-extractor` | Extracts durable `user`, `feedback`, `project`, and `reference` memories from recent turns. | Claude Code, Codex, OpenClaw |
| CC Verification Gate | `verification-gate` | Runs a read-only challenge pass after implementation to distinguish verified from merely claimed done. | Claude Code, Codex |
| CC Swarm Coordinator | `swarm-coordinator` | Splits large work into research, synthesis, implementation, and verification with bounded workers. | Claude Code, Codex, OpenClaw |
| CC Context Compressor | `structured-context-compressor` | Produces a nine-part continuation summary for long sessions and handoffs. | Claude Code, Codex, OpenClaw |
| CC Kairos Lite | `kairos-lite` | Adds lightweight proactive jobs with schedule, sleep, brief, and expiry rules. | Claude Code, OpenClaw |

Each bundle lives in [`skills/`](/Users/carl/Downloads/codegod/skills/README.md) and includes:

- `SKILL.md`
- `references/prompt-template.md`
- `references/source-notes.md`
- `scripts/...`
- `README.md`

## Start Here

If you only try three things, try these first:

1. install `dream-memory`
2. install `verification-gate`
3. install `structured-context-compressor`

That gives you one memory workflow, one quality gate, and one continuation artifact. It is the fastest way to feel whether this repo is useful.

## Quick Start

Run the basic bundle checks first:

```bash
bash ./skills/check_all.sh
```

Install one skill into a host runtime:

```bash
mkdir -p ~/.claude/skills
cp -R ./skills/dream-memory ~/.claude/skills/
```

Then invoke it in `Claude Code`:

```text
Use /dream-memory to consolidate the memory directory before we continue.
```

```bash
mkdir -p ~/.codex/skills
cp -R ./skills/dream-memory ~/.codex/skills/
```

Then invoke it in `Codex`:

```text
Use /dream-memory and consolidate recent memory files into one stable index.
```

```bash
mkdir -p ~/.openclaw/workspace/skills
cp -R ./skills/dream-memory ~/.openclaw/workspace/skills/
```

Then check it in `OpenClaw`:

```bash
openclaw skills info dream-memory
```

Publish to ClawHub after checks:

```bash
bash ./skills/publish_all.sh 0.1.0
```

## Release Docs

- Publisher guide: [`skills/README.md`](/Users/carl/Downloads/codegod/skills/README.md)
- Release order and copy: [`skills/RELEASE_PLAN.md`](/Users/carl/Downloads/codegod/skills/RELEASE_PLAN.md)
- Smoke-test report: [`skills/TEST_REPORT.md`](/Users/carl/Downloads/codegod/skills/TEST_REPORT.md)

## Naming

Recommended public GitHub repo name: `cc-harness-skills`

Good alternatives:

- `cc-agent-skills`
- `cc-harness-kit`
- `cc-portable-skills`

The public naming uses `CC` on purpose: it signals the origin of the ideas without hard-coding a full vendor product name into the repo identity.

## What Is Verified

Latest smoke-test status:

- `Claude Code`: six skills load successfully
- `OpenClaw`: six skills resolve as `Ready`
- `Codex`: bundle structure is verified; runtime smoke test is pending local auth

Full report: [`skills/TEST_REPORT.md`](/Users/carl/Downloads/codegod/skills/TEST_REPORT.md)

## Project Layout

```text
skills/
  dream-memory/
  memory-extractor/
  verification-gate/
  swarm-coordinator/
  structured-context-compressor/
  kairos-lite/
```

Internal working notes and non-publishable local experiments still live under `.codex/skills/`, but the public release surface for this project is the root `skills/` directory.
