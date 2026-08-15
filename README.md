# Dylan 内容诊断与调整

> 一个面向中文内容的诊断与调整 Skill，把选题、标题、开头、逐字稿、共鸣和 AI 味检查，整理成可以直接执行的修改建议。
>
> 中文内容诊断 · 文稿调整 · 短视频口播 · 小红书标题 · 内容复盘 · Codex Skill

<p align="center">
  <a href="README.en.md">English README</a>
</p>

<p align="center">
  <a href="https://www.xiaohongshu.com/user/profile/5df3742d000000000100212"><img src="readme-assets/xiaohongshu.svg" alt="小红书" width="40" height="40"></a>&nbsp;&nbsp;
  <a href="https://www.douyin.com/user/MS4wLjABAAAAHH81Iv6MWugNS03rPOnWulSnhRbM26Ud_S16rlgqOfY4nR8bznDSWbFIcviihJJm"><img src="readme-assets/douyin.svg" alt="抖音" width="40" height="40"></a>&nbsp;&nbsp;
  <a href="https://x.com/xDylanLong"><img src="readme-assets/x.svg" alt="X / Twitter" width="40" height="40"></a>
</p>
<p align="center">
  <a href="https://looda.cc">个人主页</a>
</p>

---

## 它解决什么问题

内容加工经常停留在“换一个标题”或“把句子写顺”，却没有回答更重要的问题：这条内容适合什么形式、观众为什么会继续看、观点之间是否真的连得起来，以及哪些表达只是看起来很完整。

`dylan-content-review` 把这些判断拆成六个可按需调用的模块。它以用户提供的原句、事实和素材为证据，输出具体的删改位置、替代句、内容骨架或下一步动作，不承诺完播率、点击率或“必火”，也不默认从零生成完整成稿。

## 六个内容模块

| 模块 | 适用任务 |
| --- | --- |
| `01-content-diagnosis` | 选题、内容形式、内容方向和完整文稿诊断 |
| `02-hook-optimization` | 短视频开头、前 5 秒、前 10 秒和开场流失风险 |
| `03-xhs-title-formulas` | 小红书标题公式匹配、生成和改写 |
| `04-script-flow` | 逐字稿的逻辑延续、信息密度和口播流畅度 |
| `05-resonance-diagnosis` | 受众共鸣、情绪入口、立场和传播机制 |
| `06-ai-expression-check` | AI 写作特征检查，以及生成口播后的表达质检 |

用户提供完整短视频稿时，默认组合 `01`、`02`、`04`、`05`、`06`；需要小红书版本时再加入 `03`。

## 怎么安装

### 安装到 Codex

```bash
git clone https://github.com/xDylanLong/dylan-content-review.git
cd dylan-content-review
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R . "${CODEX_HOME:-$HOME/.codex}/skills/dylan-content-review"
```

Windows PowerShell：

```powershell
$skillRoot = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $HOME ".codex/skills" }
New-Item -ItemType Directory -Force -Path $skillRoot | Out-Null
Copy-Item -Recurse -Force . (Join-Path $skillRoot "dylan-content-review")
```

安装后，在 Codex 中调用：

```text
Use $dylan-content-review 诊断这篇抖音口播稿，并给出可以直接修改的版本。
```

### 本地开发绑定

本项目的本地源目录是 `/Users/thawingx/Documents/dylan-content-review`。当前 Codex 运行时目录 `/Users/thawingx/.codex/skills/dylan-content-review` 与它分别维护，因此修改后需要同步更新运行时目录。

其他机器可以用符号链接建立同样的绑定：

```bash
ln -sfn /absolute/path/to/dylan-content-review "${CODEX_HOME:-$HOME/.codex}/skills/dylan-content-review"
```

## 常用用法

### 诊断完整内容

```text
Use $dylan-content-review。
请诊断下面这篇抖音口播稿：
1. 先判断核心观点和内容形式；
2. 检查开头、逻辑延续、共鸣入口和 AI 味；
3. 给出具体删改位置和下一步动作。

<粘贴口播稿>
```

### 只优化小红书标题

```text
Use $dylan-content-review。
只使用小红书标题模块，为这个选题生成 10 个标题，并推荐最适合的 3 个：

选题：<粘贴选题>
目标人群：<粘贴目标人群>
```

### 只检查 AI 味

```text
Use $dylan-content-review。
只检查下面这段文案的 AI 写作特征，默认不要改写；请标出原句、风险等级和原因。

<粘贴文案>
```

## 仓库结构

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

## 使用边界

- 适合抖音、小红书的中文选题、标题、口播稿和文案诊断。
- 诊断以用户提供的素材为依据，不凭空补充经历、数据、成绩或案例。
- 输出结构风险和可验证改法，不保证平台分发结果。
- 默认先诊断内容本身，再讨论标题和开头；技巧不能替代真实素材、观点和产品价值。

## License

本项目采用 [MIT License](LICENSE)。
