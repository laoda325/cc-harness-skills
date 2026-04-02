# CC Harness Skills（最后更新 2026-04-02）

**状态**：已安装 3 个优先技能到 `~/.claude/skills/`，版本 v0.1.0
**安装源**：`laoda325/cc-harness-skills`（GitHub，fork 自 `LearnPrompt/cc-harness-skills`）
**技能结构**：每个技能含 `SKILL.md`、`references/prompt-template.md`、`scripts/`

**三个技能**：
1. **dream-memory** — 合并记忆，防止腐烂，保持 MEMORY.md <200 行
2. **verification-gate** — 完成后只读验证，区分"验证"与"声称完成"
3. **structured-context-compressor** — 长会话产 9 段续接摘要

**调用**：在 Claude Code 中使用 `Use /skill-name to ...` 格式

**何时用**：
- dream-memory：每晚或长会话后，合并记忆
- verification-gate：重大功能完成后质量门控
- structured-context-compressor：交接或长会话归档

**剩余可安装**：`memory-extractor`、`swarm-coordinator`、`kairos-lite`
