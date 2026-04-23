# PPT-FLUX Studio TODO

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
