# 🎯 PPT-FLUX Studio

> AI 四段式流水线，从零散资料到可交付 HTML 演示文稿，全程一键生成

🔗 **直接使用：[wilingna.github.io/ppt-flux-studio](https://wilingna.github.io/ppt-flux-studio/)**

---

## 这是什么？

PPT-FLUX Studio 是一个基于 **4 个 AI Agent 串联**的演示文稿生成器，输入主题或上传资料，自动输出可直接使用的 HTML 幻灯片。

无需安装，无需 API 配置（自带 OpenRouter Key 输入框），打开即用。

---

## 工作流程

```
资料 / 主题
    ↓
Agent 1 · 资料理解（NotebookLM 式梳理）
    ↓
Agent 2 · 结构大纲（页数 · 逻辑 · 布局规划）
    ↓
Agent 3 · PPT 内容（Gemini 黄金标准表达）
    ↓
Agent 4 · HTML Slides 渲染（前端 Slides 风格）
    ↓
可编辑 HTML 文件 ↓ 下载
```

---

## 核心功能

- **6 种视觉风格**：Bold Signal / Dark Botanical / Creative Voltage / Notebook Tabs / Swiss Modern / Electric Studio
- **6 种布局类型**：hook / data / process / compare / insight / action，AI 按内容自动选择
- **每页独立创意**：每张幻灯片有粒子效果、3D tilt、数字动画，互不干扰
- **内联编辑器**：生成后可直接在页面点击修改文字，Ctrl+S 保存
- **分批生成**：每 4 页一批调用 API，失败自动重试，保证成功率
- **文件上传**：支持 PDF / Word / 图片 / PPT 等多格式资料解析

---

## 使用方法

1. 打开 [wilingna.github.io/ppt-flux-studio](https://wilingna.github.io/ppt-flux-studio/)
2. 填入 OpenRouter API Key（[免费获取](https://openrouter.ai/)）
3. 输入汇报主题，上传资料（可选）
4. 选择风格和页数，点击生成
5. 预览满意后下载 HTML 文件

---

## 技术栈

- **前端**：纯 HTML / CSS / JavaScript，零依赖
- **API**：OpenRouter → `anthropic/claude-sonnet-4-5`
- **部署**：GitHub Pages，静态托管

---

## 相关项目

| 项目 | 说明 |
|------|------|
| [ai-ppt-toolkit](https://github.com/wilingna/ai-ppt-toolkit) | NotebookLM + Gemini + Gamma 三件套工作流 |
| [ai-ppt-web](https://github.com/wilingna/ai-ppt-web) | 乱资料 → 可交付 PPT 网页工具 |
| [ai-content-pipeline](https://github.com/wilingna/ai-content-pipeline) | 7 Agent 多平台内容生产流水线 |

---

Built by [@wilingna](https://github.com/wilingna) · AI Systems · Agents · Decision Engines
