# Installing Superpowers for GitHub Copilot CLI

Enable superpowers skills, agents, and hooks in GitHub Copilot CLI.

## Prerequisites

- Git
- [GitHub Copilot CLI](https://docs.github.com/en/copilot/github-copilot-in-the-cli) (GA)

## Installation

### Method 1 — Plugin Install (recommended)

```bash
copilot plugin install obra/superpowers
```

This automatically discovers skills, agents, and hooks from the plugin manifest.

### Method 2 — Manual (clone + symlink)

1. **Clone the superpowers repository:**
   ```bash
   git clone https://github.com/obra/superpowers.git ~/.copilot/superpowers
   ```

2. **Create the skills symlink:**
   ```bash
   mkdir -p ~/.copilot/skills
   ln -s ~/.copilot/superpowers/skills ~/.copilot/skills/superpowers
   ```

   **Windows (PowerShell):**
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.copilot\skills"
   cmd /c mklink /J "$env:USERPROFILE\.copilot\skills\superpowers" "$env:USERPROFILE\.copilot\superpowers\skills"
   ```

3. **Create the agents symlink:**
   ```bash
   mkdir -p ~/.copilot/agents
   ln -s ~/.copilot/superpowers/.copilot-cli/agents/code-reviewer.agent.md ~/.copilot/agents/code-reviewer.agent.md
   ```

   **Windows (PowerShell):**
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.copilot\agents"
   cmd /c mklink "$env:USERPROFILE\.copilot\agents\code-reviewer.agent.md" "$env:USERPROFILE\.copilot\superpowers\.copilot-cli\agents\code-reviewer.agent.md"
   ```

4. **Restart Copilot CLI** to discover skills, agents, and hooks.

## Verify

```bash
ls -la ~/.copilot/skills/superpowers
ls -la ~/.copilot/agents/code-reviewer.agent.md
```

You should see symlinks pointing to your superpowers directories.

## Updating

**Plugin install:**
```bash
copilot plugin update superpowers
```

**Manual:**
```bash
cd ~/.copilot/superpowers && git pull
```

Skills and agents update instantly through the symlinks.

## Uninstalling

**Plugin install:**
```bash
copilot plugin uninstall superpowers
```

**Manual:**
```bash
rm ~/.copilot/skills/superpowers
rm ~/.copilot/agents/code-reviewer.agent.md
```

Optionally delete the clone: `rm -rf ~/.copilot/superpowers`.
