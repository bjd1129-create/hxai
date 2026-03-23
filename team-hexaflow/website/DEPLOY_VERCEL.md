# 🚀 大唐智能官网 - Vercel 部署指南

> 域名：hxai.vercel.app
> 更新时间：2026-03-23 20:38

---

## 📋 部署方式

### 方式 1：Vercel Dashboard（推荐）⭐⭐⭐⭐⭐

#### 步骤 1：创建 Vercel 账号

1. 访问：https://vercel.com
2. 点击 "Sign Up"
3. 使用 GitHub 账号登录（推荐）或邮箱注册

#### 步骤 2：导入项目

1. 点击 "Add New..." → "Project"
2. 选择 GitHub 仓库
3. 点击 "Import"

#### 步骤 3：配置项目

```
Framework Preset: Astro
Root Directory: team-hexaflow/website
Build Command: npm run build
Output Directory: dist
Install Command: npm install
```

#### 步骤 4：配置环境变量

```
PUBLIC_API_URL=https://hxai-api.vercel.app/api/v1
```

#### 步骤 5：部署

1. 点击 "Deploy"
2. 等待构建完成（约 2-3 分钟）
3. 访问分配的域名

#### 步骤 6：配置自定义域名

1. Settings → Domains
2. 添加域名：hxai.vercel.app
3. 验证域名所有权
4. 等待 DNS 生效（约 5-10 分钟）

---

### 方式 2：Vercel CLI

#### 安装 Vercel CLI

```bash
npm install -g vercel
```

#### 登录 Vercel

```bash
vercel login
```

#### 部署

```bash
cd team-hexaflow/website
vercel --prod
```

#### 配置域名

```bash
vercel domains add hxai.vercel.app
```

---

## 🌐 域名配置

### DNS 设置

如果使用自定义域名（如 hxai.ai）：

```
类型    名称    值
A       @       76.76.21.21
CNAME   www     cname.vercel.com
```

### SSL 证书

Vercel 自动提供 HTTPS 证书，无需手动配置。

---

## 📁 文件结构

```
website/
├── src/
│   ├── pages/
│   │   ├── index.astro        # 首页
│   │   ├── login.astro        # 登录
│   │   ├── register.astro     # 注册
│   │   ├── dashboard.astro    # 控制台
│   │   └── ...
│   └── components/
│       ├── Header.astro
│       ├── Footer.astro
│       └── ...
├── public/
│   └── favicon.svg
├── package.json
├── astro.config.mjs
├── tailwind.config.mjs
└── vercel.json               # Vercel 配置
```

---

## ⚙️ 构建配置

### package.json

```json
{
  "scripts": {
    "dev": "astro dev",
    "build": "astro build",
    "preview": "astro preview"
  }
}
```

### astro.config.mjs

```javascript
import { defineConfig } from 'astro/config';
import react from '@astrojs/react';

export default defineConfig({
  integrations: [react()],
  output: 'static',
  build: {
    format: 'directory'
  }
});
```

---

## 🔧 环境变量

### 开发环境

创建 `.env` 文件：

```
PUBLIC_API_URL=http://localhost:8000/api/v1
```

### 生产环境

在 Vercel Dashboard 配置：

```
PUBLIC_API_URL=https://hxai-api.vercel.app/api/v1
```

---

## 📊 部署检查清单

- [ ] Vercel 账号创建
- [ ] GitHub 仓库连接
- [ ] 项目导入
- [ ] 构建配置确认
- [ ] 环境变量配置
- [ ] 首次部署
- [ ] 域名配置
- [ ] HTTPS 验证
- [ ] 访问测试

---

## 🧪 测试

### 功能测试

- [ ] 首页加载正常
- [ ] 登录/注册功能
- [ ] 控制台页面
- [ ] 响应式设计（手机/平板）
- [ ] 所有链接有效

### 性能测试

- [ ] 首屏加载 < 3 秒
- [ ] Lighthouse 评分 > 90
- [ ] 图片优化
- [ ] CSS/JS 压缩

---

## 🚨 故障排查

### 构建失败

**原因：** 依赖安装失败

**解决：**
```bash
npm install
npm run build
# 本地测试构建
```

### 页面 404

**原因：** 路由配置错误

**解决：** 检查 `astro.config.mjs` 和文件路径

### API 请求失败

**原因：** CORS 或 API 地址错误

**解决：**
1. 检查 `PUBLIC_API_URL` 环境变量
2. 后端配置 CORS 允许 Vercel 域名

---

## 📈 监控与分析

### Vercel Analytics

启用 Vercel 自带分析：
1. Settings → Analytics
2. 点击 "Enable"

### 自定义分析

集成 Umami 或其他分析工具：

```astro
<!-- src/layouts/BaseLayout.astro -->
<script async src="https://analytics.umami.is/script.js" data-website-id="xxx"></script>
```

---

## 🔄 持续部署

### 自动部署

每次 push 到 main 分支自动触发部署：

```
GitHub Push → Vercel Webhook → 自动构建 → 自动部署
```

### 预览部署

Pull Request 自动创建预览链接：

```
PR 创建 → Vercel 预览 → 审核 → 合并 → 生产部署
```

---

## 💰 成本估算

### Vercel Hobby（免费）

- ✅ 无限部署
- ✅ 100GB 带宽/月
- ✅ 自动 HTTPS
- ✅ 自定义域名
- ❌ 无服务器功能（需升级）

### Vercel Pro（$20/月）

- ✅ 所有 Hobby 功能
- ✅ 1TB 带宽/月
- ✅ 无服务器功能
- ✅ 优先支持

**推荐：** 初期使用 Hobby 免费计划

---

## 📞 支持

**Vercel 文档：**
- https://vercel.com/docs

**Astro 文档：**
- https://docs.astro.build

**大唐智能内部：**
- 负责人：郭子仪（前端架构师）
- 协作：苏定方（DevOps）

---

**🐲 官网部署配置完成！请老庄开始部署！**
