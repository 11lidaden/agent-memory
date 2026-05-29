# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

Add whatever helps you do your job. This is your cheat sheet.

---

## Git 记忆仓库

- **仓库地址**：https://github.com/11lidaden/agent-memory.git
- **用户名**：11lidaden
- **Token**：存在 `.env.git` 中（已 gitignore）
- **用途**：存储所有记忆文件（MEMORY.md + memory/*.md）
- **本地路径**：/root/.openclaw/workspace
- **同步方式**：有新记忆时自动或手动推送到仓库

> 推送时从 .env.git 读取 token，拼接到 remote URL 中。

## 服务器

### 腾讯云
- **IP**：106.54.235.209
- **登录方式**：SSH 密码登录
- **部署项目**：/opt/ai-paper-distill/（ai-paper-distillation）
- **安全状态**：UFW 已启用（22/80/443），fail2ban 已启用
