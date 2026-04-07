# Agents Config

Centralized AI agent configuration using [`@intellectronica/ruler`](https://github.com/intellectronica/ruler).

## Requirements

- [Bun](https://bun.sh)

## For Humans

### Setup

```bash
bun install
```

### Apply Configurations

```bash
bun run ruler apply
```

For agent-specific instructions, see [INSTALL.md](INSTALL.md).

## For Agents

Read the raw installation guide:

```
https://raw.githubusercontent.com/davidbasilefilho/agents/main/INSTALL.md
```

## Project Structure

```
├── .ruler/
│   ├── AGENTS.md      # Agent instructions
│   ├── ruler.toml     # Ruler configuration
│   └── skills/        # 21 skills
├── .opencode/         # Applied opencode config
├── package.json
└── INSTALL.md
```

## Skills

21 specialized skills available in `.ruler/skills/`:

adapt, animate, arrange, audit, bolder, clarify, colorize, critique, delight, distill, extract, frontend-design, harden, normalize, onboard, optimize, overdrive, polish, quieter, teach-impeccable, typeset
