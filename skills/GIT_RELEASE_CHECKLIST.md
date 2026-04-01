# Git And Release Checklist

Use this file as the final pre-publish checklist for `v0.1.0`.

## Recommended Commit Message

Short commit title:

```text
release: prepare v0.1.0 CC harness skill pack
```

Longer commit body:

```text
release: prepare v0.1.0 CC harness skill pack

- add public repo homepage for the portable skill pack
- add per-skill READMEs for all six bundles
- add release plan, GitHub release copy, and ClawHub listing copy
- add smoke-test report for Claude Code and OpenClaw
- document Codex runtime auth as the remaining verification blocker
```

## Pre-Commit Check

Run:

```bash
bash ./skills/check_all.sh
```

Confirm:

- [ ] the six bundles each contain `SKILL.md`, `README.md`, `references/`, and `scripts/`
- [ ] [skills/TEST_REPORT.md](/Users/carl/Downloads/codegod/skills/TEST_REPORT.md) is current
- [ ] [skills/RELEASE_PLAN.md](/Users/carl/Downloads/codegod/skills/RELEASE_PLAN.md) matches the intended release order
- [ ] no local tokens, temp installs, or private config files were added to git

## Git Steps

```bash
git status
git add README.md .gitignore skills
git commit -m "release: prepare v0.1.0 CC harness skill pack"
git tag -a v0.1.0 -m "First Portable CC Harness Skills"
```

If you want a separate annotated release commit body, use the longer message above.

## GitHub Release Steps

1. Push branch and tag.
2. Create release `v0.1.0`.
3. Use title: `v0.1.0: First Portable CC Harness Skills`
4. Paste body from [GITHUB_RELEASE_v0.1.0.md](/Users/carl/Downloads/codegod/skills/GITHUB_RELEASE_v0.1.0.md)
5. Add topics from [RELEASE_PLAN.md](/Users/carl/Downloads/codegod/skills/RELEASE_PLAN.md)

## ClawHub Release Steps

Publish in this order:

1. `dream-memory`
2. `memory-extractor`
3. `structured-context-compressor`
4. `verification-gate`
5. `swarm-coordinator`
6. `kairos-lite`

Use the names and short descriptions from [CLAWHUB_LISTINGS.md](/Users/carl/Downloads/codegod/skills/CLAWHUB_LISTINGS.md).

Batch publish command:

```bash
bash ./skills/publish_all.sh 0.1.0
```

## Final Release Gate

Only say the release is fully verified across all three hosts if the `Codex` auth issue has been resolved and the smoke test has been rerun.
