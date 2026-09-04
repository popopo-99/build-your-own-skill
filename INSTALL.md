# 安装 Build Your Own Skill

如果你只是想尽快开始，优先使用 Codex 自带的 `$skill-installer`。

## A. 推荐方式：Skill Installer

在 Codex 中调用：

```text
$skill-installer

Install the skill from:
https://github.com/popopo-99/build-your-own-skill
```

`$skill-installer` 是 Codex 的 Skill，后面的内容是给它的自然语言安装请求，不是 shell 命令。

安装后，在 Codex CLI 或 IDE 中输入 `$`，或使用 `/skills`，确认出现 `build-your-own-skill`。Codex 通常会自动检测新安装或变更的 Skill；如果没有出现，再尝试重启 Codex。

## B. 不会 Git：Download ZIP

1. 在 GitHub 仓库页面点击 **Code → Download ZIP**。
2. 解压下载的文件。
3. 将整个仓库目录复制到个人 Skill 目录。
4. 建议将最终目录名整理为 `build-your-own-skill`。

Codex 的个人级（USER）Skill 目录是 `$HOME/.agents/skills`。这个 Skill 的最终入口应位于：

Windows：

```text
%USERPROFILE%\.agents\skills\build-your-own-skill\SKILL.md
```

例如：

```text
C:\Users\<username>\.agents\skills\build-your-own-skill\SKILL.md
```

macOS / Linux：

```text
~/.agents/skills/build-your-own-skill/SKILL.md
```

`SKILL.md` 必须直接位于 `build-your-own-skill/` 这一层。下载 ZIP 后要特别检查是否出现双层目录。

错误示例：

```text
build-your-own-skill/
└── build-your-own-skill-main/
    └── SKILL.md
```

正确示例：

```text
build-your-own-skill/
├── SKILL.md
├── references/
├── templates/
├── case-studies/
└── ...
```

不要只复制 `SKILL.md`。Build Your Own Skill 会使用 references、templates、tests 等支持内容，应复制完整目录。

## C. Git 用户

如果 `$HOME/.agents/skills` 尚不存在，请先创建该目录，再克隆仓库。

macOS / Linux：

```bash
git clone https://github.com/popopo-99/build-your-own-skill.git \
  ~/.agents/skills/build-your-own-skill
```

Windows PowerShell：

```powershell
git clone https://github.com/popopo-99/build-your-own-skill.git `
  "$HOME\.agents\skills\build-your-own-skill"
```

## D. Repository-scoped 安装

如果只希望这个 Skill 在某一个 repository 中生效，可以将完整目录放入：

```text
$REPO_ROOT/.agents/skills/build-your-own-skill/
```

Build Your Own Skill 通常适合跨多个项目使用，因此个人安装（USER Skill）仍是本指南的默认推荐方式。

## E. 如何确认安装成功

在 Codex CLI 或 IDE 中：

- 输入 `$` 选择 Skill；
- 或使用 `/skills`；
- 找到 `build-your-own-skill`。

然后测试：

```text
$build-your-own-skill

我想把自己的一套工作方法做成 Skill。
先帮我做 Discovery，不要创建任何文件。
```

预期行为：它应该先帮助你发现问题、经验和 Workflow，而不是立即创建 `SKILL.md`。

## F. 常见问题

### 看不到 Skill

检查 `SKILL.md` 是否位于正确目录层级、是否复制了完整 Skill。若仍未出现，尝试重新打开或重启 Codex。

### 下载 ZIP 后没有识别

检查是否出现 `build-your-own-skill/build-your-own-skill-main/SKILL.md` 这样的双层目录。将内层仓库内容移动到正确的 `build-your-own-skill/` 层级。

### 我只复制 SKILL.md 可以吗？

不推荐。Build Your Own Skill 会使用 references、templates 等支持文件；只复制入口文件会缺少完整内容。

### 安装后会自动修改我的项目吗？

不会因为“安装”本身修改项目。Discovery、Design 和 Review 默认不等于文件写入授权；只有用户明确要求 Build、创建或修改文件，并且目标范围清晰时，才应该进入写入阶段。

### GitHub 更新后，本地会自动更新吗？

手动安装的本地副本不会因为 GitHub 仓库更新而自动同步。使用 Git 安装的用户可以更新本地 clone；其他安装方式需要重新同步或重新安装最新版。

## G. 其他环境

这个仓库当前首先提供 Codex 本地 Skill 的安装说明。其他支持 Agent Skills 的环境，请根据对应产品对 Skill directory 或 package 的支持方式使用；这里不假设它们支持从 GitHub 直接安装。

安装位置、调用方式和重新加载行为以 [官方 Codex Skills 文档](https://developers.openai.com/codex/skills) 为准。
