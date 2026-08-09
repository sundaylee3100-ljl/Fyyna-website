# Fyyna 网站修改计划

## Summary
根据客户附件中的反馈，对 Fyyna 中英文网站进行多项修改，包括品牌名替换、广告法敏感词修正、图片显示修复、产品卡片删除、工艺模块重排序及交互增强。

## Current State Analysis
- 项目为静态 HTML 网站，包含 `index.html`（英文）、`zh.html`（中文）及 `css/style.css`
- 中文页面存在品牌名"飞纳"需统一替换为"颇拓机电"
- 产品卡片图片使用 `object-fit: cover` + 固定高度 `220px`，导致图片被裁剪、显示不完整
- 工艺能力模块顺序与客户期望不符
- 工艺能力卡片点击后无关联产品展示交互

## Proposed Changes

### 1. 品牌名替换（zh.html）
- **What**: 全局替换"飞纳"为"颇拓机电"
- **Where**: title、section-label、正文段落等
- **How**: 文本级 SearchReplace

### 2. 广告法敏感词修正（zh.html）
- **What**: "中国领先" → "专业"
- **Where**: 关于我们第一段

### 3. 产品卡片图片完整显示（css/style.css）
- **What**: `.product-card-img` 由 `object-fit: cover` 改为 `object-fit: contain`，使用 `aspect-ratio` 保持比例
- **Why**: 图片被裁剪，无法完整展示零件全貌

### 4. 删除难看产品卡片
- **What**: 删除 CNC 加工"滑阀"卡片及对应图片 `machining-5.jpg`

### 5. 工艺能力模块重排序
- **What**: 中英文页面 capabilities-grid 内卡片按客户标注重新排列
- **新顺序**: CNC Machining → Tube Bending → Fabrication → Custom Fittings → Stamping → Die Casting → Investment Casting → Sand Casting → Forging → Spinning

### 6. 工艺卡片点击跳转+自动筛选
- **What**: 点击能力卡片 → 滚动到产品区域并自动激活对应筛选标签

## Verification
- 本地启动 HTTP 服务器预览
- 逐条核对修改效果
