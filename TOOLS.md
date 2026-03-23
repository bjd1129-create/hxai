# TOOLS.md - Local Notes

## API Keys（机密）⚠️ 敏感信息

### Cloudflare
- **API Token:** `c4700685aef3e0b161ef2263d28bd69283c94` ✅ 完整
- **平台:** https://dash.cloudflare.com
- **用途:** Pages 部署、Workers、DNS 管理
- **状态:** ✅ 已配置
- **权限:** Pages:Edit, Workers:Write, Zone:Read
- **记录时间:** 2026-03-23 11:58

### GitHub
- **组织:** https://github.com/bjd1129-create
- **仓库:** https://github.com/bjd1129-create/hxai
- **用途:** 大唐智能官网自动化部署
- **状态:** ✅ 已配置
- **记录时间:** 2026-03-23 22:30

### MiniMax
- **Key:** `sk-cp-dfOHnWCqr1Iv_l-Tykxkt7Ok4NCAAdQsx2jCEA2TQEQElC9y7Fj1FwTx_a5EfiHlu0I0CzYGtz8SN5gDrKdBzQgexNbinTS3XGWHzI1AB9qxZ58zRLdThC0`
- **平台:** https://platform.minimaxi.com
- **套餐:** 月度套餐 119 元/月（可调用全系模型）
- **模型:** 
  - **主模型:** MiniMax-M2.5 ✅（最新）
  - 文本生成：MiniMax-M1 / MiniMax-Text-01
  - 语音合成：MiniMax-Voice-01
  - 图像理解：MiniMax-Vision-01
- **状态:** ✅ 已配置

### 百炼大模型（阿里云）
- **Key:** `sk-sp-b879148afe854c45b2850757aa4997fd`
- **平台:** https://bailian.console.aliyun.com
- **Base URL (OpenAI 兼容):** https://coding.dashscope.aliyuncs.com/v1
- **Base URL (Anthropic 兼容):** https://coding.dashscope.aliyuncs.com/apps/anthropic
- **主用模型:** qwen3.5-plus ✅
- **可用模型:**
  - **千问系列:** qwen3.5-plus, qwen3-max-2026-01-23, qwen3-coder-next, qwen3-coder-plus
  - **智谱系列:** glm-5, glm-4.7
  - **Kimi 系列:** kimi-k2.5
  - **MiniMax 系列:** minimax-m2.5
- **状态:** ✅ 已配置（备选模型源）

---

## 新技能

### CrewAI 百炼集成
- 文件：SKILL_CREWAI_BAILIAN.md
- 用途：CrewAI 连接阿里云百炼 API
- 状态：已掌握

### MiniMax 模型集成
- 文件：SKILL_MINIMAX.md
- 用途：调用 MiniMax API 进行文本生成
- 状态：✅ 已部署

---

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
