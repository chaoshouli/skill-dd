# skill-dd

**5分钟看懂一个 Skill 有没有货。**

`skill-dd` is a Codex Skill for reverse engineering and due-diligencing AI capabilities before you decide whether to learn, copy, adapt, buy, integrate, or ignore them.

It works on:

- GitHub repos
- Codex Skills
- Claude Skills
- MCP servers
- Agents
- Prompts
- Templates
- Workflows
- Knowledge bases

## What It Does

The skill answers six practical questions:

```text
这是什么
核心能力是什么
真正值钱的是什么
是否值得学习
是否值得接入
是否值得改造
```

It is intentionally not a simple scoring tool. The first job is decomposition:

```text
看穿包装 -> 找到本质 -> 找到资产 -> 判断复用价值
```

## Output Framework

The default report covers:

1. Skill / artifact type identification
2. Surface demand, real demand, and core contradiction
3. Required, enhanced, and decorative capabilities
4. Reusable assets such as prompts, rules, workflows, examples, datasets, and evaluation systems
5. Scarcity level from L1 to L5
6. Fit for AI marketing, Skill libraries, and production workflows
7. Final investment decision and weighted score

## GitHub Repo Reviews

For GitHub-hosted Skills and small repositories, `skill-dd` now uses a low-latency fetch path by default:

1. Read repo metadata through GitHub API.
2. Read the contents tree through GitHub API.
3. Inspect only high-signal files first: `README.md`, `SKILL.md`, `references/`, `scripts/`, `examples/`, `agents/`, and config files.
4. Decode API file contents from base64 when needed.
5. Use `git clone` only when local execution, full history, or binary asset inspection is necessary.

This avoids blocking first-pass judgment on slow or unstable `git clone` / `raw.githubusercontent.com` paths.

## Install

Clone or download this repository, then copy it into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills/skill-dd
cp -R . ~/.codex/skills/skill-dd/
```

Restart Codex if the skill does not appear immediately.

## Usage

```text
用 $skill-dd 评估这个 Skill：
https://github.com/example/repo
```

```text
用 skill-dd 拆一下这个 Prompt 有没有沉淀价值
```

```text
用 $skill-dd 看这个 MCP 是否值得接入我的 AI 工作流
```

## Files

```text
SKILL.md
agents/openai.yaml
references/github-fetch-policy.md
references/report-template.md
```

## License

MIT
