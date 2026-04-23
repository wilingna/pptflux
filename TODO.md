# PPT-FLUX Studio TODO

已知优化点（按优先级）

## 高优先级

- [ ] **Commit 3: SHARED_CSS 抽取** — 把 Commit 2 内联的 variant 样式抽到 `SHARED_CSS` 做统一管理
- [ ] **Commit 4: Agent 4 prompt 加硬约束** — 让真 API 生成也遵守 variant 系统
- [ ] **Commit 5/6: 扩展到 12 种风格** — 先做 3 个：Neon Cyber / Paper & Ink / Pastel Geometry

## 中优先级

- [ ] **内容密度自适应** — 当 bullet 内容过短时，所有 variant 都应该有优雅降级策略，不只是 process-v3
- [ ] **`pickProcessVariant` 关键词表扩展** — 收集更多真实场景的触发词（目前 stair 关键词略少）

## 低优先级

- [ ] **insight 权重分布（v1/v2/v3 = 50/30/20）样本验证** — 在短 PPT（<12 页）里样本不足，需要长 PPT 真实测试验证
- [ ] **`retrySinglePage` 超时 20 秒边界调整** — 在 Opus 4.7 极端情况下可能边界命中，真实跑起来再调整
