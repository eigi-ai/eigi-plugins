# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog, and this project follows a simple
unreleased-first changelog flow.

## Unreleased

## [main] - 2026-06-04

### Added

- Added Codex plugin manifest at `.codex-plugin/plugin.json`, reusing the existing `skills/` directory and `.mcp.json` configuration. (PR [#1](https://github.com/eigi-ai/eigi-plugins/pull/1))

## [main] - 2026-06-03

### Added

- Added standalone Eigi Claude Code plugin scaffold using the standard root layout.
- Added plugin manifest at `.claude-plugin/plugin.json`.
- Added marketplace manifest at `.claude-plugin/marketplace.json` so the same repository can be added directly as a marketplace.
- Added hosted Eigi MCP configuration at `https://mcp.eigi.ai/mcp`.
- Added `conversation-rules` skill for Eigi prompt-writing guidance.

### Changed

- Updated plugin description to cover voice agents, calling workflows, and conversation experiences.
