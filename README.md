# xhs-tool-launch

English | [简体中文](README.zh-CN.md)

A Codex skill for turning AI skills, software tools, and indie products into Xiaohongshu (RED) promotional image posts. Show what the tool does, make the result easy to understand, then explain how to try it.

It covers the topic, page-by-page copy, visual direction, image generation, proofreading, and a ready-to-upload ZIP with post copy.

## What you get

- A concrete hook backed by a demonstration.
- A carousel outline with exact copy and layouts for each page.
- A consistent set of images, checked for text accuracy and readability.
- A post title, caption, relevant hashtags, and an access link.
- Saved image prompts and a ZIP containing the final images and post copy.

Planning-only requests receive an outline and copy. Full production requires an image-generation tool; in Codex, the skill prefers the built-in image generator and its `imagegen` skill. Without image generation, it can prepare the copy and prompts, but cannot deliver rendered images.

## Installation

You need Git and Codex with local skill support.

**Windows (PowerShell)**

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

If the destination already exists, inspect it before replacing anything. Look for `xhs-tool-launch` in Codex's skill list; reopen your session if it is not yet recognized.

## Usage

Provide a repository URL, README, screenshots, or a short description with an example of the tool's output.

**Plan a post**

```text
Use $xhs-tool-launch to plan a Chinese Xiaohongshu post for this tool. Give me the hook, page-by-page copy, visual direction, and caption.
```

**Produce the full set**

```text
Use $xhs-tool-launch to create a six-image Chinese Xiaohongshu post for this tool. Show the results first, then explain how to use it. Deliver the images, post copy, and ZIP.
```

**Customize the design**

```text
Use $xhs-tool-launch to create four images using my brand colors. Target designers, and make the output comparison the centerpiece.
```

## Default story and visual direction

The starting structure is **cover → input or pain point → main result → second example → controls → getting started**. Pages can be merged or removed when the material calls for it.

The default look uses 3:4 portrait cards, warm ivory paper, bold black typography, and restrained red annotations. The cover serves as a style reference for the remaining images. Page count, palette, and layouts adapt to the product and your brief.

The included [editorial reference](references/editorial-cards.md) documents the six-page campaign created for [sharp-roast](https://github.com/MogooStudio/sharp-roast), including its copy, layout choices, and prompt structure. This is a reusable starting point, not a claim about platform algorithms or guaranteed engagement.

## Deliverables

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

The ZIP contains only the approved images in upload order and `post.md`. The outline and prompts remain in the source directory for revisions.

Examples are labeled when fictional, excerpts are distinguished from original screenshots, and project names, commands, and page numbers are checked on the rendered images. Preparing a package does not automatically publish it or push it to a repository; those actions require an explicit request.

## Skill files

- [SKILL.md](SKILL.md): workflow instructions in Chinese.
- [references/editorial-cards.md](references/editorial-cards.md): visual preset, prompt framework, and campaign example.
- [agents/openai.yaml](agents/openai.yaml): Codex display metadata and default prompt.

## License

[MIT](LICENSE).
