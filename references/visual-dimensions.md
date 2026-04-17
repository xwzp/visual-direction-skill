# 视觉设计的 10 个观察维度

这是分析模式使用的维度清单。给定一个界面截图、URL 或 App 录屏，逐维度观察并描述。适用于网站、移动 App、桌面应用三类产品。不需要每次都覆盖全部 10 个——根据设计本身的特点挑 5-8 个最显著的讲。

维度之间不是并列的——前几个（排版、间距、层级）通常是拉开设计水平的关键，后几个（信息密度）更偏风格归属。

**平台会影响某些维度的观察基准**——例如正文字号 14px 在 desktop 上正常，在 mobile 上偏小；同一个动效时长在 web 上感觉恰好，在 desktop 工具上可能显得过慢。分析时如果知道平台，把基准调到对应平台。

---

## 1. 排版 / Typography

观察点：
- 用了几种字体？（1-2 种克制，3+ 种通常是混乱或刻意的 chaotic）
- 衬线 / 无衬线 / 等宽 / 展示字体 —— 字体类别本身在传达什么（衬线=editorial/serious，mono=dev/technical，粗黑 display=impact）
- 字号层级有几档？好设计通常 4-5 档，新手会做 7-8 档
- 字重怎么用的？（400/500/700 三档是经典）
- 字距（tracking）：Display 级别字体是否做了负字距？（-0.02em 是精致的标志）
- 行高：正文 1.5-1.65 是舒适区（mobile 可以略紧 1.3-1.4，因为字号本身较大）
- **平台字体**：是用了系统字体（SF Pro、Segoe UI）还是自定义字体？原生 App 里用系统字体是克制，用自定义字体是要么品牌要么冒险

**这一维度往往比配色更能拉开设计水平。**

## 2. 配色 / Color

观察点：
- 总共几个颜色？（5-7 个中性色 + 1-2 个强调色是经典）
- 背景用的是纯白/纯黑还是有色相的"近白/近黑"？（纯色是新手特征）
- 强调色出现的频率和位置（只在 CTA？还是蔓延到多处？）
- 是单色系还是多色系？多色时是否属于同一"家族"（都高饱和、都柔和、都粉彩）
- 饱和度整体偏高还是偏低？
- 有没有渐变？类型（linear/radial/conic）和使用位置

## 3. 间距 / Spacing

观察点：
- 整体是"充盈"还是"稀疏"？
- 元素之间的间距是否遵循一套基数（web/mobile 通常 8px，desktop 高密度场景可能 4px）？
- 垂直节奏是否一致？（section 间距、段落间距、元素间距各有其档位）
- 内容宽度是否有上限？（web 常见 640-720px 文字、1200px 整体；desktop 工具可能全幅；mobile 受屏幕限制）
- **平台密度期望**：Desktop 工具可以高密度（Linear、Figma），Mobile 必须宽松（触摸目标），Web 介于两者之间

**新手设计业余感的 80% 来自间距。**

## 4. 层级与对比 / Hierarchy & Contrast

观察点：
- 视线落点是什么？第二眼是什么？（如果回答不了，层级就失败了）
- 通过什么制造对比：大小、色彩、字重、位置、留白？
- 整体对比偏高还是偏低？（高对比制造紧张感，低对比制造从容感）
- 有没有刻意打破层级的地方？（用于注意力锚点）

## 5. 形状语言 / Shape Language

观察点：
- 圆角半径：`0 / 4 / 8 / 12 / 16 / full(pill)` —— 哪几档在用？
- 是否所有元素遵循同一套圆角系统？
- 几何 vs 有机曲线？
- 有没有使用特殊形状（squircle、parallelogram、斜切）？

**圆角的选择几乎是一个站"气质"的签名。尖角=工业/严肃，中等圆角=克制/专业，pill=消费/友好。**

## 6. 质感 / Texture & Material

