# Installation

Install this shared AI agent configuration per repository.

## Requirements

- [Bun](https://bun.sh)

## Setup

### Step 1: Download .ruler/ to Repo Root

<details>
<summary><strong>Linux / macOS</strong></summary>

```bash
mkdir -p .ruler
curl -L https://github.com/davidbasilefilho/agents/archive/main.tar.gz | tar -xz -C . --strip-components=1 --include="*/.ruler/*"
```

</details>

<details>
<summary><strong>Windows (PowerShell)</strong></summary>

```powershell
New-Item -ItemType Directory -Force -Path ".ruler" | Out-Null
$tempFile = "$env:TEMP\agents.tar.gz"
Invoke-WebRequest -Uri "https://github.com/davidbasilefilho/agents/archive/main.tar.gz" -OutFile $tempFile
tar -xzf $tempFile -C . --strip-components=1 --include="*/.ruler/*"
Remove-Item $tempFile -Force
```

</details>

### Step 2: Install Dependencies

```bash
bun install
```

### Step 3: Apply Config

```bash
bun x ruler apply
```

## Update

Forcefully download the latest .ruler/ from GitHub and reapply:

<details>
<summary><strong>Linux / macOS</strong></summary>

```bash
rm -rf .ruler
curl -L https://github.com/davidbasilefilho/agents/archive/main.tar.gz | tar -xz -C . --strip-components=1 --include="*/.ruler/*"
bun x ruler apply
```

</details>

<details>
<summary><strong>Windows (PowerShell)</strong></summary>

```powershell
Remove-Item -Recurse -Force ".ruler"
$tempFile = "$env:TEMP\agents.tar.gz"
Invoke-WebRequest -Uri "https://github.com/davidbasilefilho/agents/archive/main.tar.gz" -OutFile $tempFile
tar -xzf $tempFile -C . --strip-components=1 --include="*/.ruler/*"
Remove-Item $tempFile -Force
bun x ruler apply
```

</details>
