# Claudian (AndySuen1 Fork)

**English | [中文](README.md)**

![GitHub stars](https://img.shields.io/github/stars/AndySuen1/claudian?style=social)
![GitHub release](https://img.shields.io/github/v/release/AndySuen1/claudian)
![License](https://img.shields.io/github/license/AndySuen1/claudian)

![Preview](Preview.png)

This repository is a fork of [YishenTu/claudian](https://github.com/YishenTu/claudian) with a few personal feature tweaks on top.

**For the full plugin overview, installation, configuration, usage, permissions, privacy, and troubleshooting docs, see the upstream repo:** [YishenTu/claudian](https://github.com/YishenTu/claudian)

This README only covers what this fork adds on top of upstream.

## What This Fork Adds

### Sandbox Mode
A new Sandbox toggle in the toolbar, on by default:
- **When enabled**: automatically switches to Haiku and closes external file access, giving the default session a lightweight, safe sandbox.
- **When disabled**: restores the previous model and reopens external access.
- The setting is stored per-tab (`tabAllowExternalAccess`), so tabs don't interfere with each other.

### Header Conversation Title
In single-tab mode, the active session title is shown next to the branding in the header so you can see the current conversation at a glance.

### Drag-to-Context
Drag any vault file onto the input area to set it as the current note context.

### FileContext Auto-Switch Fix
After a session has started, switching to a non-excluded note now updates the current note and resets its sent state, so the new note is re-sent on the next turn.

### Other Tweaks
- Default README language is Chinese (English version lives in [README_en.md](README_en.md)).

## Installation

Same as upstream — just swap the repo URL for this fork.

### GitHub Release
Download `main.js`, `manifest.json`, and `styles.css` from the [latest release](https://github.com/AndySuen1/claudian/releases/latest), drop them in `/path/to/vault/.obsidian/plugins/claudian/`, and enable the plugin under Community plugins.

### BRAT
Add the repo URL in BRAT: `https://github.com/AndySuen1/claudian`.

### From source
```bash
cd /path/to/vault/.obsidian/plugins
git clone https://github.com/AndySuen1/claudian.git
cd claudian
npm install
npm run build
```

See the [upstream README](https://github.com/YishenTu/claudian) for the full step-by-step.

## License

Licensed under the [MIT License](LICENSE).

## Acknowledgments

- Upstream [YishenTu/claudian](https://github.com/YishenTu/claudian) — every base feature in this fork comes from there.
- [Obsidian](https://obsidian.md), [Anthropic](https://anthropic.com), [OpenAI](https://openai.com).
