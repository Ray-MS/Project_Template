# 研究项目模板

复制本模板后，按下表存放代码、论文稿件和参考文献，并查阅各目录的 README。

| 目录 | 用途 |
| --- | --- |
| [`code/`](code/README.md) | 存放数据处理、分析和绘图代码 |
| [`manuscript/`](manuscript/README.md) | 存放 LaTeX 源文件、参考文献数据库（如 `.bib`）和论文插图 |
| [`references/`](references/README.md) | 存放参考文献 PDF |

## 从 GitHub 模板新建项目

配置 GitHub SSH 访问后，在 PowerShell 中运行以下命令，将 `$projectPath` 改为尚未创建的新项目目录。

```powershell
$templateUrl = 'git@github.com:Ray-MS/Project_Template.git'
$projectPath = 'F:\project\my-study'
if (Test-Path -LiteralPath $projectPath) { throw '新项目目录已存在。' }

git init -b main $projectPath
if ($LASTEXITCODE -ne 0) { throw '初始化新仓库失败。' }
Set-Location -LiteralPath $projectPath

git fetch --depth=1 $templateUrl HEAD
if ($LASTEXITCODE -ne 0) { throw '拉取模板失败。' }
git restore --source=FETCH_HEAD --worktree -- .
if ($LASTEXITCODE -ne 0) { throw '写入模板文件失败。' }
```

命令会取出模板默认分支最新提交中的文件。新项目从自己的首次提交开始，可以在新目录中运行 Codex 的 `/init`，生成项目自己的 `AGENTS.md`。

## 推荐技能

- 参考 AI 智能体如何迭代修改训练代码、运行实验并依据评估指标保留改动。[autoresearch](https://github.com/karpathy/autoresearch)
- 识别并改写文本中常见的 AI 写作痕迹。[humanizer](https://github.com/blader/humanizer)
- 用于文献检索、论文润色和科研绘图的技能集合。[nature-skills](https://github.com/Yuan1z0825/nature-skills)
- 使用 LaTeX TikZ 图标和可编辑模板绘制论文中的架构图与流程图。[OpenTikZ](https://github.com/opentikz/opentikz)
