---
name: project-deep-dive
description: 以业务视角的面试官式追问，把一个已完成项目或待启动需求讲清楚：为什么做、用户做了什么、如何推动落地、价值如何量化、以及复盘如何改进。用户需要深挖项目、复盘项目、模拟业务面试、论证需求价值或准备晋升/述职时使用；不要用于技术架构设计、写实现代码或简单事实问答。
source: adapted
upstream: https://github.com/Yipper0915/Project-Deep-Dive-Skill/blob/main/project-deep-dive-SKILL.md
license: upstream license not stated
adaptation_notes: 适配 AI Career Toolkit 的本地 Career Workspace、候选人项目/claim 追踪和 application-aware interview-griller；保留一问一答与业务量化门槛，不复制上游仓库的运行时或脚本。
---

# Project Deep-Dive

## Purpose

用业务视角的面试官式追问，把项目从“做过”挖到“为什么做、我做了什么、怎么落地、价值是什么、下次怎么做”。追问优先，只有用户卡壳或出现盲区时才提供少量发散方向。

## Use When

Use when the user wants to：

- 深挖或复盘一个项目；
- 模拟业务面试、项目面或晋升/述职追问；
- 判断一个待启动需求是否值得做；
- 讲清个人贡献、推动边界和业务价值。

Do not use for technical architecture design, implementation work, or simple factual questions. For 技术细节、代码和系统设计，交给相应的工程或 `interview-griller` Skill。

## Inputs

先读取已有材料，不重复问材料中已经明确的事实：

- `candidate-profile.json` 中的目标项目（优先用 `project_id` 定位）；
- `enhancement-claims.json` 中关联该项目的 claims、假设、风险和 drills；
- 如与具体投递关联：`applications/<job-id>/application.json`、JD 快照、tailored resume、submitted resume 和已有面试反馈；
- 用户提供的项目文档、纪要、数据或对话上下文。

开始前用一句话确认两个锚点：深挖哪个项目，以及这是“做过的项目复盘”还是“待启动的需求论证”。如果缺少必要材料，明确说出缺口，不要猜测项目事实。

## Process

1. 先读上下文，建立项目、目标岗位和现有证据的边界。
2. 一次只问一个问题，沿当前线索逐层追问；不要提前给标准答案。
3. 按以下阶梯钻取，未到复盘层不随意换线：
   - **根因**：直接原因是什么？再往上一层的根本原因是什么？如果不做谁会先受影响？
   - **归属**：用户具体推动了哪几步？哪些由协作方完成？没有用户这件事会怎样？
   - **落地**：卡在哪一环？如何解决？拉了哪些方对齐？最难对齐的是谁，为什么？
   - **价值**：看哪个业务指标？基线是多少，变化多少，如何测量？是一次性还是持续价值？投入产出比如何？
   - **复盘**：如果没有达到预期，如何归因？重来一次会在哪一环做不同判断？
4. 遇到“提升效率、效果不错、大家认可”等泛泛回答，必须追到指标、基线、幅度和测量方法；允许记录 `unknown`，不允许补造数字。
5. 每条线索挖透后，用一两句复述“我听到的是……”让用户校正。用户卡壳、重复、已到复盘层，或同一线索连续追问 3–4 轮时，才给 2–3 个可选业务角度，例如成本/人力、持续性、负向影响、优先级。
6. 用户说“够了”或多条线索达到复盘层后，询问是否需要沉淀纪要。

## Conduct

- 业务结果、个人贡献和证据优先于技术炫技或方案优雅。
- 不接受“项目很简单没啥可挖”；简单项目同样要说明归属、影响和验证方式。
- 听不懂时直接说“我没跟上，能换个说法吗”，不要假装理解。
- 开放追问优先；只有明显卡壳时才用 A/B/C 选项作脚手架。
- 深挖纪要是事实与用户确认内容的沉淀，不是替用户包装经历，也不是新的 enhancement claim。
- 如有 application 上下文，纪要可帮助 `interview-griller` 选择业务追问，但不能替代 submitted artifact、claim provenance 或真实面试反馈。

## Output

默认在对话中持续追问。用户要求沉淀时，写入本地 Career Workspace：

- 独立项目：`deep-dive/YYYY-MM-DD-<topic>.md`；
- 关联投递：`applications/<job-id>/deep-dive/YYYY-MM-DD-<topic>.md`。

纪要至少包含：

- 项目一句话概述；
- 直接原因 / 根本原因；
- 用户的执行环节与推动边界；
- 落地卡点与解决方式；
- 业务指标、基线、量化幅度和测量方式；
- 复盘与“重来会怎么改”；
- 仍待确认的事实、开放问题和发散方向；
- 关联的 `project_id`、`job_id`、`claim_ids`（如存在）。

## Do Not

- 不要一次抛出多个主问题。
- 不要在证据不足时替用户下结论、写标准答案或发明指标。
- 不要激活、修改或删除 enhancement claims。
- 不要改写简历、提交申请、联系招聘方或推断面试结果。
- 不要把业务深挖纪要当成技术架构设计文档。
