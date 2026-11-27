# Pi Starter Kit

Lean, cache-first configuration for [Pi Coding Agent](https://github.com/earendil-works/pi).

## Architecture

- **Append-Only Cache & Neon Keep-Warm**: `codemode: "only"` + `cacheWarming: "idle"` + `google-ai-plan` `gemini-4-neon` 45s cache warming override keeps prompt prefixes hot.
- **Zero-Bloat Search & Native Capabilities**: `pi-fff` (`override` mode) replaces built-in `grep`/`find`; [`pi-native-kit`](https://github.com/xeronsh/pi-native-kit) bundles 5 independent KISS extensions reusing your Pi OAuth logins (`google-ai-plan` & `openai-codex`) with zero third-party API keys.
- **Shared Rules & Skills**: `AGENTS.md` tracks [`xeronsh/agents-skills`](https://github.com/xeronsh/agents-skills) and skills live there too. `install.sh` fetches it at install time and falls back to the bundled copy.
- **Zero-MCP Browser Automation**: Replaces `chrome-devtools-mcp` with [`agent-browser`](https://github.com/vercel-labs/agent-browser) CLI + skill (`0` background MCP processes).

## Quick Start

```bash
# 1. Install Pi & agent-browser
npm install -g @earendil-works/pi-coding-agent agent-browser

# 2. Clone & Install
git clone https://github.com/xeronsh/pi-starter-kit.git ~/.pi-starter-kit
cd ~/.pi-starter-kit && ./install.sh
```

## Included Packages (2 Core Only)

- `@ff-labs/pi-fff` - SIMD fuzzy file & content search (`override` mode)
- [`pi-native-kit`](https://github.com/xeronsh/pi-native-kit) - 5 independent KISS native extensions:
  - `gemini-media` (`read_media`): video (frames + audio), audio, PDF
  - `native-web` (`web_search`, `fetch_url`): Codex-first & Gemini web search + Gemini URL context
  - `native-image` (`generate_image`): Codex image generation & editing (private `0600` output + `codemode` `outputSchema`)
  - `native-usage` (`/usage`, `check_usage`, footer): live Codex 5h/7d + Antigravity 5h/7d quota + session cache hit rate
  - `native-compact`: routes auto & `/compact` summarization to `gemini-4-hydrogen (high)` with 500K context cap
