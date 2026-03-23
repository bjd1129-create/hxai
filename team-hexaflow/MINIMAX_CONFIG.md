# 🤖 MiniMax 全系模型配置

> **套餐:** 月度套餐 119 元/月  
> **平台:** https://platform.minimaxi.com  
> **更新时间:** 2026-03-23 23:00

---

## 📋 可用模型列表

### 文本生成模型

| 模型 | 说明 | 适用场景 | 状态 |
|------|------|----------|------|
| **MiniMax-M2.5** | 最新最强模型 | 主用模型，所有核心任务 | ✅ 主用 |
| MiniMax-M1 | 上一代主力模型 | 备用，简单任务 | ✅ 可用 |
| MiniMax-Text-01 | 文本生成专用 | 长文本创作 | ✅ 可用 |

### 语音合成模型

| 模型 | 说明 | 适用场景 | 状态 |
|------|------|----------|------|
| MiniMax-Voice-01 | 语音合成 | TTS、语音播报 | ✅ 可用 |

### 视觉理解模型

| 模型 | 说明 | 适用场景 | 状态 |
|------|------|----------|------|
| MiniMax-Vision-01 | 图像理解 | 图像分析、OCR | ✅ 可用 |

---

## 🔧 配置方式

### 环境变量

```bash
# 主模型
MINIMAX_MODEL=MiniMax-M2.5

# 全系模型列表
MINIMAX_MODELS=MiniMax-M2.5,MiniMax-M1,MiniMax-Text-01,MiniMax-Voice-01,MiniMax-Vision-01

# API 配置
MINIMAX_API_KEY=sk-cp-dfOHnWCqr1Iv_l-Tykxkt7Ok4NCAAdQsx2jCEA2TQEQElC9y7Fj1FwTx_a5EfiHlu0I0CzYGtz8SN5gDrKdBzQgexNbinTS3XGWHzI1AB9qxZ58zRLdThC0
MINIMAX_BASE_URL=https://api.minimaxi.com/v1
```

### CrewAI 配置

```python
from crewai import Agent

# 使用 M2.5（主模型）
agent = Agent(
    role="研究员",
    goal="AI 研究",
    llm="minimax-m2.5"  # 或 "minimax-m1"
)

# 使用专用模型
voice_agent = Agent(
    role="语音助手",
    llm="minimax-voice-01"
)

vision_agent = Agent(
    role="视觉分析",
    llm="minimax-vision-01"
)
```

### TangAgents 配置

```python
from tangagents import Agent

# 支持多模型切换
agent = Agent(
    role="AI 研究员",
    goal="完成 AI 调研",
    model="minimax-m2.5"  # 可切换：m1, text-01, voice-01, vision-01
)
```

---

## 📊 模型使用策略

### 按任务类型分配

| 任务类型 | 推荐模型 | 说明 |
|----------|----------|------|
| **核心决策** | MiniMax-M2.5 | CEO/CTO 决策、方案审核 |
| **技术研究** | MiniMax-M2.5 | 论文分析、技术调研 |
| **代码开发** | MiniMax-M2.5 | 后端/前端/全栈开发 |
| **文档编写** | MiniMax-M1 | 技术文档、博客文章 |
| **日常对话** | MiniMax-M1 | 飞书消息、简单问答 |
| **语音播报** | MiniMax-Voice-01 | TTS、故事讲述 |
| **图像分析** | MiniMax-Vision-01 | 截图分析、OCR |

### 按优先级分配

| 优先级 | 模型 | 说明 |
|--------|------|------|
| **P0 核心任务** | MiniMax-M2.5 | 老庄明确指示、战略决策 |
| **P1 重要任务** | MiniMax-M2.5 | 功能开发、方案设计 |
| **P2 常规任务** | MiniMax-M1 | 文档、调研、测试 |
| **P3 辅助任务** | MiniMax-Text-01 | 长文本生成、格式化 |

---

## 💰 套餐说明

**月度套餐：119 元/月**

**包含额度：**
- 文本生成：1000 万 tokens/月
- 语音合成：50 小时/月
- 图像理解：1000 次/月

**适用场景：**
- ✅ 10 人团队日常使用
- ✅ AI 研究任务
- ✅ 内容创作
- ✅ 客户服务

**超额计费：**
- 文本：0.008 元/千 tokens
- 语音：2 元/小时
- 图像：0.5 元/次

---

## 🎯 优化建议

### 1. 模型降级策略
```python
# M2.5 故障时自动降级
def get_model():
    try:
        return call_minimax("MiniMax-M2.5")
    except Exception:
        return call_minimax("MiniMax-M1")  # 降级到 M1
```

### 2. 任务分流
```python
# 简单任务用 M1，复杂任务用 M2.5
if task.complexity > 0.7:
    model = "MiniMax-M2.5"
else:
    model = "MiniMax-M1"
```

### 3. 批量处理优化
```python
# 批量任务使用 Text-01（更便宜）
for doc in batch_docs:
    result = call_minimax("MiniMax-Text-01", doc)
```

---

## 📈 使用监控

### 每日检查
- Token 使用量
- API 调用次数
- 错误率

### 每周总结
- 各模型使用比例
- 成本分析
- 性能对比

### 每月复盘
- 套餐额度使用率
- 是否需要升级套餐
- 模型效果评估

---

## 🔗 相关链接

- **MiniMax 平台:** https://platform.minimaxi.com
- **API 文档:** https://platform.minimaxi.com/api
- **模型对比:** https://platform.minimaxi.com/models
- **定价详情:** https://platform.minimaxi.com/pricing

---

**🐲 大唐智能 · 技术配置**
*贞观之治，始于足下*
