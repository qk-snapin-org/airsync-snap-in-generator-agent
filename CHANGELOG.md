# Changelog

All notable changes to the snapin-builder plugin.

## [2.2.0] - 2026-03-20

### Changed
- SKILL.md anti-patterns: added "NEVER force offset-based APIs into nextPageToken with string conversion".

## [2.1.0] - 2026-03-20

### Added
- `/update-snapin` command — update or improve existing AirSync snap-ins without rebuilding from scratch. Supports adding entities, switching auth, fixing pagination, adding bidirectional loading, attachments, nested children, and more.

### Changed
- `/build-snapin` command now explicitly instructs to check for multi-datacenter/regional URLs (e.g., `.com`, `.eu`, `.in`) during research and use `[REGION]` placeholders in manifest.
- `/build-snapin` command now enforces calling `get_code_template("data-extraction")` before generating data-extraction.ts.
- SKILL.md research checklist now includes multi-datacenter URL detection.
- SKILL.md sync unit decision now explains Pattern B (org as sync unit) when no container object exists.
- SKILL.md now includes "MANDATORY Structure" section for data-extraction.ts with required patterns and anti-patterns.
- Plugin description updated to reflect build + update capabilities.

## [2.0.0] - 2026-03-15

### Added
- `/build-snapin` command — scaffold + generate complete AirSync snap-in from a single prompt.
- `/generate-metadata` command — generate external_domain_metadata.json and initial_domain_mapping.json.
- `/search-guide` command — quick reference lookup for AirSync patterns.
- `snapin-builder` skill — full 6-step workflow: scaffold → research → decisions → metadata → code → validate.
- MCP tool orchestration: 9 tools (scaffold, guides, search, templates, schemas, validation).
- Marketplace support via `.claude-plugin/marketplace.json`.

## [1.0.0] - 2026-03-01

### Added
- Initial plugin with basic snap-in building workflow.
- Single command for AirSync snap-in generation.
- Direct guide embedding (pre-MCP architecture).
