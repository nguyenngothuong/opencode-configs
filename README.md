# OpenCode Configs

My personal OpenCode configuration - commands and settings.

## Quick Start

1. Copy `opencode.json` to `~/.config/opencode/opencode.json`
2. Add your API keys to `opencode.json`
3. Copy commands from `command/` to your opencode commands folder

## Repository Structure

```
opencode-configs/
├── command/           # Slash commands
├── opencode.json     # Main config template
├── README.md         # English
└── README.vi.md     # Vietnamese
```

## Commands

| Command | Description |
|---------|-------------|
| `/check` | Report current plan progress |
| `/commit` | Smart commit with conventional messages |
| `/continue` | Resume an in-progress plan |
| `/exec` | Execute a plan (parallel/sequential) |
| `/next` | Run next pending task in plan |
| `/plan` | Create implementation plan |
| `/push` | Push to GitHub, optionally create PR |
| `/recap` | Summarize what agent did |
| `/report` | Full project status report |
| `/wrap` | Create walkthrough + learning summary |

## Config Template

`opencode.json` is a template - you must add your own API keys:

```json
{
  "provider": {
    "minimax": {
      "options": {
        "apiKey": "YOUR_MINIMAX_API_KEY"
      }
    },
    "bailian-coding-plan": {
      "options": {
        "apiKey": "YOUR_ALIYUN_API_KEY"
      }
    }
  }
}
```

## License

Personal config - feel free to adapt for your own use.
