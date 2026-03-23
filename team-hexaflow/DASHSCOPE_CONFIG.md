# 🤖 百炼大模型配置

> **平台:** 阿里云百炼  
> **更新时间:** 2026-03-23 23:02  
> **状态:** ✅ 已配置（备选模型源）

---

## 📋 配置信息

### API 配置

| 配置项 | 值 |
|--------|-----|
| **套餐专属 Base URL** | https://coding.dashscope.aliyuncs.com/v1 |
| **Anthropic 兼容 URL** | https://coding.dashscope.aliyuncs.com/apps/anthropic |
| **API Key** | `sk-sp-b879148afe854c45b2850757aa4997fd` |
| **主用模型** | qwen3.5-plus |

---

## 📦 可用模型列表（8 个）

### 千问系列（通义千问）

| 模型 | 能力 | 适用场景 |
|------|------|----------|
| **qwen3.5-plus** | 文本生成、深度思考、视觉理解 | 主用模型，复杂任务 |
| qwen3-max-2026-01-23 | 文本生成、深度思考 | 超大上下文任务 |
| qwen3-coder-next | 文本生成 | 代码生成专用 |
| qwen3-coder-plus | 文本生成 | 代码生成增强版 |

### 智谱系列

| 模型 | 能力 | 适用场景 |
|------|------|----------|
| glm-5 | 文本生成、深度思考 | 复杂推理任务 |
| glm-4.7 | 文本生成、深度思考 | 常规任务 |

### Kimi 系列（月之暗面）

| 模型 | 能力 | 适用场景 |
|------|------|----------|
| kimi-k2.5 | 文本生成、深度思考、视觉理解 | 长上下文任务 |

### MiniMax 系列

| 模型 | 能力 | 适用场景 |
|------|------|----------|
| minimax-m2.5 | 文本生成、深度思考 | 备用 MiniMax 源 |

---

## 🔧 使用方式

### 环境变量

```bash
# 百炼配置
DASHSCOPE_BASE_URL=https://coding.dashscope.aliyuncs.com/v1
DASHSCOPE_API_KEY=sk-sp-b879148afe854c45b2850757aa4997fd
DASHSCOPE_MODEL=qwen3.5-plus

# 可用模型
DASHSCOPE_MODELS=qwen3.5-plus,qwen3-max-2026-01-23,qwen3-coder-next,qwen3-coder-plus,glm-5,glm-4.7,kimi-k2.5,minimax-m2.5
```

### OpenAI 兼容调用

```python
from openai import OpenAI

client = OpenAI(
    api_key="sk-sp-b879148afe854c45b2850757aa4997fd",
    base_url="https://coding.dashscope.aliyuncs.com/v1"
)

response = client.chat.completions.create(
    model="qwen3.5-plus",
    messages=[
        {"role": "system", "content": "你是一个 AI 助手"},
        {"role": "user", "content": "你好"}
    ]
)
```

### Anthropic 兼容调用

```python
from anthropic import Anthropic

client = Anthropic(
    api_key="sk-sp-b879148afe854c45b2850757aa4997fd",
    base_url="https://coding.dashscope.aliyuncs.com/apps/anthropic"
)

response = client.messages.create(
    model="qwen3.5-plus",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "你好"}
    ]
)
```

### CrewAI 集成

```python
from crewai import Agent

# 使用百炼模型
agent = Agent(
    role="研究员",
    goal="AI 研究",
    llm="dashscope-qwen3.5-plus"
)

# 或使用智谱
agent = Agent(
    role="研究员",
    llm="dashscope-glm-5"
)

# 或使用 Kimi
agent = Agent(
    role="研究员",
    llm="dashscope-kimi-k2.5"
)
```

### TangAgents 集成

```python
from tangagents import Agent

# 支持多模型切换
agent = Agent(
    role="AI 研究员",
    model="dashscope-qwen3.5-plus"  # 或 glm-5, kimi-k2.5
)
```

---

## 🎯 模型使用策略

### 按任务类型

| 任务类型 | 推荐模型 | 说明 |
|----------|----------|------|
| **核心决策** | qwen3.5-plus | 复杂推理、多模态 |
| **代码生成** | qwen3-coder-plus | 代码专用优化 |
| **长文本** | kimi-k2.5 | 长上下文支持 |
| **视觉理解** | qwen3.5-plus / kimi-k2.5 | 图像分析 |
| **常规任务** | glm-4.7 | 性价比高 |
| **深度思考** | glm-5 / qwen3-max | 复杂推理 |

### 按优先级

| 优先级 | 模型 | 说明 |
|--------|------|------|
| **P0 核心** | qwen3.5-plus | 老庄指示、战略决策 |
| **P1 重要** | qwen3.5-plus / glm-5 | 功能开发、方案设计 |
| **P2 常规** | glm-4.7 / qwen3-coder-next | 文档、代码 |
| **P3 辅助** | kimi-k2.5 | 长文本处理 |

---

## 🔄 多模型故障转移

```python
# 模型降级链
FALLBACK_CHAIN = [
    "qwen3.5-plus",      # 主模型
    "glm-5",             # 备选 1
    "kimi-k2.5",         # 备选 2
    "minimax-m2.5",      # 备选 3（MiniMax 源）
]

def call_with_fallback(prompt):
    for model in FALLBACK_CHAIN:
        try:
            return call_model(model, prompt)
        except Exception as e:
            print(f"[WARN] {model} failed: {e}")
            continue
    raise Exception("All models failed")
```

---

## 📊 模型对比

| 模型 | 推理能力 | 代码能力 | 中文理解 | 长上下文 | 多模态 |
|------|----------|----------|----------|----------|--------|
| qwen3.5-plus | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ✅ |
| qwen3-max | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ❌ |
| qwen3-coder-plus | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ❌ |
| glm-5 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ❌ |
| glm-4.7 | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ❌ |
| kimi-k2.5 | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ✅ |
| minimax-m2.5 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ❌ |

---

## 💰 成本优化

### 模型选择建议

```python
# 简单任务用便宜模型
if task.complexity < 0.5:
    model = "glm-4.7"  # 便宜
elif task.is_code:
    model = "qwen3-coder-plus"  # 代码专用
elif task.needs_vision:
    model = "qwen3.5-plus"  # 多模态
elif task.long_context:
    model = "kimi-k2.5"  # 长上下文
else:
    model = "qwen3.5-plus"  # 默认主模型
```

### 批量处理优化

```python
# 批量任务使用性价比高的模型
for doc in batch_docs:
    result = call_model("glm-4.7", doc)
```

---

## 📈 监控与告警

### 每日检查
- API 调用次数
- Token 使用量
- 错误率
- 响应时间

### 告警阈值
- 错误率 > 5% → 告警
- 响应时间 > 5s → 告警
- 连续失败 3 次 → 切换模型

---

## 🔗 相关链接

- **百炼控制台:** https://bailian.console.aliyun.com
- **API 文档:** https://help.aliyun.com/zh/dashscope
- **模型广场:** https://bailian.console.aliyun.com/model-market
- **定价详情:** https://help.aliyun.com/zh/dashscope/pricing

---

## 🐲 大唐智能 · 模型配置

**主用模型:** MiniMax-M2.5  
**备选模型源:** 百炼大模型（qwen3.5-plus）

**故障转移链:**
```
MiniMax-M2.5 → qwen3.5-plus → glm-5 → kimi-k2.5
```

---

**🐲 贞观之治，始于足下**
