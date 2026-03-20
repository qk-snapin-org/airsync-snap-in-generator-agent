# Snap-in Builder Plugin

Claude Code plugin for building DevRev AirSync snap-ins from a single prompt.

This is the **public** plugin — it contains slash commands, skills, and workflow instructions. The actual guide content and MCP server are in a separate private repository.

## Prerequisites

You need **two MCP servers** for the complete snap-in development workflow:

1. **Snap-in Builder MCP** — Provides guides, templates, validation, and code pattern tools
2. **DevRev AirSync MCP** (via `chef-cli`) — Provides metadata testing, field mapping, and validation tools

> See the [official DevRev AirSync MCP docs](https://developer.devrev.ai/airsync/mcp) for full details on the AirSync MCP server.

## Setup

### Claude Code

**1. Install the plugin**

```bash
/plugin install --github your-org/snapin-builder-plugin
```

**2. Add the Snap-in Builder MCP server**

Add to your `~/.claude/settings.json`:

```json
{
  "mcpServers": {
    "snapin-builder": {
      "type": "streamable-http",
      "url": "https://your-server.com/mcp"
    }
  }
}
```

**3. Add the DevRev AirSync MCP**

```bash
claude mcp add airsync chef-cli mcp initial-mapping
```

Then use: `/build-snapin Wrike`

### Cursor

Add both MCP servers to your project's `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "snapin-builder": {
      "type": "streamable-http",
      "url": "https://your-server.com/mcp"
    },
    "AirSync": {
      "command": "chef-cli",
      "args": ["mcp", "initial-mapping"]
    }
  }
}
```

> Note: Cursor users get the MCP tools but not the plugin commands/skills.

## Available Commands

| Command | What it does |
|---------|-------------|
| `/build-snapin <system>` | Scaffold + generate a complete AirSync snap-in |
| `/generate-metadata <system>` | Generate metadata and mapping JSON with validation |
| `/search-guide <topic>` | Quick reference lookup using targeted tools |

## MCP Tools (provided by the server)

| Tool | Purpose |
|------|---------|
| `scaffold_snapin` | Clone the official [airdrop-template](https://github.com/devrev/airdrop-template) |
| `build_snapin_guide` | Full builder guide — auth, extraction, patterns, file rules |
| `metadata_guide` | Full metadata guide — field types, references, stage diagrams |
| `get_decision_guide` | Look up a specific architectural decision |
| `get_code_template` | Get a specific code pattern |
| `get_devrev_object_schema` | Required fields for a DevRev object type |
| `validate_metadata` | Validate metadata JSON against all rules |
| `search_snapin_guide` | Full-text search across both guides |
| `suggest_guide_update` | Report a correction to improve the guides |

## Repository Structure

```
snapin-builder-plugin/   (this repo — public)
├── plugin.json          — Plugin manifest
├── commands/            — Slash command definitions
│   ├── build-snapin.md
│   ├── generate-metadata.md
│   └── search-guide.md
└── skills/
    └── snapin-builder/
        └── SKILL.md     — Detailed workflow instructions

snapin-builder-mcp/      (separate repo — private)
├── server/              — MCP server (TypeScript)
└── guide/               — Proprietary guide content
```
