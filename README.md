# Pi Starter Kit

Lean, cache-first configuration for [Pi Coding Agent](https://github.com/earendil-works/pi).

## Architecture

- **Append-Only Cache**: `codemode: "only"` + `pi-cache-optimizer` + `cacheWarming: "idle"` keeps prompt prefixes intact for 95% cache discounts.
- **Zero-Bloat Search**: `pi-fff` in `override` mode replaces built-in `grep`/`find`; `pi-web-access` runs raw (`workflow: "none"`) so search results stay out of the cached prompt prefix.
- **Shared Rules & Skills**: `AGENTS.md` tracks [`0xNorex/agents-skills`](https://github.com/0xNorex/agents-skills) and skills live there too, so both starter kits share one source of truth. `install.sh` fetches it at install time and falls back to the bundled copy.
- **Zero-MCP Browser Automation**: Replaces `chrome-devtools-mcp` with the [`agent-browser`](https://github.com/vercel-labs/agent-browser) CLI + thin stub skill (`0` background MCP processes, compact `@eN` accessibility snapshots).

## Quick Start

```bash
# 1. Install Pi & agent-browser
npm install -g @earendil-works/pi-coding-agent agent-browser

# 2. Clone & Install
git clone https://github.com/0xNorex/pi-starter-kit.git ~/.pi-starter-kit
cd ~/.pi-starter-kit && ./install.sh
```

## Included Packages (3 Core Only)

- `pi-cache-optimizer` - Prompt prefix stability & cache telemetry
- `pi-web-access` - Web search, URL/GitHub/PDF fetching
- `@ff-labs/pi-fff` - SIMD fuzzy file & content search (`override` mode)
