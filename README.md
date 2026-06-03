# Eigi Claude Code Plugin

This repository is structured as a standalone Claude Code plugin named `eigi`.

It connects Claude Code to the hosted Eigi MCP server and adds Eigi conversation prompt rules as a Claude Code skill.

## Repository Structure

```text
eigi-plugins/
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json
├── README.md
└── skills/
    └── conversation-rules/
        └── SKILL.md
```

## Components

- MCP server: `https://mcp.eigi.ai/mcp`
- Skill: `/eigi:conversation-rules`

## Local Testing

From this repository root, validate the plugin:

```sh
claude plugin validate .
```

Load the plugin directly during development:

```sh
claude --plugin-dir .
```

After Claude Code starts, reload plugin components if needed:

```text
/reload-plugins
```

Then use the skill:

```text
/eigi:conversation-rules
```

Check the MCP connection from inside Claude Code:

```text
/mcp
```

## Public Distribution

This repo is now the plugin source, not a marketplace catalog.

For Anthropic's community marketplace submission:

1. Push this repository to GitHub.
2. Run `claude plugin validate .` locally.
3. Submit the plugin through the Claude plugin submission form.
4. Wait for automated validation and safety review.

## Notes

- The Eigi MCP server uses Claude Code's remote HTTP MCP transport.
- If the MCP server later requires authentication, add plugin `userConfig` to `.claude-plugin/plugin.json` and reference it from `.mcp.json` headers.
- Agents and hooks are intentionally not included in this first scaffold. They can be added later under `agents/` and `hooks/` at the plugin root.