观察点：
- 扁平、拟物、glassmorphism、neumorphism？
- 有没有 noise texture（颗粒感）？
- 阴影系统：是否有一套从 subtle 到 dramatic 的 elevation？
- 渐变的使用：subtle（点缀）还是 bold（主视觉）？
- 金属质感、纸质感、塑料感？

## 7. 图像风格 / Imagery

观察点：
- 摄影：真实 vs 编辑化 vs 产品图 vs 无？
- 插画：线性 vs 填充 vs 手绘 vs 3D？
- 图标：线性 vs 填充 vs 双色 vs 彩色？图标粗细是否统一？
- 整站图像风格是否一致？

## 8. 动效 / Motion

观察点（只能看视频或实产品，截图看不出）：
- 过渡时长：< 200ms（snappy）、200-400ms（标准）、> 400ms（dramatic）
- Easing：linear、ease-out、ease-in-out、spring？（spring 是"弹性"的关键）
- 有没有 idle 动画（永远在动的东西，如呼吸、漂浮、闪烁）？
- 微交互：hover 反馈（web/desktop）、点击反馈、focus 反馈的精致程度
- **平台动效预期**：
  - Web：动效余地最大，可以从克制到夸张
  - Mobile：iOS 系统 spring 有标志性"感觉"，偏离系统的 motion 很容易显得廉价
  - Desktop：工具类应用动效必须克制（时长 100-200ms），打扰人是大忌
- **Haptic（仅 mobile）**：good design 会精细使用 haptic feedback（light/medium/heavy/success/warning）
- Signature moment 是否有专门的动效预算？

**动效的"克制度"和"有意义性"是高级感的来源。**

## 9. 信息密度 / Information Density

观察点：
- 每屏承载多少信息？（Bloomberg 级 vs 作品集级）
- 信息密度决定整个设计语言的走向——稠密型必须精致紧凑，稀疏型必须舍得留白

## 10. 文案和视觉的同构性 / Copy-Visual Coherence

观察点：
- 文案在传达什么气质？（严肃？俏皮？技术？温暖？）
- 视觉决策是否在**同一件事上用力**？
- 举反例：如果文案很 chaotic（"no cap fr fr"）但视觉用衬线字体 + 奶油背景，就是撕裂的。

**这一维度往往是区分"做得好"和"做得精"的分水岭。**

---

## 分析时的常见风格归属

看完 10 个维度后，把设计归到一个风格流派，帮助用户建立坐标系：

- **Editorial minimalism** —— 衬线 display + 奶油底 + 大量留白（Every.to、Stripe docs、某些独立创作者站）
- **Precise tool aesthetic** —— 暗色 + mono 点缀 + 电光强调色 + spring 动效（Raycast、Linear、Vercel、Warp）
- **Swiss modernism** —— 网格严格、无衬线、黑白红（Apple 早期、很多 agency 站）
- **Brutalist** —— 刻意粗糙、超大字、反常规布局（一些独立设计师作品集）
- **Chaotic maximalism / Y2K revival** —— 多色糖果 + 混字体 + 粒子装饰 + 手写感（Gumroad、很多 Gen-Z 产品）
- **Neo-skeuomorphism / glassmorphism** —— 半透明、模糊、深度（Apple Vision Pro 周边站、macOS Sonoma）
- **Corporate premium** —— 深色 + 金色/铂色 + 超宽字距（高端金融、奢侈品）
- **Neo-native（mobile/desktop）** —— 极度尊重系统语汇，系统字体 + 系统动画曲线 + 系统组件，美学是"像系统自带的一样"（Things 3、Tot、NetNewsWire）
- **Material expressive（Android）** —— Material Design 3 的彩色主题 + 动态配色 + 物理感 motion

每一派都有它自己的语言体系，"好不好"要在派内评判。

**不同平台典型的风格选择**：
- Web 百花齐放，每一派都有代表
- 原生 macOS / iOS app 主流是 "Neo-native" 或 "Precise tool"
- Electron 桌面应用如果成功，通常是 "Precise tool"（Linear、Figma、Raycast）
- Android 原生常是 "Material expressive" 或 "Neo-native"
