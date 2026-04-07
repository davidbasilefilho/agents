# Shared Agents Config

Universal AI agent configuration shared across all developer environments.

## Overview

This repository provides a centralized, version-controlled configuration for AI coding agents using [`@intellectronica/ruler`](https://github.com/intellectronica/ruler). Configurations are distributed from [davidbasilefilho/agents](https://github.com/davidbasilefilho/agents) and can be overridden per-repository.

## Stack

- **Runtime**: [Bun](https://bun.sh)
- **Config Manager**: [`@intellectronica/ruler`](https://github.com/intellectronica/ruler)

## Setup

```bash
bun add -g @intellectronica/ruler
```

## Apply Configurations

Apply globally:

```bash
ruler apply
```

Apply per-repo:

```bash
ruler apply --local-only
```

## Per-Repo Override

Contributors can override global settings by adding files to their repo root:

```bash
# .claude.md      - Claude override
# .zed.md         - Zed override
# .gemini.md      - Gemini override
# .antigravity.md - Antigravity override
# .copilot.md     - Copilot override
```

The local file takes precedence over the global config.

## Update Config

Pull latest via git subtree:

```bash
git subtree pull --prefix=config https://github.com/davidbasilefilho/agents.git main --squash
```

## Configuration

```toml
default_agents = ["claude", "zed", "gemini", "antigravity", "copilot", "opencode"]

[mcp]
enabled = true
strategy = "merge"

[mcp_servers.context7]
command = "bun"
args = ["x", "--bun", "@upstash/context7-mcp"]

[mcp_servers.websearch]
url = "https://mcp.exa.ai/mcp"
```
