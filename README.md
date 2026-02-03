# VibeMon Docs

VibeMon is a real-time status monitoring system for AI coding assistants. It displays the current state (thinking, working, done) on ESP32 devices, Desktop App, or cloud service.

## Supported Platforms

- **Claude Code** - Anthropic's CLI for Claude
- **Kiro IDE** - Amazon's AI coding assistant
- **OpenClaw** - Open source AI gateway

## Installation

### Online Install (Recommended)

```bash
curl -fsSL https://docs.vibemon.io/install.py | python3
```

### Local Install

```bash
git clone https://github.com/nalbam/vibemon-docs.git
cd vibemon-docs
python3 docs/install.py
```

## Configuration

After installation, edit `~/.vibemon/.env.local` to configure your targets:

| Variable | Description | Example |
|----------|-------------|---------|
| `VIBEMON_HTTP_URLS` | HTTP targets (comma-separated) | `http://127.0.0.1:19280` |
| `VIBEMON_SERIAL_PORT` | ESP32 USB serial port (wildcard supported) | `/dev/cu.usbmodem*` |
| `VIBEMON_AUTO_LAUNCH` | Auto-launch Desktop App (`1` or `0`) | `0` |
| `VIBEMON_URL` | VibeMon cloud API URL | `https://vibemon.io` |
| `VIBEMON_TOKEN` | VibeMon API access token | (from dashboard) |
| `VIBEMON_CACHE_PATH` | Cache file path | `~/.vibemon/cache/statusline.json` |
| `DEBUG` | Enable debug logging (`1` or `0`) | `0` |

## CLI Commands

The hook script supports these commands:

```bash
# Lock monitor to current project
python3 ~/.claude/hooks/vibemon.py --lock [project_name]

# Unlock monitor
python3 ~/.claude/hooks/vibemon.py --unlock

# Get current status
python3 ~/.claude/hooks/vibemon.py --status

# Get/set lock mode (first-project, on-thinking)
python3 ~/.claude/hooks/vibemon.py --lock-mode [mode]

# Reboot ESP32 device
python3 ~/.claude/hooks/vibemon.py --reboot
```

## State Mapping

| Event | State |
|-------|-------|
| SessionStart | start |
| UserPromptSubmit | thinking |
| PreToolUse | working |
| PreCompact | packing |
| Notification | notification |
| Stop | done |

## GitHub Pages

This repository serves the `docs` folder via GitHub Pages at https://docs.vibemon.io

### Setup

1. Go to repository Settings
2. Select "Pages" from the left menu
3. Under "Source", select:
   - Branch: `main`
   - Folder: `/docs`
4. Click "Save"

### Custom Domain

The `docs/CNAME` file sets the domain to `docs.vibemon.io`.

DNS configuration:
- CNAME record: `docs.vibemon.io` -> `nalbam.github.io`

Or use GitHub's IP addresses (A records):
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
