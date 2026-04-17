# 平台约定 / Platform Conventions

这份参考解释 **web、mobile、desktop** 三类产品在视觉设计上的关键差异。
当授意模式确定了平台后，读这个文件对应章节，知道该平台的标准规格和设计范式。

核心前提：**6 条核心原则跨平台通用**，但实现细节（间距、字号、触摸目标、动效参数、导航范式）必须按平台调整。把 web 规格一比一套到移动或桌面就会翻车。

---

## 先识别平台

在写 brief 前，先问清楚（如果用户没说）：

- **Web**：浏览器里运行，需要响应式
- **iOS native**：SwiftUI / UIKit，遵循 Human Interface Guidelines
- **Android native**：Jetpack Compose，遵循 Material Design
- **macOS native**：SwiftUI / AppKit，遵循 macOS HIG
- **Windows native**：WinUI / Fluent Design
- **跨平台桌面**：Electron / Tauri（通常用 web 技术构建）
- **跨平台移动**：React Native / Flutter
- **混合（同一产品覆盖多端）**：Figma、Notion、Linear 这种既有 web 也有原生 app

"跨平台桌面"和"移动原生"混淆是新手常见错误——Electron app 本质是 web app，但用户会用"桌面原生"的标准评价它，所以更难做。

---

## Web

### 标准规格

- **间距基数**：8px（经典）
- **正文字号**：15-18px，行高 1.5-1.65
- **文字列宽**：640-720px（阅读舒适上限）
- **整体容器**：1200-1400px
- **响应式断点**：640 / 768 / 1024 / 1280 / 1536
- **圆角家族**：8 / 12 / 16px 是主流
- **触控目标**：无硬性要求，但互动元素建议 ≥32px

### 交互约定

- **hover 态是 web 独有的**——大量 micro-interaction 设计在此展开
- **cursor**：链接和按钮必须 `cursor: pointer`
- **focus ring**：可见性要足够（至少 2px 外描边），但可以做得精致
- **键盘快捷键**：Cmd/Ctrl+K 打开搜索/命令面板是近年惯例

### Signature moments

- Hero scroll reveal
- 页面切换动画（SPA 才能做）
- Pricing 或功能表的揭示动画
- CTA hover 的精致反馈

### 字体选择

UI 友好的 web 字体：Geist、Inter、IBM Plex Sans、Satoshi、JetBrains Mono、Geist Mono。

### 动效

- 工具：CSS transitions + Framer Motion（React 生态）
- Spring 参数：`stiffness: 400, damping: 25` 是标准
- 时长：200-300ms 是舒适区

### 暗色模式

Web 的暗色模式不是必须（但近年几乎成为标配）。如果做，必须覆盖所有颜色 token，不能只翻转背景。

---

## 移动端（iOS / Android）

### 核心约束：触摸目标

**最小触摸目标**：
- iOS：44×44 pt
- Android：48×48 dp

这是硬性 HIG 要求，违反会直接影响可用性和 App Store 审核。按钮、tab bar 图标、list item 都要满足。

### 标准规格

- **间距基数**：8pt / 8dp
- **正文字号**：
  - iOS：17pt（Body）、15pt（Subhead）、13pt（Footnote）
  - Android：16sp（Body1）、14sp（Body2）
- **行高**：通常是字号的 1.3-1.4（比 web 紧）
- **安全区**：必须避开 notch、home indicator、状态栏——布局用 `safeAreaInsets`

### 没有 hover

**重要：所有 hover 交互都要重新设计成 tap/press 或 long-press。** 不能把 web 的 hover tooltip 直接搬到 mobile。

取而代之：
- `:active`（按下态）的视觉反馈要明显（scale 0.95 + 颜色微变）
- Haptic feedback 替代 hover 的"感知反馈"
- Long-press 展示 context menu

### 导航范式

**iOS**：
- Tab bar（底部，3-5 个）或 Navigation Stack（左上 back 按钮）
- Modal sheet 从底部上滑是 iOS 的标志交互
- Pull-to-refresh 是预期行为（不做反而奇怪）

**Android**：
- 底部 tab bar 或顶部 app bar + 抽屉（drawer）
- 系统级后退手势（从屏幕边缘滑动）——不要遮挡边缘
- FAB（Floating Action Button）是 Material 特有的主操作按钮

### Haptic feedback

Mobile 的独有维度。一个产品"精致"的很大一部分来自 haptic 的精细使用：
- `light` / `medium` / `heavy` impact
- `success` / `warning` / `error` notification
- Selection haptic（滚动选择器的每一档都有 tick）

iOS `UIFeedbackGenerator` / Android `Haptic.vibrate()` 是具体 API。

### Signature moments

- App launch 动画（从 icon 展开到主界面）
- Pull-to-refresh 的自定义动画（比如 Dark Noise 的声波，Things 的磁吸）
- List item 展开/折叠（heights 动画）
- Modal sheet 的上滑 + 部分展开的 detents
- Long-press 的 haptic + 菜单出现

### 字体选择

- **iOS**：SF Pro（系统字体，直接用）。自定义字体需要理由——通常只用在品牌 wordmark。
- **Android**：Roboto（系统）、Inter（流行替代）

### 动效

