# PPTFlux

> 一个超级个体用 4 周时间端到端做出的 AI PPT 工具。
> 输入资料 → 一份能直接演示、可交互、可继续编辑的 12–15 页 HTML 幻灯片。

🔗 **在线 demo**：[wilingna.github.io/pptflux](https://wilingna.github.io/pptflux/)
📜 **协议**：[MIT License](./LICENSE) — 随便用，做衍生项目不用问。

---

## 这是什么

PPTFlux 是一个 **纯前端单文件 HTML 的 AI PPT 生成工具**。一个网页搞定从"乱七八糟的资料"到"可以直接上台演示的幻灯片"全过程，不用导来导去、不用拼工具链。

它是我"AI 做 PPT 三件套"系列的**终极完成版**——后面会展开讲三件套到 PPTFlux 是怎么一步步演进过来的。

---

## 为什么值得 Star —— 你能从这里得到什么

### 🎯 一个工具走完全程，不再"复制粘贴接力赛"

以前用 AI 做一份像样的 PPT，至少要在 3 个工具之间来回搬：一个梳理大纲、一个润色表达、一个生成视觉。每跳一次就丢一次上下文，每跳一次就要手动对齐一次格式。

PPTFlux **把内容生产和视觉呈现打通成一个闭环**：粘资料 → 选风格 → 生成 → 直接演示。中间不用打开第二个标签页，不用复制 Markdown，不用导入再调样式。

### ✏️ 内容可控，**两层都能改**

这是 PPTFlux 和市面上"一键生成 PPT"工具最不一样的地方：

- **表达润色层可编辑** —— Agent 把内容写完后，你可以直接改文字、改金句、改 bullet 字数，再让它重新渲染。不满意结论？换一句重跑这一页就行
- **HTML 呈现层也可编辑** —— 生成的不是图片，是真正的 HTML。下载下来用任何编辑器打开，文字、颜色、布局、动效全都能改。不会写代码？让 Cursor 或 Claude 帮你改也行

意思就是：**AI 的产出是起点，不是终点。** 你永远能拿回控制权。

### ✨ 不是静态图片，是会动的交互式幻灯片

生成出来的每一页都是带粒子背景、鼠标尾巴动效、数字滚动动效、SVG 流程图动画的真·HTML 页面。

- 翻页有过渡，不是 PPT 那种生硬切换
- 鼠标移动会有跟随效果
- 数据页的大数字会从 0 滚到目标值
- 流程图的箭头是 SVG 动画，不是死图
- 暗黑底 + 高饱和点缀，自带"发布会"质感

复制 Markdown 进 Gamma 出来的那种"模板感很重的静态页"，和 PPTFlux 是两个东西。

### 🎨 6 套设计语言 × 18 种排版，相邻页绝不重样

每页布局都不同：6 个 layout（hook / data / process / compare / insight / action）× 3 个 variant = **18 种内容排版**，按页位 + 风格智能轮转派发。

6 套视觉风格各有自己的字体、留白、装饰元素，**不是换配色那种敷衍**：

| 风格 | 适合场景 |
|---|---|
| **Bold Signal** | 大字号强信号，发布会、宣讲 |
| **Dark Botanical** | 暗底植物剪影，沉稳叙事、深度报告 |
| **Creative Voltage** | 高饱和撞色，创意提案 |
| **Swiss Modern** | 极简网格，咨询报告底子 |
| **Electric Studio** | 工作室感，工具/产品介绍 |
| **Notebook Tabs** | 纸感笔记本，教学/复盘 |

### 🔒 数据本地，不绑平台

API Key 存你浏览器 localStorage，资料从你电脑出去只走 OpenRouter → 模型，中间没有任何"PPTFlux 服务器"。clone 下来双击 `index.html` 就能离线用。

---

## 三件套到 PPTFlux：四周三次跃迁

如果你也在做"AI 做 PPT"这件事，可能会对这条演进路径感兴趣：

### 🥇 [ai-ppt-toolkit](https://github.com/wilingna/ai-ppt-toolkit) (49 ⭐) — 方法论起点

**NotebookLM + Gemini + Gamma 三件套**：NotebookLM 梳理大纲 → Gemini 升级表达 → Gamma 生成视觉。

教你**为什么**这样做。三个工具各司其职，理解之后才知道"AI 做 PPT"不是一句 prompt 的事。

### 🥈 [ai-ppt-web](https://github.com/wilingna/ai-ppt-web) (13 ⭐) — 第一次合并

**Claude 替掉前两步，一个网页 + Gamma**。从三个工具压到两个，从手动接力压到自动衔接。但视觉那一步还得跳出去 Gamma，还是有断点。

### 🥉 PPTFlux (本仓库) — 闭环完成

**4 个 Agent 流水线，一个网页全部搞定**：
```
资料理解 → 结构大纲 → 表达升级 → HTML 渲染
```

连 Gamma 那一步都不用了。视觉呈现自己接管，做成 6 套设计语言 × 18 种排版的交互式 HTML。**到这一步，"AI 做 PPT"才真正变成了一个产品，而不是一条工作流。**

> 三件套帮你理解"为什么"，ai-ppt-web 帮你"快一点"，PPTFlux 帮你"一气呵成 + 完全可控"。三个仓库可以并存，按你的需求选。

---

## 内部实现简介（给好奇的朋友）

不是单一 prompt 黑盒，是 4 个有明确职责的 Agent + 工程化兜底：

| 阶段 | 职责 | 关键约束 |
|---|---|---|
| Agent 1 · 资料理解 | 判断受众真正关心什么、提炼主线、给取舍建议 | 不直接产出内容，只产出"判断" |
| Agent 2 · 结构架构 | 逐页大纲、核心问题、时间分配、叙事弧 | 12–15 页强约束，每页只回答一个问题 |
| Agent 3 · 表达升级 | 结论先行、正文 ≤ 60 字、Bullet ≤ 15 字、去 AI 味 | 字数硬上限 + 反 AI 套话词表 |
| Agent 4 · HTML 渲染 | 内容保持原样，按规范出交互式 HTML | post-processing 层强制统一品牌/页码 |

工程化兜底：漏页走 per-page recovery、错位用 slot-map 内容寻址、不一致过 `sanitizeAgentSlide` 后处理、`isValidSlideHtml` 内容校验、`retrySinglePage` 单页重试……

详见 [CHANGELOG.md](./CHANGELOG.md)，4 轮迭代每一轮解决了什么真实 bug 写得很清楚。

---

## 使用

1. 访问 [GitHub Pages 在线 demo](https://wilingna.github.io/pptflux/) 或 clone 仓库本地打开 `index.html`
2. 在设置里填入你的 OpenRouter API Key
3. 选择风格、填资料、生成
4. 在表达层调文字 → 重新渲染 → 演示 / 打印 PDF / 下载 HTML 继续魔改

推荐模型：**Claude Opus 4 / Sonnet 4**，通过 [OpenRouter](https://openrouter.ai/) 接入。其他模型也能跑，但 4 Agent 流水线对长上下文 + 指令遵循要求较高，弱模型容易在 Agent 3、Agent 4 翻车。

### 常见问题

**Q：报错 `API 错误 401: User not found`？**
A：OpenRouter 的 API Key 失效或账户欠费。去 [openrouter.ai/keys](https://openrouter.ai/keys) 重新生成 key 填进设置即可。这不是 PPTFlux 的 bug。

**Q：API Key 安全吗？**
A：Key 只存在你本地浏览器，代码完全开源可查，不经过任何第三方服务器。

**Q：每次生成多少钱？**
A：完整跑一次大约 $0.10–$0.30（取决于资料长度和模型），$5 充值够日常用很久。

**Q：能导出 PPTX / Keynote 吗？**
A：暂不支持。设计目标就是"一份能直接演示、能继续编辑的 HTML"——支持打印 PDF、下载 HTML 文件。要塞进 PowerPoint 里逐页编辑不是这个项目的方向。

**Q：生成中途某页空白 / 漏页？**
A：v0.1 之后已经做了单页重试 + 本地兜底，但弱模型仍可能触发。换 Claude Sonnet 4 以上基本不会出现。

---

## 技术栈

- 单文件 HTML + Vanilla JS，无构建，无依赖
- OpenRouter API Gateway
- Claude Opus / Sonnet 模型
- 部署在 GitHub Pages，源文件就一个 `index.html`

---

## 为什么写这个

我是一个超级个体创作者，做 AI 工作流方向。这个项目是我"超级个体作品集"之一 —— 想验证一件事：

> 作为一个人，能不能用 4 周时间端到端做出一个有产品感、有设计语言、能稳定输出的 AI 工具。

这不是一个商业产品。我不打算做付费版，也不打算做用户运营。它只是一份"超级个体能做到什么"的证明。

开发过程的复盘文章正在写，写完会更新链接在这里。

---

## 关于作者

**Halina** ([@wilingna](https://github.com/wilingna))，AI Systems Architect，做 AI 工作流 / 中国传统美学数字文化出海。

我的其他项目：

- [ai-ppt-toolkit](https://github.com/wilingna/ai-ppt-toolkit) — AI 做 PPT 三件套工作流（49 ⭐）
- [ai-ppt-web](https://github.com/wilingna/ai-ppt-web) — 三件套的网页版升级（13 ⭐）
- [ai-decision-5steps](https://github.com/wilingna/ai-decision-5steps) — 用 5 个 AI 工具做高质量决策（17 ⭐）
- [ai-content-pipeline](https://github.com/wilingna/ai-content-pipeline) — 7 个 Agent 自动跑内容生产线
- [zengen.art](https://zengen.art) — 中国神话美学剪纸 DIY 出海

如果这个项目对你有启发，欢迎点个 ⭐ Star，这是对超级个体创作者最直接的支持。
