# Skills-Matnoble

这是一个专门为 OpenClaw 架构及其他需要高度定制化大模型交互场景设计的**高阶技能 (Skills) 集合**。

## 目录结构

每个子目录代表一个独立的系统提示词 (System Prompt) 或行为约束规范（即 Skill）。

### [ocr-latex](./ocr-latex/SKILL.md)

专为基于 Google Gemini 3.0 Flash 等多模态大模型设计的零容错 OCR 工具。
*   **核心功能**：精确地将图片或 PDF 中包含中文文本与数学公式的混合排版完整翻译为标准的 LaTeX 格式代码。
*   **特性**：强制英文提示以最大化指令遵循度；内置了强硬的防偏离机制以屏蔽大模型的寒暄式回答；具备面向多模态混合输入的鲁棒性处理设计。

## 如何使用 (How to Use)

本项目兼容 [vercel-labs/skills](https://github.com/vercel-labs/skills) 标准规范。你可以通过 `skills` CLI 工具快速将这些高级技能集成到你的 Agent 或工作流中。

### 1. 添加技能
运行以下命令来安装本项目中的特定技能（请将 `<YOUR_GITHUB_ID>` 替换为你的真实 ID）：

```bash
# 格式：npx skill add <Repository_URL>/<Skill_Subdirectory>
npx skill add https://github.com/ross/skills-matnoble/ocr-latex
```

### 2. 更新技能
若要同步本仓库的最新优化逻辑：

```bash
# 进入你的 agent 目录执行更新
npx skill update ocr-latex
```

> [!TIP]
> **从旧版本迁移**：如果你之前是以 `ocr_latex_generator` 名字安装的，请重新运行一次 `npx skill add` 命令以获取最新的命名空间支持。

## 适用场景

*   多 Agent 协同流水的管道节点 (Pipeline Node)。
*   基于 Telegram Bot 等终端界面下的非结构化指令接收端。
*   对接基于 API 的自动化文献与公式排版系统。

## 规范

*   所有技能文件必须以 `SKILL.md` 的规范格式编写。
*   顶部必须包含标准的 YAML Frontmatter，声明 `name` 和 `description` 元数据。
*   使用 Markdown 列出绝对边界条件，拒绝含糊其辞的引导词。