- iOS 原生 spring：`response: 0.5, dampingFraction: 0.8` 是系统标准
- 避免 `ease-out` / `ease-in-out`——用 cubic Bezier `(0.25, 0.1, 0.25, 1.0)` 或 spring
- 页面切换：iOS 是右推右拉，Android 是系统默认的 fade/slide
- 时长：200-300ms

### 暗色模式

**移动端几乎必须做**。系统级开关，用户期待 app 自动跟随。颜色设计时就要思考两套。

---

## 桌面端（macOS / Windows / Electron）

### 密度

桌面用户是**工作场景**，期待更高信息密度：
- Notion、Figma、Linear 的 desktop 版比 web 版更紧凑
- 正文字号通常 13-14px（比 web 小一号）
- 间距可以用 **4px 基数**（而不是 8px）——更密的栅格

### 标准规格

- **间距基数**：4px 或 8px（根据密度需求）
- **正文字号**：13-14px（标准）、12px（辅助文字）
- **圆角**：通常比 web 小（4-8px），体现工具感
- **Window 最小尺寸**：需要明确（例如最小 800×600）

### Window chrome

- **macOS**：traffic lights（红黄绿圆点）在左上。**不要**自己画窗口控件。菜单合并到系统菜单栏（屏幕顶部）。
- **Windows**：最大化/最小化/关闭在右上。顶部 title bar。
- **跨平台（Electron）**：可以自定义 frameless window，但要根据系统切换控件位置。

### 键盘优先

桌面受众默认期待键盘操作：
- **Cmd+K / Ctrl+K** 打开命令面板（几乎成为行业标配）
- 所有主要操作都要有快捷键
- **Tab 遍历**要正确
- **Escape** 关闭 modal / 取消操作

### Native menu 和 Context menu

- 菜单栏（macOS 顶部、Windows 窗口内）是桌面独有
- 右键菜单（context menu）是用户预期行为
- 原生 menu 不能用 CSS 仿制（Electron 里要用 Menu API）

### Signature moments

- **Command palette**（Cmd+K）：现代桌面应用的标志性时刻
- Sidebar 折叠动画
- Native menu 和 system tray 集成
- Trackpad 手势响应（mac 原生）
- 多窗口支持（打开第二个窗口、拖拽 tab 出来新窗口）

### 字体选择

- **macOS**：SF Pro（系统）
- **Windows**：Segoe UI（系统）、Inter
- **Electron**：和 web 一样自由，但选 Inter/Geist 更有 UI 感

### 动效

**比 web 更克制**。桌面工具不能打扰人——动效时长 100-200ms，幅度小。

Spring 参数可以更 tight：`stiffness: 500, damping: 30`（快速稳定、不 overshoot）。

### Electron 的陷阱

用 web 技术做桌面 app，默认会有"网页套壳"感。要刻意解决：
- **字体渲染**：禁用 subpixel antialiasing（macOS 上看起来太粗）
- **滚动行为**：使用原生 momentum scroll，不要自定义滚动条
- **右键菜单**：不要用浏览器默认的（"Back / Forward / Reload"），换成应用级 context menu
- **Cmd+W / Cmd+Q 行为**：符合系统预期

### 暗色模式

桌面暗色模式通常跟随系统。**macOS 的 vibrancy（半透明模糊）**是原生独有的，Electron 可以通过 `vibrancy` 参数部分模拟。

---

## 跨平台一致性 vs 平台特性

### 通用的（不管什么平台）：

- 6 条核心原则
- 文案即 brief
- 签名时刻 + 稳定支点
- ❌ 不要做清单
- 具体参考产品 > 抽象形容词
- 色彩系统、字体选择、形状语言（品牌锚点）

### 必须按平台调整的：

- 间距基数和字号
- 触摸目标尺寸（mobile 必须 ≥ 44pt/48dp）
- 导航范式
- 动效参数（iOS 原生 spring ≠ web Framer Motion spring）
- 是否支持 hover 态
- 是否需要暗色模式（mobile 基本必须，web 按情况）
- 键盘快捷键（desktop 必须，web 最好有，mobile 无关）
- Haptic feedback（mobile 独有）

---

## 跨平台产品怎么做 brief

如果产品要同时支持 web + iOS + Android（典型 SaaS 场景）：

1. **先定视觉系统**：色彩、字体家族、形状语言、动效语言——这些跨平台一致
2. **再按平台调整实现**：每个平台用自己的 spacing scale、字号、组件、导航范式
3. **允许平台差异化**：iOS 用 bottom sheet，web 用 modal，不要强行统一
4. **保持品牌锚点一致**：logo、主色、关键交互的"感觉"

**错误做法**：把 web 版设计"一比一缩小"搬到 mobile（字太小、点击区太小、没有 safe area）。

**正确做法**：同一品牌、同一色彩系统、同一字体家族——但每个平台各自做地道的实现。参考 Linear、Figma、Notion 是怎么在多端保持一致又不失各自平台感的。

### 跨平台 brief 的结构建议

可以在同一份 brief 里：
1. 主 brief：通用的视觉系统（颜色、字体、调性）
2. 子 brief Web：具体规格 + 响应式策略
3. 子 brief iOS：具体规格 + HIG 合规
4. 子 brief Android：具体规格 + Material 合规

每个子 brief 都遵循 `brief-template.md` 的 10 节结构，但主 brief 的一致性部分不重复。
