# AGENTS.md

## 项目规则（必须遵守）

1. **命名前缀**：所有 CSS 类名、id 名、JS 变量一律以 `cmq_` 开头（如 `.cmq_card`、`#cmq_nav`、`let cmq_count`）。新写的代码必须遵守；既有旧文件不因此批量重命名。
2. **HTML 注释**：所有 HTML 页面顶部必须加入注释，格式如下（日期用当天实际日期，功能名称用中文简述页面用途）：
   ```html
   <!-- 姓名：蔡美琪，日期：YYYY-MM-DD，功能名称：XXX -->
   ```
   规则生效前已存在的旧文件不因此批量改动。
3. **提示词记录**：每条提示词必须在**执行之前**以**追加**方式写入 `cai_prompt.md`，永不覆盖已有内容。每条记录包含三部分：时间（格式 `yyyy-mm-dd-hh-mm`）、使用的模型、提示词原文。按文件原有条目格式继续追加（`## 时间` + `- 模型:` + `- 提示词:`）。
4. **首页链接**：新建的 HTML 文件必须加入指向 `1.html`（首页，"蔡美琪的《高级网页设计》课堂实践"）的超链接，例如 `<a href="1.html">返回首页</a>`，保证从新页面能回到首页。规则生效前已存在的旧文件不因此批量改动。

## 技术栈

- 使用**原生 HTML + CSS + JavaScript** 实现，不使用任何第三方库、框架或 CDN 链接（如 jQuery、Bootstrap、CDN font-awesome 等）。
- 数据请求统一使用原生 `fetch` API。
- 图标统一使用 `font/` 目录下的 **iconfont** 字体图标（`font/iconfont.css` + 字体文件）或 SVG 内联方式，不引入外部图标库。
- 规则生效前已引入的资源文件（如 `cdn/` 目录下的 font-awesome、lucide）不因此删除，仅对新写的代码生效。

## What this repo is

- Static HTML/CSS/JS only: no package.json, no build/test/lint commands, no CI. Do not add tooling unless asked.
- Verify changes by opening the file in a browser (`file://`); there is no dev server.
- No third-party libraries, no external CDN assets — everything must work offline via relative paths.

## File roles

- `index.html` (~2000 lines) is the main deliverable: a single-page site ("山野植物手册") with **all CSS inline in one `<style>` block**. Style changes belong there; there is no external stylesheet for it.
- Files named `N-M topic.html` (2-x … 10-x, 13-x, 14-x …) are independent course exercises (links, forms, box model, flex, selectors, transitions, animations, iconfont, JS basics). Each is fully self-contained.
  - Do not refactor across exercise files or "fix" their inconsistencies (`lang="zh"` vs `zh-CN` vs `en`, indentation, spacing) — they are lesson snapshots.
  - They link to each other only occasionally and are not linked from `index.html`.
- `css.css` and `网页元素1原图-植物分类导航.svg` are **referenced by nothing**. Don't wire them up or "clean up" by deleting without being asked.
- `font/` 目录存放 iconfont 字体图标资源（`iconfont.css` + `.woff2`/`.woff`/`.ttf`），新项目图标统一从这里引入。
- `cdn/` 目录存放历史引入的第三方图标库（font-awesome、lucide），规则生效后新代码不再使用。

## Conventions

- Encoding: UTF-8 without BOM, `<meta charset="UTF-8">` in every file. Keep it that way; content is Chinese.
- Filenames contain Chinese characters and spaces (e.g. `5-1 层叠与继承.html`, but `7-1上图下文.html` has no space — name patterns are not consistent). Always quote paths; in PowerShell set `[Console]::OutputEncoding = [Text.Encoding]::UTF8` to see them correctly, and never rename files to "fix" names.
- All assets are referenced relatively from the shared `img/` dir (`./img/s*.jpg` in `index.html`, `./img/1-9.jpg` etc. in exercises). Keep references relative so pages open directly from disk.
