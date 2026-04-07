# Installation

**Before proceeding, ask the user: "Do you want to install this config globally (shared across all your projects) or locally (only in this repository)?"**

---

## Global Installation

This installs the config to `~/.config/ruler` and applies it globally to your AI agents.

### Step 1: Download .ruler/ to ~/.config/ruler

<details>
<summary><strong>Linux / macOS</strong></summary>

```bash
mkdir -p ~/.config/ruler
curl -L https://github.com/davidbasilefilho/agents/archive/main.tar.gz | tar -xz -C ~/.config/ruler --strip-components=1 --include="*/.ruler/*"
```

</details>

<details>
<summary><strong>Windows (PowerShell)</strong></summary>

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.config\ruler" | Out-Null
$tempFile = "$env:TEMP\agents.tar.gz"
Invoke-WebRequest -Uri "https://github.com/davidbasilefilho/agents/archive/main.tar.gz" -OutFile $tempFile
tar -xzf $tempFile -C "$env:USERPROFILE\.config\ruler" --strip-components=2 --include="*/.ruler/*"
Remove-Item $tempFile -Force
```

</details>

### Step 2: Install Ruler Globally

```bash
bun add -g @intellectronica/ruler
```

### Step 3: Apply Config

```bash
ruler apply
```

---

## Local Installation (Per Repo)

This installs the config only in the current repository.

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

### Step 2: Detect Package Manager & Install Ruler

First, check which package manager is used in this repo:

- `bun.lock` or `bun.lockb` → **bun** 
- `yarn.lock` → **yarn**
- `pnpm-lock.yaml` → **pnpm**
- Otherwise → **npm** (check for `package.json`)

<details>
<summary><strong>Using bun</strong></summary>

```bash
bun add @intellectronica/ruler
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```bash
npm install @intellectronica/ruler
```

</details>

<details>
<summary><strong>Using yarn</strong></summary>

```bash
yarn add @intellectronica/ruler
```

</details>

<details>
<summary><strong>Using pnpm</strong></summary>

```bash
pnpm add @intellectronica/ruler
```

</details>

### Step 3: Apply Config

Run with the same package manager you used above:

<details>
<summary><strong>Using bun</strong></summary>

```bash
bun x ruler apply
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```bash
npx ruler apply
```

</details>

<details>
<summary><strong>Using yarn</strong></summary>

```bash
yarn ruler apply
```

</details>

<details>
<summary><strong>Using pnpm</strong></summary>

```bash
pnpm exec ruler apply
```

</details>

---

## Update Config

Forcefully download the latest .ruler/ from GitHub (overwrites existing files).

### Global Update

<details>
<summary><strong>Linux / macOS</strong></summary>

```bash
rm -rf ~/.config/ruler
curl -L https://github.com/davidbasilefilho/agents/archive/main.tar.gz | tar -xz -C ~/.config/ruler --strip-components=1 --include="*/.ruler/*"
```

</details>

<details>
<summary><strong>Windows (PowerShell)</strong></summary>

```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.config\ruler"
$tempFile = "$env:TEMP\agents.tar.gz"
Invoke-WebRequest -Uri "https://github.com/davidbasilefilho/agents/archive/main.tar.gz" -OutFile $tempFile
tar -xzf $tempFile -C "$env:USERPROFILE\.config\ruler" --strip-components=2 --include="*/.ruler/*"
Remove-Item $tempFile -Force
```

</details>

### Local Update (Per Repo)

<details>
<summary><strong>Linux / macOS</strong></summary>

```bash
rm -rf .ruler
curl -L https://github.com/davidbasilefilho/agents/archive/main.tar.gz | tar -xz -C . --strip-components=1 --include="*/.ruler/*"
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
```

</details>

After updating, reapply the config:

```bash
# Global
ruler apply

# Local (use the same package manager as original install)
bun x ruler apply   # or: npx ruler apply / yarn ruler apply / pnpm exec ruler apply
```