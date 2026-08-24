# Veracode Skills

GitHub Copilot skills for Veracode security scanning workflows. Each skill is a pre-built prompt that knows which [Veracode MCP](https://github.com/dipsylala/veracode-mcp) tools to call for a specific task.

## Prerequisites

- The [Veracode MCP server](https://github.com/dipsylala/veracode-mcp) must be installed and configured in VS Code
- An authenticated Veracode account with API credentials configured
- GitHub Copilot with agent mode enabled in VS Code

## Available Skills

| Skill | Trigger | What it does |
| --- | --- | --- |
| **scanit** | `/scanit` | Packages the workspace and starts a pipeline SAST scan |
| **thirdit** | `/thirdit` | Runs a local SCA scan on third-party dependencies and checks IaC configurations |
| **reportit** | `/reportit` | Retrieves findings and produces a prioritised executive summary |

## Installation

### Install for a project (team-shared, checked in to source control)

Copy the skill directories into your project's `.claude/skills/` directory:

*Windows:*

```powershell
Copy-Item -Recurse scanit, thirdit, reportit, fixit, explainit "<your-project>\.claude\skills\"
```

*macOS/Linux:*

```bash
cp -r scanit thirdit reportit fixit explainit <your-project>/.claude/skills/
```

### Install for personal use across all projects

*Windows:*

```powershell
Copy-Item -Recurse scanit, thirdit, reportit, fixit, explainit "$env:USERPROFILE\.claude\skills\"
```

*macOS/Linux:*

```bash
cp -r scanit thirdit reportit fixit explainit ~/.claude/skills/
```

After placing the directories, the skills are available immediately — no VS Code reload required.

## Typical Workflow

```text
# 1. Package and scan
/scanit

# 2. Review findings
/reportit

# 3. Scan dependencies and IaC separately
/thirdit
```

> **Note:** Skills call MCP tools automatically based on your request. The Veracode MCP server must be running and configured in VS Code for skills to work.

## See Also

- [veracode-agents](https://github.com/dipsylala/veracode-agents) — VS Code Copilot agents for autonomous analysis and remediation loops
- [veracode-mcp](https://github.com/dipsylala/veracode-mcp) — The MCP server these skills connect to
