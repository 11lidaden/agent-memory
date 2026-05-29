# MEMORY.md - 长期记忆

> 这是 AI 助手的长期记忆，记录所有重要的工作、决策、项目和经验教训。
> 上次更新：2026-05-29

---

## 用户信息

- **称呼**：待确认
- **时区**：GMT+8（中国标准时间）
- **技术栈**：Python, Flask, React, Nginx, Linux 服务器运维
- **云服务**：腾讯云（服务器 106.54.235.209）
- **GitHub**：https://github.com/11lidaden
- **兴趣**：AI/LLM 应用、论文研究

---

## 项目记录

### 1. ai-paper-distillation（arXiv 论文蒸馏工具）

- **仓库**：https://github.com/11lidaden/ai-paper-distillation
- **功能**：arXiv 论文抓取 → LLM 三层蒸馏 → 收藏/历史/笔记管理
- **技术栈**：
  - 后端：Flask + SQLite + Gunicorn（2 worker, 4 thread）
  - 前端：React + Vite + TailwindCSS（深色主题）
  - 蒸馏模型：mimo-v2-flash（小米 MiMo API）
- **部署**：腾讯云 106.54.235.209，项目路径 /opt/ai-paper-distill/
- **数据库**：51 篇论文（截至 2026-05-27），34 篇已蒸馏
- **2026-05-29 安全加固**：
  1. FLASK_ENV → production
  2. Nginx 恶意路径拦截（/shell, /.env, /wp-login 等返回 444）
  3. UFW 开启（仅放行 22/80/443）+ fail2ban 启用（3 个 jail）
- **待修复**：
  - distill.py 缺少重试机制
  - 前端 401 无自动跳转登录
  - CORS 指向旧 IP（同源所以不影响，但应清理）
- **文档**：DEPLOY_GUIDE.md, AGENTS.md, SERVER_ENV.md（已推送到 GitHub main）

---

## 工具与环境

### 服务器（腾讯云 106.54.235.209）
- SSH 密码登录（已知凭据）
- UFW：已启用（22/80/443）
- fail2ban：已启用（3 个 jail）

---

## 经验与教训

### 2026-05-29
- **记忆很重要**：上一个 claw 实例被意外关闭，丢失了所有上下文。之后建立了专门的记忆仓库（agent-memory）来持久化存储。
- **安全加固顺序**：先修应用配置（FLASK_ENV），再加固 Web 层（Nginx），最后开系统防火墙（UFW + fail2ban）
- **文档先行**：修完东西要及时更新文档并推送到 Git

---

## 待办事项

- [ ] 确认用户称呼和偏好
- [ ] 修复 ai-paper-distillation 的 distill.py 重试机制
- [ ] 修复前端 401 自动跳转登录
- [ ] 配置 SSH 密钥登录替代密码登录
