# Brief 模板

这是授意模式使用的完整 brief 模板。适用于网站、移动 App、桌面应用三类产品。

填空时遵循以下原则：

- **具体优于抽象**：参考产品写名字，颜色写 hex，字体写具体名字，动效写具体参数
- **"不要做"清单不能为空**：主动替用户推导，这是模板的灵魂
- **结尾一句话总结必须写**：AI 会重点抓头尾
- **按平台调整数值**：不同平台的具体规格见 `platform-conventions.md`

---

## 完整模板

````markdown
# [产品名] Visual Design Brief

## 平台与范围

- **平台**：[Web / iOS / Android / macOS / Windows / 跨平台]
- **技术栈**：[React / SwiftUI / Jetpack Compose / Electron / ...]
- **最小支持尺寸**：[例如 desktop 最小 800×600、mobile iPhone SE 到 iPad]
- **暗色模式**：[v1 做 / v1 不做]

## 品牌气质

**一句话定位：[气质 A] + [气质 B] + [一个具体的差异化特征]。**

例子："Raycast 的精度 + Vercel 的现代感 + 一个会弹跳的灵魂"

[用 2-3 句话展开说明这个产品是做什么的、给谁的、为什么需要这种气质。]

核心比喻：**[静态状态] + [动态状态]。**

例子："静态看是精致的开发者工具，动起来有灵魂。"

## 视觉原则

列出 3-5 条最重要的原则。每条原则应该能在后面的具体规格里找到对应实现。

1. [原则名] — [一句话解释]
2. [原则名] — [一句话解释]
3. [原则名] — [一句话解释]

## 气质参考

- **主要参考**：[2-3 个具体产品名，**优先同平台的产品**]
- **次要参考**：[1-2 个 design system 或 component library]

**不要写"现代设计"、"简约风"这种**——必须是具体的产品名字。

对跨平台产品，参考要覆盖每个平台的典范（例如 web 参考 Linear web 版，iOS 参考 Linear iOS 版）。

## ❌ 不要做的事（必填，不能空）

这一节是 brief 的灵魂。列出所有**会把 AI 推向默认路径、但不是你想要的**选项。

常见模板：

- 不要用 [某类字体]（[具体字体名举例]）
- 不要用 [某类背景色]（[hex 举例]）
- 不要做 [某种形状]（[举例]）
- 不要用 [某种饱和度/风格] 的 [某元素]
- 不要出现 [某类语汇/手势]（例如"手写感"、"editorial quote"、"app icon squircle"）
- 不要用 [某种动效]（例如"fade-in"、"linear easing"）
- 不要 [某种布局约定]

每一条都应该对应一个 AI 可能走错的方向。

## 调色板

```
Background      #XXXXXX   [简短说明]
Surface         #XXXXXX   [用在哪]
Surface hover   #XXXXXX
Border          #XXXXXX
Border strong   #XXXXXX
Text primary    #XXXXXX
Text muted      #XXXXXX
Text subtle     #XXXXXX
Accent          #XXXXXX   [强调色定位]
Accent glow     rgba(...)  [用于发光/hover]
Success         #XXXXXX
Warn            #XXXXXX
Error           #XXXXXX
```

**强调色建议控制在 1 个**。需要彩色时，扩展成一个"家族"（例如 `#8B5CF6` 紫 + `#EC4899` 粉 + `#22D3EE` 青——同属电光家族），而不是随便拿三个不相关的颜色。

**移动端注意**：暗色模式基本是必须，颜色设计时就要同时考虑两套。

## 字体系统

- **UI / Display**: [具体字体名] + 可选 fallback
- **Mono**: [具体字体名]（用于：loading 文案、metadata、代码感元素）
- **不使用**: [明确禁止的字体类别]

**平台字体选择提示**：
- Web：Geist / Inter / Satoshi / IBM Plex Sans
- iOS：优先 SF Pro（系统字体）；自定义字体需要理由
- Android：Roboto（系统）或 Inter
- macOS 原生：SF Pro（系统）
- Windows 原生：Segoe UI（系统）或 Inter
- Electron：和 Web 一样自由

Scale（按平台有所不同）：

**Web**: 12 / 13 / 14 / 16 / 20 / 28 / 40 / 56 / 72（px）
**Mobile**: 12 / 13 / 15 / 17 / 20 / 24 / 28 / 34（pt/sp，正文基准 17pt/16sp）
**Desktop**: 11 / 12 / 13 / 14 / 16 / 20 / 28 / 40（px，比 web 小一档）

Display 级别字重 [数字]，tracking [数字]。

## 间距与圆角

**间距基数**（根据平台选）：
- Web / Mobile：**8px / 8pt**
- Desktop（高密度场景）：**4px**

Space scale 示例（8px 基数）：4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 96

**圆角家族**：
- 小元素（chip、badge）：`[N]px`
- 中元素（按钮、输入框）：`[N]px`
- 大元素（卡片、modal）：`[N]px`
- **明确禁止或要求 pill 形**

平台建议：
- Web：8 / 12 / 16px 主流
- Mobile：10 / 14 / 20px（iOS 略大），Material 有专门的 shape system
- Desktop：4 / 8px 偏小，强调工具感

## 触控目标（mobile / 触屏设备必填）

