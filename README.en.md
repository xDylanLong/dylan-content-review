# Dylan Content Workbench

> A Chinese-content Skill for Douyin and Xiaohongshu that turns topic, title, hook, script, resonance, and AI-expression checks into an executable workflow.
>
> Chinese content diagnosis · Short-video scripts · Xiaohongshu titles · Content review · Codex Skill

<p align="center">
  <a href="README.md">中文版 README</a>
</p>

---

## What problem does it solve?

Content editing often stops at “try another title” or “make the sentences smoother.” It still leaves the important questions unanswered: which format fits the material, why the audience should keep watching, whether the ideas actually connect, and which parts only look complete because they sound machine-written.

`dylan-content` breaks those decisions into six focused modules. It uses the user’s original wording, facts, and materials as evidence, then returns concrete edit locations, replacement lines, content structures, or next actions. It does not promise completion rate, click-through rate, distribution, or virality.

## Six content modules

| Module | Use it for |
| --- | --- |
| `01-content-diagnosis` | Topic, format, content direction, and full-draft diagnosis |
| `02-hook-optimization` | Short-video hooks, the first 5–10 seconds, and opening drop-off risks |
| `03-xhs-title-formulas` | Xiaohongshu title formula matching, generation, and rewriting |
| `04-script-flow` | Script continuity, information density, and spoken fluency |
| `05-resonance-diagnosis` | Audience resonance, emotional entry points, stance, and sharing mechanisms |
| `06-ai-expression-check` | AI-writing signals and post-generation spoken-expression QA |

For a complete short-video script, the default combination is `01`, `02`, `04`, `05`, and `06`. Add `03` when a Xiaohongshu version is needed.

## Installation

### Install into Codex

```bash
git clone https://github.com/xDylanLong/dylan-content.git
cd dylan-content
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R . "${CODEX_HOME:-$HOME/.codex}/skills/dylan-content"
```

Windows PowerShell:

```powershell
$skillRoot = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $HOME ".codex/skills" }
New-Item -ItemType Directory -Force -Path $skillRoot | Out-Null
Copy-Item -Recurse -Force . (Join-Path $skillRoot "dylan-content")
```

Then call it in Codex:

```text
Use $dylan-content to diagnose this Douyin short-video script and give me a directly usable revision.
```

### Local development binding

The local source directory for this project is `/Users/thawingx/Documents/dylan-content`. The current Codex runtime directory, `/Users/thawingx/.codex/skills/dylan-content`, is bound to that source directory. Changes made in the source directory are therefore visible to the runtime Skill immediately.

On another machine, create the same binding with a symbolic link:

```bash
ln -sfn /absolute/path/to/dylan-content "${CODEX_HOME:-$HOME/.codex}/skills/dylan-content"
```

## Common usage

### Diagnose a complete draft

```text
Use $dylan-content.
Diagnose the Douyin script below:
1. identify the core judgment and best format;
2. check the hook, continuity, resonance, and AI-writing signals;
3. give concrete edit locations and one next action.

<paste script>
```

### Optimize Xiaohongshu titles only

```text
Use $dylan-content.
Use only the Xiaohongshu title module. Generate 10 titles and recommend the best 3:

Topic: <paste topic>
Target audience: <paste audience>
```

### Check AI-writing signals only

```text
Use $dylan-content.
Check the copy below for AI-writing signals. Do not rewrite by default; quote the original line, severity, and reason.

<paste copy>
```

## Repository structure

```text
.
├── README.md
├── README.en.md
├── LICENSE
├── SKILL.md
├── agents/
│   └── openai.yaml
└── modules/
    ├── 01-content-diagnosis.md
    ├── 02-hook-optimization.md
    ├── 03-xhs-title-formulas.md
    ├── 04-script-flow.md
    ├── 05-resonance-diagnosis.md
    └── 06-ai-expression-check.md
```

## Boundaries

- Designed for Chinese topics, titles, short-video scripts, and copy for Douyin and Xiaohongshu.
- Uses the supplied material as evidence and does not invent experiences, metrics, achievements, or cases.
- Reports structural risks and testable improvements; it does not guarantee platform distribution results.
- Diagnoses the content before suggesting title or hook tactics; tactics cannot replace real material, a clear point of view, or product value.

## License

This project is released under the [MIT License](LICENSE).
