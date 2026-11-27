# Pi Starter Kit

Lean, cache-first configuration for [Pi Coding Agent](https://github.com/earendil-works/pi).

## Architecture

- **Append-Only Cache**: `codemode: "only"` + `pi-cache-optimizer` + `cacheWarming: "idle"` keeps prompt prefixes intact for maximum cache discounts.
- **Zero-Bloat Search & Media**: `pi-fff` (`override` mode) replaces built-in `grep`/`find`; `pi-native-web`, `pi-native-image`, and `pi-gemini-media` reuse your existing Pi OAuth logins (`google-ai-plan` & `openai-codex`) with zero third-party API keys.
- **Shared Rules & Skills**: `AGENTS.md` tracks [`xeronsh/agents-skills`](https://github.com/xeronsh/agents-skills) and skills live there too. `install.sh` fetches it at install time and falls back to the bundled copy.
- **Zero-MCP Browser Automation**: Replaces `chrome-devtools-mcp` with [`agent-browser`](https://github.com/vercel-labs/agent-browser) CLI + thin stub skill (`0` background MCP processes).

## Quick Start

```bash
# 1. Install Pi & agent-browser
npm install -g @earendil-works/pi-coding-agent agent-browser

# 2. Clone & Install
git clone https://github.com/xeronsh/pi-starter-kit.git ~/.pi-starter-kit
cd ~/.pi-starter-kit && ./install.sh
```

## Included Packages (5 Lean Core)

- `pi-cache-optimizer` - Prompt prefix stability & cache telemetry
- `@ff-labs/pi-fff` - SIMD fuzzy file & content search (`override` mode)
- `pi-native-web` - Native `web_search` & `fetch_url` via Gemini (`google-ai-plan`) & Codex (`openai-codex`) logins
- `pi-native-image` - Native `generate_image` via Codex (`openai-codex`) login
- `pi-gemini-media` - Native `read_media` (video frames+audio, audio, PDF) via Gemini
