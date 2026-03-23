# 🚀 大唐智能官网 - 部署指南

> 域名：datang-ai.pages.dev
> 更新时间：2026-03-23 18:48

---

## 📋 部署方式

### 方式 1：Cloudflare Dashboard（推荐）

1. 访问：https://dash.cloudflare.com
2. Workers & Pages → Create application → Pages
3. Connect to Git → 选择仓库
4. 配置：
   ```
   Project name: datang-ai
   Production branch: main
   Build command: echo 'Static site'
   Output directory: team-hexaflow/website
   ```
5. 点击 "Save and Deploy"

### 方式 2：Wrangler CLI

```bash
cd team-hexaflow/website
wrangler pages deploy . --project-name=datang-ai
```

---

## 🌐 访问地址

部署成功后：
- **官网：** https://datang-ai.pages.dev
- **团队状态：** /team-status（如需要）

---

## 📁 网站结构

```
website/
├── index.html          # 主页（已完成）
├── wrangler.toml       # Cloudflare 配置
└── DEPLOY.md          # 本文件
```

---

## ✅ 部署检查清单

- [x] 官网页面完成
- [x] Wrangler 配置完成
- [ ] Cloudflare 部署
- [ ] 域名验证
- [ ] HTTPS 证书

---

**🐲 请老庄选择部署方式！**
