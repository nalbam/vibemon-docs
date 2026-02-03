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

After installation, edit `~/.vibemon/config.json` to configure your targets:

```json
{
  "debug": false,
  "cache_path": "~/.vibemon/cache/statusline.json",
  "auto_launch": false,
  "http_urls": ["http://127.0.0.1:19280"],
  "serial_port": "/dev/cu.usbmodem*",
  "vibemon_url": "https://vibemon.io",
  "vibemon_token": "your-token-here"
}
```

| Field | Description |
|-------|-------------|
| `debug` | Enable debug logging |
| `cache_path` | Cache file path for project metadata |
| `auto_launch` | Auto-launch Desktop App on session start |
| `http_urls` | HTTP targets (Desktop App, ESP32 WiFi) |
| `serial_port` | ESP32 USB serial port (wildcard supported) |
| `vibemon_url` | VibeMon cloud API URL |
| `vibemon_token` | VibeMon API access token (from dashboard) |

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
