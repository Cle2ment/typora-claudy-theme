# AGENTS.md

## 项目概述

Typora 主题「Claudy」，纯 CSS 无构建。两个主题文件：

- `claudy.css` — 浅色
- `claudy-dark.css` — 深色

## 目录结构

```
claudy.css / claudy-dark.css            # 主题本体（Typora 主题文件夹直接使用）
image/                                    # README 截图（README 用相对路径引用）
try.md                                    # 主题预览/投稿文档（带 frontmatter）
README.md                                 # 中英双语文档（中文在前，英文在 #english-version 锚点后）
.github/workflows/release-latest.yml      # 发布流水线
```

## 开发约定

- **双主题同步维护**：改样式通常要同时改两份 CSS（版心、字体、代码高亮逻辑一致，仅配色/对比度独立调校）。
- **Windows 特例**：`.os-windows` 作用域规则单独覆盖 UI 字体/菜单样式，新增 UI 覆盖时注意同步。
- **验证方式**：无构建无测试。改完在 Typora 中切换主题目测验证；CSS 语法可用编辑器 LSP 检查。
- **README 双语**：中文区和英文区内容一一对应，改 README 必须双语同步修改。

## 发布流程

- 推 `v*` tag 发版本 release（makeLatest），推 `Stable` tag 发稳定版（title 自动解析为最新 v* tag）。
- workflow 打包 `Typora_Claudy_Theme.zip`（含两个 CSS）并上传 CSS + zip 为 release artifacts。

## 提交规范

Conventional Commits 前缀 + 中文描述，如 `docs: README 末尾追加 Star History 图表`、`ui: 将侧栏字体覆盖改为全平台`。常用前缀：`ui` / `fix` / `docs` / `ci` / `chore`。

## 其他

- `.codegraph/`、`.code-review-graph/` 为本地工具缓存，已 gitignore，勿提交。
- `*.zip` 不入库。
