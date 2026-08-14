# open-skills

通用 **Agent Skills** 合集（开源 monorepo）。

每个 skill 独立目录，内含 `SKILL.md`（及可选 `assets/`、`references/`、`agents/`），可安装到 Grok、Claude、Codex 等支持 skills 的客户端。

## Skills

| 名称 | 说明 |
|------|------|
| [markdown-format](./skills/markdown-format/) | 通用 Markdown 排版：新建按规则写；修改已有文件只改格式不改内容 |
| [http-api-doc-writer](./skills/http-api-doc-writer/) | 按通用模板生成与实现/契约一致的详细 HTTP 接口文档 |

## 安装

以 monorepo 为真源，软链到用户级 skills 目录（改一处三端同步）。

### Grok（用户级）

```bash
git clone https://github.com/qinchihongye/open-skills.git
cd open-skills
mkdir -p ~/.grok/skills
ln -sfn "$(pwd)/skills/markdown-format" ~/.grok/skills/markdown-format
ln -sfn "$(pwd)/skills/http-api-doc-writer" ~/.grok/skills/http-api-doc-writer
```

重载或新开 Grok 会话后可用 `/markdown-format`、`/http-api-doc-writer`，或由 description 自动匹配。

### Claude Code（可选）

```bash
mkdir -p ~/.claude/skills
ln -sfn "$(pwd)/skills/markdown-format" ~/.claude/skills/markdown-format
ln -sfn "$(pwd)/skills/http-api-doc-writer" ~/.claude/skills/http-api-doc-writer
```

### Codex（可选）

```bash
mkdir -p ~/.codex/skills
ln -sfn "$(pwd)/skills/markdown-format" ~/.codex/skills/markdown-format
ln -sfn "$(pwd)/skills/http-api-doc-writer" ~/.codex/skills/http-api-doc-writer
```

### 项目级（仅当前仓库）

```bash
mkdir -p /path/to/your-project/.grok/skills
ln -sfn /path/to/open-skills/skills/markdown-format \
  /path/to/your-project/.grok/skills/markdown-format
ln -sfn /path/to/open-skills/skills/http-api-doc-writer \
  /path/to/your-project/.grok/skills/http-api-doc-writer
```

## 使用

### markdown-format

- **新建 / 生成 md**：按标题后 `*`、最多三级标题、少标题、`*` 作分类等规则写
- **修改已有 md**：只改格式，不改内容
- **不要默认用于**：`create-skill`、任意 skills 目录内文件（除非强制指定本 skill 且点名某一个 md 路径）

详情见 [skills/markdown-format/SKILL.md](./skills/markdown-format/SKILL.md)。

### http-api-doc-writer

- **输入**：指定项目 + 可核对的接口实现，或用户明确指定的契约/OpenAPI
- **输出**：业务路径下的详细接口文档（按模板骨架，删除不适用章节）
- **不要**：交空模板冒充实档；编造字段/错误码/URL；写入 skill 包或 skills 安装目录；明文 secret
- **排版**：纯格式修复交给 `markdown-format`

详情见 [skills/http-api-doc-writer/SKILL.md](./skills/http-api-doc-writer/SKILL.md)。

## 仓库结构

```text
open-skills/
├── README.md
├── LICENSE
├── .gitignore
└── skills/
    ├── markdown-format/
    │   ├── SKILL.md
    │   ├── agents/
    │   │   └── openai.yaml
    │   └── references/
    └── http-api-doc-writer/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        ├── assets/
        │   └── http-api-doc-template.md
        └── references/
            └── template-guide.md
```

新增 skill：在 `skills/<name>/` 下放置 `SKILL.md`，并更新本 README 表格。

## License

[MIT](./LICENSE)
