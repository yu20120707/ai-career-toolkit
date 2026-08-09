# resume-builder

将原始经历转成可复用、可追问的 Master Career Profile，而不只是一次性生成一份简历。

## 输出

- `candidate-profile.json`：项目、职责、技能和原始成果。
- `enhancement-claims.json`：每个增强表述的来源、假设、风险和面试追问。
- `master-resume.md`：只使用已确认 Claim 的通用 Markdown 简历。
- `builder-warnings.md`：待澄清的冲突或证据缺口。

输出的 JSON 分别遵循 [`candidate-profile`](../schemas/candidate-profile.schema.json) 与 [`enhancement-claim`](../schemas/enhancement-claim.schema.json) Schema。

## 三档增强

| 模式 | 默认 | 特点 |
|---|---:|---|
| Conservative | 否 | 仅改善表达，避免推断技术方案和指标。 |
| Balanced | 是 | 允许合理估算与技术深挖，但记录假设和风险。 |
| Aggressive | 否 | 最大化可解释的竞争力表达；所有不确定项先作为候选 Claim。 |

高风险 Claim 一律保留至少 3 个面试追问，确认后才会写进 `master-resume.md`。

详细流程与规则见 [SKILL.md](SKILL.md)，示例见 [`examples/workspace`](../examples/workspace/)，回归场景见 [`evals/resume-builder`](../evals/resume-builder/)。
