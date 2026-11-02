# PPTX 演示文稿 · PowerPoint Toolkit

> 创建、读取、编辑 .pptx/.potx：幻灯片、版式、备注、模板；含 pptxgenjs 生成与 OOXML 直接编辑两条路径

![Type](https://img.shields.io/badge/type-Agent%20Skill-4a6b7c)
![Upstream](https://img.shields.io/badge/upstream-pptx%20v1.0.0%20-%20©%202025%20Anthropic,%20PB-8f8a80)
![License](https://img.shields.io/badge/license-见 LICENSE-b8935a)

> ⚠️ 本仓库是个人使用环境中的 Skill 归档副本，**版权归原提供方**：pptx v1.0.0 · © 2025 Anthropic, PBC. All rights reserved.

## 这是什么

一套处理 `.pptx` / `.potx` 的完整工具箱，覆盖**新建、读取、编辑、模板复用、QA** 全流程。

## 两条技术路径

| 路径 | 适用 | 说明 |
|---|---|---|
| `pptxgenjs` | 从零生成 | 写 JS 生成幻灯片，样式控制直接 |
| OOXML 直接编辑 | 改已有文件 | 解压 → 改 `ppt/slides/slideN.xml` → 重打包 |

改已有演示文稿时**必须走 OOXML**：用生成库重写会丢掉母版、主题和动画。

## 常见操作

- 调整页序 / 删除页：编辑 `ppt/presentation.xml` 的 `<p:sldIdLst>`
- 修改单页内容：改 `ppt/slides/slideN.xml`
- 读取备注：解析 `ppt/notesSlides/`
- 转图片预览：用脚本渲染后逐页检查

## 设计建议（skill 内置）

配色不超过三组、标题层级靠字号不靠加粗、每页一个主张、图表优先于表格。`SKILL.md` 的 Design Ideas 段有可直接套用的版式清单。

## QA（强制）

生成或编辑后**必须**渲染成图片逐页看：文字溢出、元素重叠、字体回退、图片裁切——这四类问题在 XML 层面看不出来，只能看渲染结果。

## 目录结构

```
pptx/
├─ SKILL.md
├─ README.upstream.md       原包自带说明
├─ LICENSE.txt              原许可（未改动）
├─ scripts/                 生成 / 编辑 / 渲染脚本
├─ schemas/                 OOXML 结构参考
└─ references/              设计规范与操作细则
```

## 许可

**© 2025 Anthropic, PBC. All rights reserved.**

本仓库为个人环境中的归档副本，`LICENSE.txt` 原样保留，**不在 MIT 授权范围内，不作出任何再许可**。使用受你与 Anthropic 之间的协议约束，详见 `LICENSE.txt` 与 `NOTICE.md`。


## 安装

```bash
git clone https://github.com/px-pangu/pptx.git ~/.workbuddy/skills/pptx
# Claude Code：~/.claude/skills/pptx
```

> 若原包依赖 CLI（如 `kdocs`、`ima`、`wecom`、`pdfkit`），需先按 `SKILL.md` 的安装与认证段落配置本机环境。**仓库内不含任何凭据。**

