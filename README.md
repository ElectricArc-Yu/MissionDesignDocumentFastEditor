# MDD Quick Editor

[English](#english) | [简体中文](#简体中文)

---

<a id="english"></a>
## English

A purely browser-based **Mission Design Document (MDD)** quick editor. Single HTML file, runs out-of-the-box with no installation or backend required. Fill in your level design following a structured template, and export to Word, PPT, or PDF in one click.

**Live Demo:** <https://electricarc-yu.github.io/MissionDesignDocumentFastEditor/>

### Features

- **WYSIWYG A4 Landscape Pages**: Click grey `[placeholders]` to edit directly. Selected text supports bold, italic, bullet lists, or red highlight (used to highlight "Current Level").
- **Fixed MDD Section Structure**: Overview (Cover) → Context → Mission Walkthrough → Layout Plan Legends → 2D Layout Plan → Flow → Beats → Battle Intensity → Appendices A–E (see below).
- **Image Handling**: Click image slots to upload, drag-and-drop, or paste from clipboard; supports rotation, flipping, cropping, and brightness/contrast adjustments. Original images are always preserved at full resolution.
- **Auto-generated Charts**: Flow diagrams, Beats Chart, Beats Timeline, and Battle Intensity curves are all dynamically generated based on your input data.
- **Version Control**: Once marked as initial version complete, each subsequent save performs field-by-field diff comparison against the previous version, automatically logging changes, reasons, and remarks into Appendix E.
- **Export Options**: Word (.docx), PPT (.pptx), and PDF — all formatted as A4 landscape with headers and footers.
- **Project Files**: `Download project` bundles everything into a `.zip` archive (`project.json` + `pic/` source images folder). Load it anytime via `Open project` to resume editing. Drafts are also auto-saved in your browser (IndexedDB).

### Quick Start

1. Visit the [Live Demo](https://electricarc-yu.github.io/MissionDesignDocumentFastEditor/) or open the local `MDD_Editor.html` in any modern browser.
   *Libraries required for export are loaded via CDN; internet access is required on first launch.*
2. Click **Document setup** to configure Game Name, Level Name, Level Number, Lead Designer, and Campaign Hierarchy (e.g., Campaign → Chapter).
3. Fill in content and upload images section by section. Click **Preview export** at the top right to preview the final export layout.
4. When content is finalized, click **Mark initial version complete** to lock cover details and initialize revision tracking.
5. For subsequent updates, click **Save draft**, choose the change severity (Minor / Major / New full build), and provide reasons for modification.
6. Use **Export Word / PPT / PDF** to export, and **Download project (.zip)** to back up your project.

### Example

The `Mock_POI/` folder provides a complete sample mission (a fictional level "Exposed" inspired by TV series *Person of Interest* S5E10):

| File | Description |
| --- | --- |
| [`Exposed_MDD.zip`](Mock_POI/Exposed_MDD.zip) | Project archive, open via **Open project (.zip)** to inspect and edit |
| [`POI_5.10.1_Exposed_MDD.docx`](Mock_POI/POI_5.10.1_Exposed_MDD.docx) | Exported Word document |
| [`POI_5.10.1_Exposed_MDD.pptx`](Mock_POI/POI_5.10.1_Exposed_MDD.pptx) | Exported PPT presentation (excluding cover) |
| [`POI_5.10.1_Exposed_MDD.pdf`](Mock_POI/POI_5.10.1_Exposed_MDD.pdf) | Exported PDF document |

Syntax notes from the example:

**Hierarchy & Numbering**: Hierarchy is set to `Season 5` → `Episode 10`, Level Number is `1`, yielding a cover identifier of `5.10.1`. Headers display the name of each hierarchy level.

**Version String**: Formatted as `Ver.Build.Major.Minor-Date.CumulativeSaves`. The example version is:

```
Ver.1.01.0001-2026.10.31.0000,0004
```

**Combat / Rest / Event Tags in Mission Walkthrough**: Enter compact tags inside Actions. During export, they are converted into human-readable text and plotted on the battle intensity curve.

```
Sit at the window table (look at the camera to talk) !(20)
Order a coffee, waitress greets Finch !(e1)
Defend the safe house as Reese and Shaw !(b2,35)
```

| Tag | Meaning | Export Display |
| --- | --- | --- |
| `!(b1,45)` | Fight unit b1 for 45 seconds | `[Battle: Name (45s)]` |
| `!(30)` | Rest for 30 seconds (intensity decays) | `[Rest: 30s]` |
| `!(e1)` | Trigger event e1 | `[Event: Name (Time)]` |
| `? ...` | Line starting with `?` (after its number) is optional and excluded from all statistics | grey `[Option] ...` |

Units, enemy types, events, and intensity decay rates (default: -2 per 30s) are configured under **Battle data** in the top bar.

### Appendices

| Appendix | Content |
| --- | --- |
| A - Preceding Process Result | Process name, 1 / 3 / 9 captioned 16:9 images (or none) and three text blocks. Filled images move to the front. Read-only once the initial version is marked complete. |
| B - Project Specification | Item / Spec / Info table, e.g. `Character move speed, jump distance` / `10 UU/s, 400 UU`. **+ Image** adds a picture to a cell. |
| C - Applied Guidelines | Index / Name / Brief / Detail. Ticked **Global** guidelines come first with red indices. **+ Cite** takes a web address or a BibTeX entry; cites are listed in two columns under the table. **Copy global guidelines** copies them as CSV; **Import CSV from clipboard** reads CSV or TSV (`Global,Name,Brief,Detail,Cite`). |
| D - PO List | Paint-over entries with PO / Finish times and optional Unreal camera. |
| E - Minor Modify List | Filled in automatically on every save, including changes to Appendix B and C. |

### Tips

- **Hide empty on export**: When enabled, empty fields, placeholder images, and entirely empty sections are omitted from export. When disabled, placeholders are preserved to export as a blank template.
- A **red border** around a page indicates content overflow. Shorten the text or adjust the layout to fit within the page.
- Browser drafts are stored locally. Always use **Download project** before switching computers or clearing site data.
- Click **Help** at the top right for complete documentation and shortcuts.

### Deployment

Pushing to `main` triggers GitHub Actions ([`.github/workflows/static.yml`](.github/workflows/static.yml)), which copies `MDD_Editor.html` to `index.html` and deploys it to GitHub Pages.

### License

[AGPL-3.0](LICENSE)

---

<a id="简体中文"></a>
## 简体中文

一个纯浏览器端的 **关卡任务设计文档（Mission Design Document, MDD）** 快速编辑器。只有一个 HTML 文件，打开就能用，不需要安装或后端。在页面上按固定模板填写关卡设计，再一键导出 Word / PPT / PDF。

**在线使用：** <https://electricarc-yu.github.io/MissionDesignDocumentFastEditor/>

### 功能一览

- **所见即所得的 A4 横版页面**：点击灰色 `[占位符]` 直接输入，选中文字可加粗、斜体、列表，或标红（标记“当前关卡”）。
- **固定的 MDD 章节结构**：Overview（封面）→ Context → Mission Walkthrough → Layout Plan Legends → 2D Layout Plan → Flow → Beats → Battle Intensity → Appendix A–E（见下文）。
- **图片**：点击图片框上传，也可以拖拽或粘贴；支持旋转、翻转、裁剪、亮度/对比度调节，原图始终按原分辨率保留。
- **自动生成的图表**：流程图（Flow）、节奏图表（Beats Chart）、节奏时间线（Beats Timeline）、战斗强度曲线，都根据填写的数据自动绘制。
- **版本管理**：标记初版完成后，每次保存都会和上一版逐字段比对，把改动连同原因、备注写入 Appendix E。
- **导出**：Word（.docx）、PPT（.pptx）、PDF，均为 A4 横版并带页眉页脚。
- **项目文件**：`Download project` 打包为 `.zip`（`project.json` + `pic/` 原图文件夹），之后可用 `Open project` 打开继续编辑。草稿也会自动保存在浏览器里（IndexedDB）。

### 快速开始

1. 打开 [在线页面](https://electricarc-yu.github.io/MissionDesignDocumentFastEditor/)，或直接用浏览器打开本地的 `MDD_Editor.html`。
   *导出功能用到的库从 CDN 加载，首次使用需要联网。*
2. 点击 **Document setup**，填写游戏名、关卡名、关卡序号、负责人，以及战役层级（如 Campaign → Chapter）。
3. 在页面上逐节填写内容、上传图片。右上角 **Preview export** 可以预览最终导出效果。
4. 内容定稿后点击 **Mark initial version complete**，锁定封面信息并开始版本记录。
5. 之后每次 **Save draft** 选择改动级别（Minor / Major / New full build），并填写修改原因。
6. 用 **Export Word / PPT / PDF** 导出，用 **Download project (.zip)** 备份工程。

### 示例

`Mock_POI/` 文件夹里是一份完整的示例关卡（以美剧《Person of Interest》S5E10 为题材的虚构关卡 “Exposed”）：

| 文件 | 说明 |
| --- | --- |
| [`Exposed_MDD.zip`](Mock_POI/Exposed_MDD.zip) | 工程文件，用 **Open project (.zip)** 打开即可查看和编辑 |
| [`POI_5.10.1_Exposed_MDD.docx`](Mock_POI/POI_5.10.1_Exposed_MDD.docx) | 导出的 Word |
| [`POI_5.10.1_Exposed_MDD.pptx`](Mock_POI/POI_5.10.1_Exposed_MDD.pptx) | 导出的 PPT（不含封面页） |
| [`POI_5.10.1_Exposed_MDD.pdf`](Mock_POI/POI_5.10.1_Exposed_MDD.pdf) | 导出的 PDF |

示例中的一些写法：

**层级与编号**：层级为 `Season 5` → `Episode 10`，关卡序号为 `1`，所以封面编号为 `5.10.1`，页眉显示各层名称。

**版本号**：格式为 `Ver.Build.Major.Minor-日期.累计保存次数`，示例当前版本为：

```
Ver.1.01.0001-2026.10.31.0000,0004
```

**Mission Walkthrough 中的战斗 / 休息 / 事件标记**：在 Actions 里写简短标记，导出时会替换成可读文字，并计入战斗强度曲线。

```
Sit at the window table (look at the camera to talk) !(20)
Order a coffee, waitress greets Finch !(e1)
Defend the safe house as Reese and Shaw !(b2,35)
```

| 标记 | 含义 | 导出显示 |
| --- | --- | --- |
| `!(b1,45)` | 与战斗单位 b1 战斗 45 秒 | `[Battle: 名称 (45s)]` |
| `!(30)` | 休息 30 秒，期间强度衰减 | `[Rest: 30s]` |
| `!(e1)` | 触发事件 e1 | `[Event: 名称 (发生时间)]` |
| `? ...` | 以 `?` 开头（不计序号）的条目为可选项，不计入任何统计 | 灰色 `[Option] ...` |

战斗单位、敌人类型、事件、强度衰减规则（默认每 30 秒 -2）都在顶部的 **Battle data** 里设置。

### 附录

| 附录 | 内容 |
| --- | --- |
| A - Preceding Process Result | 前置流程名称、1 / 3 / 9 张带题注的 16:9 图片（也可不放图）和三段文字，已上传的图片自动排到前面。标记初版完成后不可再改。 |
| B - Project Specification | Item / Spec / Info 三列表格，如 `角色移动速度、跳跃距离` / `10 UU/s, 400 UU`。**+ Image** 可在单元格中插图。 |
| C - Applied Guidelines | Index / Name / Brief / Detail 四列。勾选 **Global** 的条目排在最前，序号标红。**+ Cite** 可插入网页地址或 BibTeX，引用在表格下方分两栏列出。**Copy global guidelines** 把全局条目复制为 CSV；**Import CSV from clipboard** 从剪贴板导入 CSV 或 TSV（`Global,Name,Brief,Detail,Cite`）。 |
| D - PO List | Paint-over 记录，含 PO / Finish 时间和可选的 Unreal 摄像机信息。 |
| E - Minor Modify List | 每次保存自动记录，包括 Appendix B、C 的改动。 |

### 小贴士

- **Hide empty on export**：开启时，空字段、空图片和整个空章节不会导出；关闭时会保留所有占位符，可以当空白模板导出。
- 页面出现**红色边框**说明这一页内容溢出，需要精简内容或调整布局。
- 浏览器草稿只保存在当前浏览器，换电脑或清除站点数据前请先 **Download project** 备份。
- 右上角 **Help** 有完整的功能说明。

### 部署

推送到 `main` 后，GitHub Actions（[`.github/workflows/static.yml`](.github/workflows/static.yml)）会把 `MDD_Editor.html` 复制为 `index.html` 并发布到 GitHub Pages。

### 许可证

[AGPL-3.0](LICENSE)
