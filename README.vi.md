# OpenCode Configs

Cấu hình OpenCode cá nhân của tôi - commands và settings.

## Bắt Đầu Nhanh

1. Copy `opencode.json` vào `~/.config/opencode/opencode.json`
2. Thêm API keys của bạn vào `opencode.json`
3. Copy commands từ `command/` vào folder commands của opencode

## Cấu Trúc

```
opencode-configs/
├── command/           # Slash commands
├── opencode.json     # Main config template
├── README.md         # Tiếng Anh
└── README.vi.md      # Tiếng Việt
```

## Commands

| Command | Mô tả |
|---------|--------|
| `/check` | Báo cáo tiến độ plan hiện tại |
| `/commit` | Commit thông minh với conventional messages |
| `/continue` | Tiếp tục plan đang dở |
| `/exec` | Thực thi plan (parallel/sequential) |
| `/next` | Chạy task pending tiếp theo trong plan |
| `/plan` | Tạo implementation plan |
| `/push` | Push lên GitHub, tạo PR nếu cần |
| `/recap` | Tóm tắt những gì agent đã làm |
| `/report` | Báo cáo trạng thái project đầy đủ |
| `/wrap` | Tạo walkthrough + learning summary |

## Config Template

`opencode.json` là template - bạn phải thêm API keys của mình:

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

Config cá nhân - thoải mái adapt cho use case của bạn.
