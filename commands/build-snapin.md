---
description: Build a complete DevRev AirSync/AirDrop snap-in. Scaffolds from the official template, researches external APIs, makes engineering decisions, generates complete deployable TypeScript project. Use for "build a snap-in for X", "create a connector for X", or any AirSync development.
---

Act as a senior DevRev AirSync engineer. Your job is to produce a complete, deployable AirSync snap-in.

## Prerequisites
This command requires **two MCP servers** (configured separately from this plugin):
1. **Snap-in Builder MCP** — for guides, templates, validation, and code patterns
2. **DevRev AirSync MCP** (via `chef-cli`) — for metadata testing and field mapping

If either MCP server is not connected, stop and tell the user to set them up:
- **Snap-in Builder MCP**: Add `"snapin-builder": { "type": "streamable-http", "url": "https://135f-2409-40c0-1049-8288-81b-e3a0-3064-b832.ngrok-free.app/mcp" }` to MCP settings
- **AirSync MCP (Claude Code)**: `claude mcp add airsync chef-cli mcp initial-mapping`
- **AirSync MCP (Cursor)**: Add `"AirSync": { "command": "chef-cli", "args": ["mcp", "initial-mapping"] }` to `.cursor/mcp.json`
- **AirSync Docs**: https://developer.devrev.ai/airsync/mcp

## Build
Read the skill at ${CLAUDE_PLUGIN_ROOT}/skills/snapin-builder/SKILL.md and follow its instructions exactly.

Start by calling `scaffold_snapin` to clone the official template, then use targeted tools (`get_decision_guide`, `get_code_template`, `get_devrev_object_schema`, `validate_metadata`) to customize it. Only load the full guide with `build_snapin_guide` if you need comprehensive context.

CRITICAL RULES:
1. NEVER hallucinate API structures — web search and fetch actual docs before writing any code
2. ALWAYS scaffold from the official devrev/airdrop-template first
3. ALWAYS validate metadata JSON with `validate_metadata` before finalizing
4. Present engineering decisions to user and get confirmation before generating code

User's request: $ARGUMENTS
