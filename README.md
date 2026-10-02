# Faceless plugin for Claude

Create, render and publish AI faceless videos with [Faceless.so](https://faceless.so): TTS voiceover, AI visuals, captions and music, rendered in the cloud and published to YouTube, TikTok, Instagram, X and more.

## Install

In Claude Code:

```
/plugin marketplace add Side-Products/faceless-claude-plugin
/plugin install faceless@faceless
```

## Authenticate

The first time a Faceless tool runs, Claude opens a Faceless sign-in. Sign in, pick the team to connect and approve the permissions. There is no key to configure, and you can revoke access any time from your team settings at https://faceless.so/team.

## What you get

- The `faceless` skill: workflows for creating videos, running automated series, scheduling posts and checking analytics.
- The `faceless` MCP server (remote, https://faceless.so/api/v1/mcp): every public API operation as a tool, over OAuth 2.1 with dynamic client registration.

## Privacy

The plugin talks only to faceless.so. See https://faceless.so/privacy for what Faceless stores and how long.

Docs: https://faceless.so/developers. This repo is generated from the Faceless API registry; do not edit by hand.
