# PPTFlux TODO

## 已知优化点（按优先级）

### 高优先级

- [x] Commit 1: 漏页基础修复
- [x] Commit 2: buildLocalSlide variant 重构
- [ ] Commit 3: SHARED_CSS 抽取（把 Commit 2 内联的 variant 样式抽到 `SHARED_CSS` 做统一管理）
- [ ] Commit 4: Agent 4 prompt 硬约束 + Agent 3 内容连贯性
  - 子项：Agent 3 SYS 加「编号概念首次出现必须定义」硬约束（防止只讲阶段2/3 不讲阶段1）
  - 子项：Agent 4 prompt 读 variant 字段并严格按 variant 生成
- [ ] Commit 5/6: 扩展到 12 种风格（先做 3 个：Neon Cyber / Paper & Ink / Pastel Geometry）

### 中优先级

- [ ] nav-dots tooltip + 点击跳页（对标 Zara frontend-slides 的右侧导航）
- [ ] 内容密度自适应：所有 variant 面对短文本时的优雅降级
- [ ] 真 API 本地兜底触发频率监控：收集数据决定是否要增强 `retrySinglePage`（目前 20s 超时 + 4000 tokens 非流式可能不够）
- [ ] process-v3 redesign 扩展：stair 形态的 6 步测试、circular 形态的 6 步测试
- [ ] `pickProcessVariant` 关键词表扩展：收集更多真实场景的触发词（目前 stair 关键词略少）
- [ ] 重写 `verify-variants.js` 的 variant 分类器 —— 从 eyebrow 字符串匹配（`READING ·` / `BEFORE · 现状` / `FRAMEWORK ·` 等）改为基于 section innerHTML 的结构特征匹配（`.insight-wrap` / `.hook-stat` / `.data-cards` / 双色背景 flex / SVG 弧形 `<path ... stroke=` 等），脱离文本依赖。Round 4 删 eyebrow 后该分类器已失效，当前只靠 adjacent-diversity 结构检查仍在工作

### UI / 品牌视觉优化（独立 commit，在 Commit 4 之后做）

- [ ] UI 主色改为冷白 `#E8E4D8` 或珍珠灰 `#C0C0C5`（避免和产品内 12 种风格撞色）
- [ ] 主背景改炭黑 `#121212`（Linear/Raycast 方案，替代纯黑）
- [ ] Step 3 风格卡片加迷你预览缩略图（每个风格 60×40px SVG 示例）
- [ ] 右侧面板 living preview（Step 填入实时反馈）
- [ ] 衬线字体换 Fraunces / 思源宋体
- [ ] 输入框占位符字重和对比度调整

### 低优先级

- [ ] insight 权重分布（v1/v2/v3 = 50/30/20）在长 PPT 的真实分布验证
- [ ] `retrySinglePage` 超时可能需要从 20s 调到 25s（Opus 4.7 边界）
- [ ] CSS 孤儿规则清理（Round 4 删除后留下的无 HTML 引用规则）：`.hook-eyebrow`（`index.html:1597`）、`.data-eyebrow`（`:1608`）、`.insight-eyebrow`（`:1644`）、`.action-eyebrow`（`:1653`）、`.slide-bg-num`（`:1370`，改动 3 后唯一剩余引用在 `buildTitleSlide` 的 `✦` 星形装饰，仍在使用所以此条暂不是完全孤儿——确认标题页 ✦ 保留与否后再统一处理）
- [ ] Notebook Tabs 署名融入纸卡设计 —— 将 `.slide-signature` 从卡外 margin 移入 `.paper-card` 内部紧挨 `tab-strip` 上方或 paper 右下角内，作为"笔记本纸张水印"的设计语言一部分，需调整 6 处 `buildNotebookSlide` 的 wrap 模板。当前（Round 4 改动 4）用风格 CSS 覆盖把 signature 挪到卡外左下 margin 作为临时避让方案
- [ ] UI brand 锁头改造 —— `index.html:484-486` 顶部 `PPT·FLUX / Studio` 三层 typographic 处理（`.brand-serif` 斜体金色 `·` / `.brand-sep` 分隔符 `/` / `.brand-sub` "Studio" 小字）需要随品牌改名（PPTFlux）一起重做视觉。改造完成后，3 条 CSS 规则（`.brand-serif` / `.brand-sep` / `.brand-sub`）可能全变孤儿，届时一起清理
- [ ] Bold Signal 粒子动效感知问题 —— 当前 `initParticleTrail`（`index.html:1832`）是鼠标轨迹粒子，鼠标不动就无粒子；shoot.js 截图时还显式 `display:none`。Halina 感知"粒子消失"是因为静态观察 / 截图场景看不到。**代码未被删除，无需恢复**。待评估：是否需要为 Bold Signal 加一套"不依赖鼠标"的环境粒子/星光（类似 Dark Botanical 的 `.slide-orb` 静态浮光），作为风格语言的一部分
