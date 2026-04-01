# Smoke Test Report

Date: April 1, 2026

Scope:

- `dream-memory`
- `memory-extractor`
- `verification-gate`
- `swarm-coordinator`
- `structured-context-compressor`
- `kairos-lite`

## Summary

- Bundle structure checks: passed
- Python helper script compilation: passed
- Claude Code skill availability: passed for all six
- OpenClaw skill availability: passed for all six
- Codex skill availability: blocked by runtime authentication in the local environment

## Commands Run

Bundle checks:

```bash
bash ./skills/check_all.sh
python3 -m py_compile \
  skills/dream-memory/scripts/dream_memory.py \
  skills/memory-extractor/scripts/memory_manifest.py \
  skills/verification-gate/scripts/verification_context.py \
  skills/swarm-coordinator/scripts/task_board.py \
  skills/structured-context-compressor/scripts/render_template.py \
  skills/kairos-lite/scripts/job_spec.py
```

Claude Code availability test:

```bash
printf 'Use /dream-memory and reply AVAILABLE or UNAVAILABLE only.\n' \
  | claude -p --model sonnet --setting-sources user,project,local --allowedTools Read,Grep,Glob
```

The same pattern was run for all six skills.

OpenClaw availability test:

```bash
openclaw skills info dream-memory
```

The same pattern was run for all six skills.

Codex isolated smoke test:

```bash
HOME="$tmp/home" CODEX_HOME="$tmp/codex-home" \
  codex exec --skip-git-repo-check --sandbox read-only --model gpt-5 --cd "$tmp" \
  'Use /dream-memory. Reply AVAILABLE or UNAVAILABLE only.'
```

## Results

### Bundle Checks

`bash ./skills/check_all.sh` returned:

```text
All skill bundles passed basic checks.
```

### Claude Code

All six skills returned `AVAILABLE` when invoked through `claude -p` after installation into `~/.claude/skills`.

### OpenClaw

All six skills returned `✓ Ready` from `openclaw skills info <slug>` after installation into `~/.openclaw/workspace/skills`.

Observed note:

- the local OpenClaw environment emits repeated `Skipping skill path that resolves outside its configured root.` warnings while scanning other workspace-linked skills
- those warnings did not block any of the six tested skills from resolving as `Ready`

### Codex

The initial local test was blocked by unrelated malformed installed skills outside this repo.

A second isolated test used a temporary `HOME` and `CODEX_HOME` containing only the six skill bundles. That removed the unrelated skill parsing issue, but the request still failed because the local Codex runtime could not authenticate to the OpenAI Responses API:

```text
ERROR: unexpected status 401 Unauthorized: Missing bearer or basic authentication in header
```

Interpretation:

- bundle loading is no longer blocked by foreign skills once `HOME` and `CODEX_HOME` are isolated
- end-to-end Codex invocation remains unverified in this environment until valid local auth is configured

## Release Readiness

Current release recommendation:

- safe to publish for `Claude Code` and `OpenClaw`
- publish for `Codex` with an explicit note that local smoke verification is still pending valid auth
- do not claim full three-host runtime verification in the release notes until the Codex auth issue is cleared
