# Visual Direction Skill

[English](#english) · [中文](#中文)

---

## 中文

一个 Claude Code skill,帮你把**模糊的视觉设计意图**转成**可执行的 brief**,给 AI 设计工具(Figma AI、v0、Lovable、Claude 等)使用。适用于网站、移动 App(iOS/Android)、桌面应用(macOS/Windows/Electron)等所有数字产品。

### 核心洞察

**AI 设计工具不缺执行力,缺的是精确的方向。**

好的 brief 不是描述想要什么,而是用 **具体的参考产品 + 具体的禁止清单 + 具体的数值** 把 AI 的默认路径拉到你想去的方向。

### 三种使用模式

| 模式 | 触发信号 | 主要产出 |
|------|----------|----------|
| **分析** | 发来截图/URL/app 录屏,问"好不好看"、"这是什么风格"、"拆解一下" | 维度化的设计评价 |
| **授意** | 要设计自己的产品,需要给 AI 工具写 prompt | 一份完整的 brief |
| **迭代** | 已有 AI 生成的结果,某些地方不满意 | 一个 delta update |

### 六条核心原则

1. **文案即 brief,视觉兑现 brief** —— tagline 和视觉必须说同一件事
2. **具体的参考产品 >> 抽象的形容词** —— "像 Raycast + Linear" 比 "现代、干净" 有用一万倍
3. **❌ 不要做的事比要做的事更重要** —— AI 默认路径是"友好、温暖、安全",不明确禁止就会滑过去
4. **抽象意图必须翻译成具体数值** —— "弹性" → `spring stiffness: 400, damping: 25`
5. **签名时刻 + 稳定支点** —— 把设计预算集中砸在一个瞬间,其他地方保持克制
6. **继承而非照搬** —— 周围元素用更克制的方式继承 signature moment 的视觉系统

### 文件结构

```
visual-direction-skill/
├── SKILL.md                          # skill 主文件(方法论 + 三种模式)
└── references/
    ├── brief-template.md             # 完整 brief 模板(授意模式必用)
    ├── visual-dimensions.md          # 10 个视觉维度清单(分析模式必用)
    ├── iteration-patterns.md         # 常见 delta update 模式(迭代模式必用)
    └── platform-conventions.md       # 网站/移动/桌面三类平台的设计约定
```

### 如何安装

把整个目录放到 Claude Code 的 skills 位置:

```bash
# 用户级(所有项目可用)
cp -r visual-direction-skill ~/.claude/skills/visual-direction

# 或者项目级(只在当前项目可用)
cp -r visual-direction-skill .claude/skills/visual-direction
```

### 触发方式

不用显式调用。只要对话里涉及:

- "帮我设计一个网站/App/桌面应用"
- "我想做个人主页/产品"
- "这个页面/这个 App 不好看想改"
- "给 Figma/v0 写个 brief"
- "拆解一下这个产品的设计"
- "为什么 AI 生成的设计不对劲"
- "这个设计好不好看"

Claude 会自动调用这个 skill。

---

## English

A Claude Code skill that turns **vague visual design intent** into **executable briefs** for AI design tools (Figma AI, v0, Lovable, Claude, etc.). Works for websites, mobile apps (iOS/Android), and desktop apps (macOS/Windows/Electron) — any digital product.

### Core Insight

**AI design tools don't lack execution — they lack precise direction.**

A good brief doesn't describe what you want. It pulls the AI's default path toward your direction using **specific reference products + a specific "do not" list + specific numeric values**.

### Three Modes

| Mode | Trigger | Output |
|------|---------|--------|
| **Analyze** | User sends screenshot/URL/app recording, asks "is this good?", "what style is this?", "break it down" | Dimension-by-dimension design critique |
| **Direct** | User is designing their own product, needs a prompt for AI tools | A complete brief |
| **Iterate** | User has AI-generated results, some parts aren't right | A delta update |

### Six Core Principles

1. **Copy is the brief, visuals fulfill the brief** — tagline and visuals must say the same thing
2. **Specific reference products >> abstract adjectives** — "like Raycast + Linear" beats "modern, clean" by an order of magnitude
3. **What NOT to do matters more than what to do** — AI's default path is "friendly, warm, safe"; without explicit prohibitions it slides there
4. **Abstract intent must translate to concrete numbers** — "springy" → `spring stiffness: 400, damping: 25`
5. **Signature moment + stable anchors** — concentrate the design budget on one moment, keep everything else restrained
6. **Inherit, don't replicate** — surrounding elements should inherit the signature moment's visual system in a more restrained way

### File Structure

```
visual-direction-skill/
├── SKILL.md                          # Main skill file (methodology + three modes)
└── references/
    ├── brief-template.md             # Complete brief template (required for Direct mode)
    ├── visual-dimensions.md          # 10 visual dimensions checklist (required for Analyze mode)
    ├── iteration-patterns.md         # Common delta update patterns (required for Iterate mode)
    └── platform-conventions.md       # Design conventions across web/mobile/desktop
```

### Installation

Drop the directory into Claude Code's skills location:

```bash
# User-level (available in all projects)
cp -r visual-direction-skill ~/.claude/skills/visual-direction

# Or project-level (only in the current project)
cp -r visual-direction-skill .claude/skills/visual-direction
```

### How It Triggers

No explicit invocation needed. Claude auto-activates this skill whenever the conversation touches:

- "Help me design a website/app/desktop app"
- "I want to make a personal site/product"
- "This page/app doesn't look good, help me fix it"
- "Write a brief for Figma/v0"
- "Break down this product's design"
- "Why does AI-generated design feel off?"
- "Is this design good?"
