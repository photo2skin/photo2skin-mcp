<p align="center"><img src="logo.png" width="96" alt="Photo2Skin logo"></p>

# Photo2Skin — AI tools for Minecraft, for AI agents

**AI tools for Minecraft: skins from a photo or prompt, AI builds, real-world maps, textures and more.**
Connect Photo2Skin to Claude, ChatGPT, Cursor, VS Code, Gemini CLI or any MCP client and make
Minecraft things just by chatting.

This repo holds the public connection files: the remote MCP server's address, a Claude Code
plugin, a Cursor plugin, a Gemini CLI extension and an agent skill. The server itself is hosted
by Photo2Skin; there is nothing to run locally.

| | |
|---|---|
| **MCP server** | `https://mcp.photo2skin.com/mcp` (Streamable HTTP) |
| **Sign-in** | OAuth with a free Photo2Skin account — no API key |
| **Official MCP Registry** | `com.photo2skin/photo2skin` |
| **Install guide** | https://app.photo2skin.com/agents |

## What it does

1. **AI skins** — make a real, playable 64x64 Minecraft skin from a photo, a description, or both,
   then keep asking for changes ("add a red cap"). Bring in a skin you already have (any Java
   player's current skin, or a skin PNG) and edit it with words.
2. **AI builds** — castles, houses, ships, statues… from a description or a photo. Walk around
   them in 3D and download for Java or Bedrock.
3. **Real-world maps** — turn any place on Earth into a playable Minecraft world (Java and Bedrock).
4. **Textures** — AI texture packs for Java and Bedrock, on the website at
   [app.photo2skin.com/texture-packs](https://app.photo2skin.com/texture-packs).
5. **And more** — a skin grabber for any Java player, a free skin library and builds library, and
   Minecraft-style pixel art from a photo.

## Install

**Claude Code**

```bash
claude mcp add --transport http photo2skin https://mcp.photo2skin.com/mcp
```

or as a plugin, with the skill included:

```
/plugin marketplace add photo2skin/photo2skin-mcp
/plugin install photo2skin@photo2skin
```

**Claude, ChatGPT** — add a custom connector with the URL `https://mcp.photo2skin.com/mcp`
(step-by-step: https://app.photo2skin.com/agents).

**Cursor, VS Code, Windsurf and other MCP clients**

```json
{
  "mcpServers": {
    "photo2skin": { "url": "https://mcp.photo2skin.com/mcp" }
  }
}
```

**Gemini CLI**

```bash
gemini extensions install https://github.com/photo2skin/photo2skin-mcp
```

The first time a tool runs, your app opens Photo2Skin's sign-in page; sign in and press Allow.

## Tools

| Tool | Cost | What it does |
|---|---|---|
| `create_skin` | credits | A skin from a description, a photo, or both — or a change to one, in words |
| `save_skin`, `choose_skin_take`, `publish_skin` | free | Bring in a skin, pick a take, publish to the library (only when asked) |
| `create_build` | credits | A Minecraft structure from a description, a photo, or both |
| `create_map` | credits | A real place as a playable Minecraft world |
| `pixelate_photo` | credits | Photo to Minecraft-style pixel art |
| `search_skins`, `get_skin`, `grab_player_skin`, `search_builds` | free | Skin library, any Java player's skin, builds library |
| `get_account`, `get_job`, `get_photo_upload_link` | free | Credits and prices, job status, photo upload link |

Browsing, grabbing and the libraries are free. AI creations spend Photo2Skin credits; the agent
tells you the price first and never buys anything. Prices: https://app.photo2skin.com/pricing

## Files

| File | For |
|---|---|
| [`server.json`](server.json) | The official MCP Registry entry |
| [`.mcp.json`](.mcp.json), [`.claude-plugin/`](.claude-plugin) | Claude Code plugin and marketplace |
| [`mcp.json`](mcp.json), [`.cursor-plugin/`](.cursor-plugin) | Cursor plugin |
| [`gemini-extension.json`](gemini-extension.json), [`GEMINI.md`](GEMINI.md) | Gemini CLI extension |
| [`skills/photo2skin/SKILL.md`](skills/photo2skin/SKILL.md) | Agent skill: when and how to use the tools |

## Support and legal

- Support: admin@photo2skin.com
- Privacy policy: https://photo2skin.com/privacy.html
- Terms: https://photo2skin.com/terms.html
- Security: https://app.photo2skin.com/.well-known/security.txt

The files in this repo are MIT-licensed. The Photo2Skin service they connect to is governed by its
terms. Not an official Minecraft product; not affiliated with Mojang or Microsoft.
