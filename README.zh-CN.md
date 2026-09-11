# xhs-tool-launch · 小红书工具图文推广

[English](README.md) | 简体中文

一个把 AI 技能、软件工具和独立产品做成小红书宣传图文的 Codex skill。先展示工具的使用效果，让读者看懂价值，再介绍用途与上手方式。

覆盖选题、逐页文案、视觉设计、图片生成、校对和发布包交付。

## 你会得到什么

- 有具体演示支撑的选题和封面标题。
- 包含准确文案与布局的分页大纲。
- 风格统一、经过文字与可读性检查的系列图片。
- 发布标题、正文、相关话题和获取入口。
- 可复用的出图提示词，以及包含成品图片和正文的 ZIP。

只问“怎么宣传”时交付方案与文案。要求完整制作时，需要可用的图片生成工具；在 Codex 中优先使用内置图片生成能力和 `imagegen` 技能。没有图片生成能力时可以准备文案与提示词，但不能交付成品图片。

## 安装

需要已安装 Git 和支持本地技能的 Codex。

**Windows（PowerShell）**

```powershell
$skillRoot = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME 'skills' } else { Join-Path $env:USERPROFILE '.codex\skills' }
New-Item -ItemType Directory -Path $skillRoot -Force | Out-Null
git clone https://github.com/MogooStudio/xhs-tool-launch.git (Join-Path $skillRoot 'xhs-tool-launch')
```

**macOS / Linux**

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/MogooStudio/xhs-tool-launch.git "${CODEX_HOME:-$HOME/.codex}/skills/xhs-tool-launch"
```

如果目标目录已经存在，先检查内容，避免覆盖已有文件。安装后在 Codex 技能列表中查找 `xhs-tool-launch`；当前会话未识别时，重新打开会话再试。

## 使用

提供仓库链接、README、截图，或一段工具介绍和使用效果即可。

**先做策划**

```text
用 $xhs-tool-launch 帮我策划这个工具的小红书宣传，给出选题、逐页文案、视觉方向和发布正文。
```

**直接制作整套图文**

```text
用 $xhs-tool-launch 为这个工具制作 6 张小红书宣传图，先展示效果，再介绍用法，交付图片、发布正文和 ZIP。
```

**调整风格与数量**

```text
用 $xhs-tool-launch 做 4 张图，沿用我的品牌色，面向设计师，把效果对比作为重点。
```

## 默认叙事与视觉

从 **封面 → 输入或痛点 → 核心效果 → 第二案例 → 怎么控制 → 上手入口** 的六页结构起步，按素材合并或删减，不强行凑页数。

默认使用 3:4 竖图、米白纸面、黑色大字和克制的红色批注。先生成封面，再把封面作为后续页面的风格参考。页数、配色和布局可以按产品与要求调整。

附带的 [编辑批注参考](references/editorial-cards.md) 收录了为 [sharp-roast](https://github.com/MogooStudio/sharp-roast) 制作的六页推广案例，包括文案、布局和提示词结构。它是可复用的设计起点，不代表平台算法规律，也不承诺流量表现。

## 交付目录

```text
image-cards/<topic>/
  outline.md
  post.md
  prompts/
  01-cover.png
  02-setup.png
  ...
  <topic>-xhs.zip
```

ZIP 只包含按上传顺序排列的成品图片和 `post.md`。大纲、提示词留在源目录，方便后续修改。

虚构案例会明确标注，文案摘录与原始截图会区分；项目名、调用指令和页码会在成品图上核对。制作发布包不会自动发帖或推送仓库，实际发布和推送需由用户明确提出。

## 技能文件

- [SKILL.md](SKILL.md)：中文工作流指令。
- [references/editorial-cards.md](references/editorial-cards.md)：视觉预设、提示词框架和完整案例。
- [agents/openai.yaml](agents/openai.yaml)：Codex 显示信息与默认提示词。

## 许可证

[MIT](LICENSE)。
