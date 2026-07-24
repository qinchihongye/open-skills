# open-skills

通用 **Agent Skills** 合集（开源 monorepo）。

每个 skill 独立目录，内含 `SKILL.md`（及可选 `references/`），可安装到 Grok、Claude 等支持 skills 的客户端。

## Skills

| 名称 | 说明 |
|------|------|
| [markdown-format](./skills/markdown-format/) | 个人笔记向 Markdown：新建按规则写；修改已有文件只改格式不改内容 |

## 安装

### Grok（用户级）

```bash
git clone https://github.com/qinchihongye/open-skills.git
cd open-skills
mkdir -p ~/.grok/skills
ln -sfn "$(pwd)/skills/markdown-format" ~/.grok/skills/markdown-format
```

重载或新开 Grok 会话后，可使用 `/markdown-format`，或在写/整理笔记 md 时由 description 自动匹配。

### Claude Code（可选）

```bash
mkdir -p ~/.claude/skills
ln -sfn "$(pwd)/skills/markdown-format" ~/.claude/skills/markdown-format
```

### 项目级（仅当前仓库）

```bash
mkdir -p /path/to/your-project/.grok/skills
ln -sfn /path/to/open-skills/skills/markdown-format /path/to/your-project/.grok/skills/markdown-format
```

## 使用（markdown-format）

- **新建 / 生成笔记 md**：按标题后 `*`、最多三级标题、少标题、`*` 作分类等规则写
- **修改已有 md**：只改格式，不改内容
- **不要默认用于**：`create-skill`、任意 skills 目录内文件（除非你强制指定本 skill 且点名某一个 md 路径）

详情见 [skills/markdown-format/SKILL.md](./skills/markdown-format/SKILL.md)。

## 仓库结构

```text
open-skills/
├── README.md
├── LICENSE
├── .gitignore
└── skills/
    └── markdown-format/
        ├── SKILL.md
        └── references/
```

新增 skill：在 `skills/<name>/` 下放置 `SKILL.md`，并更新本 README 表格。

## License

[MIT](./LICENSE)
