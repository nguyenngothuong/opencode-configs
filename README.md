# OpenCode Config Files

Config files cho [OpenCode](https://opencode.ai) - AI coding agent mã nguồn mở, thay thế Claude Code.

## Cài đặt OpenCode

```bash
# Linux/Mac
curl -fsSL https://opencode.ai/install | bash

# Homebrew
brew install opencode-ai/tap/opencode

# Go install
go install github.com/opencode-ai/opencode@latest
```

## Vị trí file config

- **Linux/Mac:** `~/.config/opencode/opencode.json`
- **Windows:** `C:\Users\<USERNAME>\.config\opencode\opencode.json`

---

## Config Files

### 1. Antigravity (Claude & Gemini miễn phí qua Google)

File: [`config-antigravity.json`](./config-antigravity.json)

Sử dụng Claude Opus 4.5, Sonnet, Gemini 3 Pro/Flash **miễn phí** qua Google OAuth.

**Setup:**
```bash
# 1. Copy config vào file opencode.json
# 2. Đăng nhập Google
opencode auth login
# 3. Chọn "Antigravity oauth"
# 4. Kiểm tra auth
opencode auth list
# 5. Chạy OpenCode
opencode
```

### 2. GLM (Z.AI - Model Trung Quốc giá rẻ)

File: [`config-glm.json`](./config-glm.json)

GLM-4.7 thinking model, giá cực rẻ, chất lượng tốt (~8/10 so với Claude).

**Setup:**
1. Đăng ký tại [open.bigmodel.cn](https://open.bigmodel.cn)
2. Lấy API key
3. Thay `YOUR_API_KEY_HERE` trong config
4. Chạy `opencode`

### 3. Multi-provider (Kết hợp nhiều provider)

File: [`config-multi.json`](./config-multi.json)

Cấu hình đồng thời GLM + Antigravity + các provider khác.

---

## Tính năng hay của OpenCode

- **Multi-provider:** Không bị lock vào 1 provider
- **TUI đẹp:** Giao diện terminal đẹp hơn CLI thuần
- **Session management:** Lưu và quay lại các session chat
- **Commands:** Lưu lệnh tái sử dụng (`/breaking`, `/commit`, ...)
- **Skills:** Plugin system mở rộng
- **Plan vs Build mode:** Lên kế hoạch trước hoặc chạy trực tiếp

---

## Liên hệ

- **YouTube:** [Diginno](https://youtube.com/@diginno)
- **Video hướng dẫn:** [Link video]

---

*By Diginno Engineering Team*