- **最小触摸目标**：iOS 44×44pt / Android 48×48dp
- **按钮实际尺寸**：[≥48pt 是建议下限]
- **列表项行高**：[≥44pt]
- **安全区处理**：[描述 notch / home indicator 的处理方式]

## 核心屏幕

一个屏幕一节，描述每个屏幕的具体布局和元素。每节包含：

### N. [屏幕名]

[布局描述 —— 居中/左对齐/栅格？]
[元素从上到下依次列举，每个元素说明尺寸、颜色、字体、圆角、特殊交互]
[特别是这个屏幕的 signature moment 是什么]

**Mobile 补充**：描述导航位置（tab bar? nav stack?）、modal 类型（full-screen? sheet?）
**Desktop 补充**：描述 window chrome、是否有 sidebar、key shortcuts

## 组件清单

把上面各屏幕用到的组件归总：
Button (primary / secondary / ghost)、Input、Textarea、Chip、Card、Modal / Sheet、ProgressBar、Banner 等。

**跨平台产品**应该注明哪些组件跨平台共享、哪些是各平台特有的。

## 微交互（这是产品的灵魂）

### 动效参数基线

**Web / Electron**（Framer Motion / React Spring）：
- 标准：`stiffness: 400, damping: 25`
- 更柔和：`stiffness: 300, damping: 20`
- 更夸张（overshoot 明显）：`stiffness: 500, damping: 18`

**iOS 原生**（SwiftUI Animation）：
- 标准：`response: 0.5, dampingFraction: 0.8`
- snappy：`response: 0.3, dampingFraction: 0.9`
- bouncy：`response: 0.4, dampingFraction: 0.6`

**Android 原生**：
- Material motion 标准 curves：`FastOutSlowInEasing`（默认）
- Spring：`Spring.StiffnessMedium, DampingRatioMediumBouncy`

### 具体交互规格

- **按钮 hover/press**: scale [数字], [时长], [easing]
- **卡片入场**: [初始态] → [终态], stagger [N]ms
- **Focus 态**: [具体的 ring / border 变化]（web/desktop 重点）
- **Signature moment 的动效**: [详细描述]
- **Idle 动画**: [哪些元素一直在动，周期多少]

### Haptic feedback（mobile 必填）

- 主要 tap：[light / medium / heavy]
- 成功操作：[success notification]
- 错误：[error notification]
- Selection：[selection haptic，如果有滚轮/picker]

### 交互约束

- **Web**：hover 态是主要 micro-interaction 载体
- **Mobile**：没有 hover，用 press 态 + haptic 补偿
- **Desktop**：键盘快捷键必须覆盖所有主要操作，Cmd+K 命令面板几乎是标配

动效是让"静态很专业"升华到"动起来有灵魂"的关键，不能省略。

## MVP 不做

- [浅色/暗色模式一个先不做]
- [响应式的某个断点先不做]
- [某些跨平台的同步先不做]
- [其他推迟到后续版本的功能]

## 一句话核心

（必填！放在 brief 最末尾。）

**[一句话浓缩方向 + 再次强调最重要的禁止项]**

例子：`Dark canvas, sans-serif + mono, one electric accent, everything bounces with spring. Not editorial, not warm, not cream. Think Raycast meets a creative tool.`
````

---

## 填写时的决策提示

### 如果用户方向是「工具类 / dev-focused / 精致克制」

- 背景用近黑（`#09090B` 或 `#0A0A0B`），**不用纯黑**
- 字体：Web 用 Geist / Inter + Geist Mono / JetBrains Mono；Mobile 用系统字体
- 强调色用电光色（紫、绿、青其一）
- 圆角偏小：Web 8-16px，Desktop 4-8px，禁 pill
- 参考：
  - Web：Raycast / Linear / Vercel / Warp / Railway
  - macOS：Raycast / Linear Desktop / Warp
  - iOS：Dark Noise、NotePlan、Tot

### 如果用户方向是「editorial / warm / 个人品牌站」

- 背景用奶油米（`#FAF8F3` 附近），**不用纯白**
- 字体用 Inter 无衬线 + Instrument Serif / Fraunces 衬线做 display
- 强调色用暖色（琥珀、桃、锈红）
- 圆角 12-16px，可以 pill
- **这种风格基本只适合 web**——mobile 和 desktop 很少走这条路
- 参考：Stripe / Every.to / 独立创作者站

### 如果用户方向是「chaotic / maximalist / Gen-Z」

- 背景可深可浅但要有"质地"（noise texture、彩色底）
- 字体混用（display sans + mono + 偶尔装饰字体）
- 配色糖果色、高饱和、多色
- 圆角大圆角、pill、偶尔尖角
- 可以加 marquee、粒子、emoji
- 参考：Gumroad、部分 Vercel template

### 如果用户方向是「原生平台 / native feel」（桌面/移动特有）

- 优先使用系统字体、系统动画曲线、系统组件
- 颜色用系统 palette（iOS dynamic colors、macOS named colors）
- **尽量不要**用"夸张"的 signature moment——原生 feel 的美学是"像系统自带的一样"
- 参考：
  - macOS：Things 3、Craft、Notion Calendar
  - iOS：Things 3、Overcast、NetNewsWire

每种方向都不对称地禁止另外几种的语汇。
