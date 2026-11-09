---
name: photo2skin
description: Photo2Skin's AI tools for Minecraft — make and edit Minecraft skins just by chatting (from a photo or a description, then changes in words), grab any Java player's skin, search a skin library, make Minecraft builds (castles, houses, ships…) from a description or a photo, make Minecraft-style pixel art from a photo, and turn real places into playable Minecraft worlds. Use when the user wants a Minecraft skin (for playing, or a character for a video or a client), a player's skin, a Minecraft build or structure, a Minecraft map of a real place, or Minecraft-style pixel art.
---

# Photo2Skin

Photo2Skin is a set of AI tools for Minecraft. Its main one makes real, playable 64x64 Minecraft
skins just by chatting: from a photo or a description, then any change in words ("add a red cape"),
to a skin the user made here, a real skin they already have (the one they wear in Minecraft, or a
skin PNG), or a library skin. It also grabs any Java player's skin, turns photos into
Minecraft-style pixel art, makes Minecraft builds from a description or a photo, builds real places
as Minecraft worlds (Java and Bedrock), and has a free skin library and a library of builds. For players and for creators who make Minecraft characters for videos or design
skins for others. Turning a Roblox avatar into a Minecraft skin is on the website, not a tool:
https://app.photo2skin.com/roblox-to-minecraft-skin. AI texture packs are on the website too, not
a tool: made at https://app.photo2skin.com/texture-packs, and players' public packs are free to
download from https://app.photo2skin.com/textures. Not an official Minecraft product.

## Connect (once)

Add the remote MCP server — the user signs in to Photo2Skin and presses Allow:

```bash
claude mcp add --transport http photo2skin https://mcp.photo2skin.com/mcp
```

Other apps: https://app.photo2skin.com/agents

## Tools

| Tool | Cost | Use |
|---|---|---|
| `search_skins`, `get_skin`, `grab_player_skin` | free | Find skins in the library; read any Java player's current skin |
| `get_account` | free | Credit balance and every price — check before a paid tool |
| `create_skin` | credits | From a `description`, a photo (`photo`, `photo_url` or `upload_id`), or both. Or change a skin in words: one of the user's (`job_id`) or a library skin to remix (`library_skin_id`), optionally with a picture to copy from |
| `choose_skin_take` | free | When `get_job` shows several takes of a skin, keep the one the user picks |
| `pixelate_photo` | credits | Photo to Minecraft-style pixel art |
| `create_map` | credits, by area | Latitude/longitude + `size_km2` (0.25 street … 25 city), `edition` |
| `create_build` | credits, by size and quality | A structure from a `description`, a photo, or both; `size` (32, 64, 256 blocks per side), `quality` (standard, high, max). Change one of the user's builds: `job_id` + the change in `description` |
| `search_builds` | free | Search the public library of AI builds by words, one category (castles, houses, structures, statues, free) or a sort order; each has a page to view and download it (downloading needs a free account; a few builds cost credits to download, paid once on that page; its `build.download_credits` says how many) |
| `get_job` | free | Poll a `skin_…`, `map_…`, `pixel_…` or `build_…` job; done = image + download link, or for a build the page where the user walks around it and downloads it |
| `get_photo_upload_link` | free | When you can't pass the photo yourself: the user uploads it at a link |
| `save_skin`, `publish_skin` | free | Save a PNG to the account; publish to the library only when asked |

Gift cards (a code worth AI credits, as a present) are not a tool: they are bought and redeemed by the person at https://app.photo2skin.com/gift-cards. Send them the link.

## Rules

- Tell the user the price (from `get_account`) before any paid tool.
- Paid tools return a job id within seconds. Poll `get_job` every ~10 s; skins take 30–90 s,
  builds and maps minutes. Pass the same `idempotency_key` when retrying, so nothing is charged twice.
- `INSUFFICIENT_CREDITS`: send the user to https://app.photo2skin.com/pricing. Never try to buy.
- Never publish a skin to the library unless the user asked.
- A finished build is not a file you hand over: share the page `get_job` gives, where the user
  turns it in 3D, walks inside and downloads it for Java or Bedrock (signed in).
- To edit a skin the user already has: `save_skin` (`player` for the skin they wear in Java, or
  `skin_url`), then `create_skin` with that `job_id` and the change in `description`.
- When `get_job` shows several takes of a skin, show them and let the user pick; keep it with
  `choose_skin_take`. Until then, take 1 is the skin.

## Without MCP (read-only, no account)

`GET https://app.photo2skin.com/api/library/skins?q=knight` — schema at
`https://app.photo2skin.com/api/openapi.json`.
