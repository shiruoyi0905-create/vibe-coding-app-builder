# Vibe Coding App Builder

[English](./README_EN.md)

一套把产品想法推进为**有边界、可验证、可运行 Web MVP**的阶段化方法，同时提供可直接安装到 Codex 的 Skill。

它解决的不是“如何让 AI 一次生成更多代码”，而是如何让 AI 与人围绕同一份产品基准，小步完成需求判断、原型验证、规格固化、技术设计、开发测试和发布交付。

## 适合谁

- 想把产品 idea 快速做成可演示 MVP 的个人开发者或产品经理
- 正在使用 Codex、Cursor 等 AI 编程工具推进完整项目的人
- 希望减少 AI 跑偏、需求漂移、反复返工和“看起来能跑”问题的小团队

不适合仅修改一个孤立 Bug，也不能替代支付、医疗、隐私、高并发等场景所需的专项工程与合规设计。

## 核心方法

整个流程由 7 个阶段组成：

| 阶段 | 核心产出 | 进入下一阶段的依据 |
|---|---|---|
| Phase 0 问题与 MVP | 产品简报、风险假设、P0/P1/P2 | 用户、场景、任务和 MVP 边界清晰 |
| Phase 1 体验原型 | 可点击原型、关键状态 | 用户无需讲解可走通核心路径 |
| Phase 2 产品规格 | PRD、验收标准、非目标 | 开发者可据此判断实现是否合格 |
| Phase 3 技术方案 | 架构、数据模型、垂直切片 | 复杂度匹配，风险有验证方案 |
| Phase 4 正式开发 | 可运行项目、测试、说明 | 干净环境可启动，核心检查通过 |
| Phase 5 质量打磨 | 走查记录、修复证据 | 阻断、理解成本和关键体验达标 |
| Phase 6 发布交付 | 线上版本、发布记录、回滚点 | 生产环境复测并可安全回退 |

详细流程见 [Vibe-Coding-SOP.md](./Vibe-Coding-SOP.md)。

## 仓库结构

```text
.
├── README.md
├── README_EN.md
├── Vibe-Coding-SOP.md
├── launch/
│   └── launch-copy.md
├── examples/
│   └── quick-start.md
├── templates/
│   └── context-packet.md
└── skill/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── vibe-coding-sop.md
```

## 安装 Skill

将仓库中的 `skill/` 复制到 Codex Skills 目录，并命名为 `vibe-coding-app-builder`：

```bash
mkdir -p ~/.codex/skills/vibe-coding-app-builder
cp -R skill/. ~/.codex/skills/vibe-coding-app-builder/
```

重新打开 Codex 任务后，可显式调用：

```text
Use $vibe-coding-app-builder 把这个产品想法推进成可测试、可运行的 MVP：[你的想法]
```

Skill 也允许在符合“从想法到 App”“Vibe Coding 完整项目”等请求时被自动发现。

## 5 分钟开始

如果你只有一个模糊想法：

```text
Use $vibe-coding-app-builder。

我的想法是：[一句话描述]
目标用户可能是：[用户]
我认为最重要的体验是：[体验]

先不要写代码。请识别最危险的 3 个假设，定义一条核心用户路径，
将功能分为 P0/P1/P2，并告诉我现在最值得验证什么。
```

如果已经有 PRD 或代码仓库：

```text
Use $vibe-coding-app-builder。

这是现有 PRD/仓库：[路径]
目标：[本轮目标]
不得改变：[明确约束]

先检查已有内容，判断当前处于哪个阶段，只补缺失部分。
完成后报告改动文件、验证命令、实际结果和遗留风险。
```

更多完整示例见 [examples/quick-start.md](./examples/quick-start.md)。

## 与 AI 协作的关键习惯

1. 每轮提供最小但完整的上下文包。
2. 先处理核心路径，再补页面和装饰。
3. 用测试、日志、截图和用户行为判断，而不是接受“应该可以”。
4. 需求若改变核心路径，先更新 PRD 和验收标准。
5. 同一失败修补两次仍无效，停止试错并回查根因。
6. 区分原型捷径与可上线实现，明确标记假数据和临时方案。

可直接复制 [templates/context-packet.md](./templates/context-packet.md) 开始一轮任务。

## 完成标准

一个 MVP 至少应满足：

- 目标用户能独立完成核心任务
- P0 没有阻断性错误，重要失败有恢复路径
- 干净环境可按文档启动
- 相关 lint、typecheck、测试和构建已实际执行
- 手机与桌面端关键路径已走查
- 假数据、临时实现、已知风险和后续工作已标注

## 时间预期

1.5–2.5 小时通常只够完成范围极小、使用假数据的可演示原型。带真实接口、认证、持久化、部署和质量保障的 MVP，通常需要数小时到数天。以阶段门是否通过判断进度，不以乐观时间承诺替代质量。

## 状态

当前仓库包含 SOP 与 Codex Skill 的首个可用版本。欢迎通过 Issue 记录真实使用中出现的跑偏案例、遗漏阶段或改进建议。
