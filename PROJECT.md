# Shared Agents Config

Universal AI agent configuration shared across all developer environments.

## Overview

This repository provides a centralized, version-controlled configuration for AI coding agents using [`@intellectronica/ruler`](https://github.com/intellectronica/ruler). Configurations are distributed from [davidbasilefilho/agents](https://github.com/davidbasilefilho/agents) and can be overridden per-repository.

## Stack

- **Runtime**: [Bun](https://bun.sh)
- **Package Manager**: [uv](https://github.com/astral-sh/uv) for Python
- **Config Manager**: [`@intellectronica/ruler`](https://github.com/intellectronica/ruler)

## Setup

```bash
bun install
```

## Apply Configurations

Apply globally:

```bash
bun run ruler apply
```

Apply per-repo:

```bash
bun run ruler apply --local-only
```

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
