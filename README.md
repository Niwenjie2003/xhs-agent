# 📖 小红书内容策划 Agent

> 一个面向内容创作者的 AI 辅助工具，帮你解决"不会写、写得慢、风格不稳定"的问题。

## ✨ 功能特性

与传统 AI 写作工具不同，该 Agent 会先理解用户输入的主题、目标人群与内容风格，并自动拆解为多个子任务，逐步完成内容生产：

| 步骤 | 说明 |
|------|------|
| 🔍 选题分析 | 分析话题热度、竞品笔记与受众偏好 |
| ✍️ 标题生成 | 生成多个高点击率候选标题供选择 |
| 📝 正文撰写 | 按指定风格撰写完整笔记正文 |
| 🏷️ 标签推荐 | 匹配高流量相关话题标签 |
| 🛡️ 自检优化 | 降低广告感，提升真实感与平台适配性 |

## 🚀 快速开始

无需安装任何依赖，直接用浏览器打开 `index.html` 即可使用。

```bash
# 本地预览
python3 -m http.server 3456
# 访问 http://localhost:3456
```

## 🎯 使用说明

1. **填写创作主题** — 输入你想写的话题，如"秋冬护肤保湿攻略"
2. **选择目标人群** — 学生党 / 职场白领 / 宝妈 / 美妆达人等
3. **选择内容风格** — 真实分享 / 干货教程 / 种草推荐 / 幽默日常 / 情感治愈
4. **设定字数目标** — 滑块调整 200～1000 字
5. **开启智能自检** — 降低广告感、提升真实感、平台适配等优化项
6. **点击生成** — Agent 自动完成全流程，实时展示每个步骤进度

## 📸 页面预览

- 左侧：配置面板（主题输入、人群/风格标签、字数滑块）
- 右侧上：Agent 执行进度追踪（5 步动态展示）
- 右侧下：生成结果（可切换标题、复制全文、查看质量评分）

## 🛠️ 技术栈

- 纯原生 HTML + CSS + JavaScript
- 零依赖，单文件部署
- 响应式布局，支持移动端

## 🔭 后续拓展方向

### 接入真实 AI 大模型

当前版本为 Demo 演示，内容由本地模板生成。后续可接入以下 AI 服务，实现真正的智能生成：

| AI 服务 | 接入方式 | 适用场景 |
|---------|---------|---------|
| **OpenAI GPT-4o** | `fetch` 调用 `/v1/chat/completions` | 综合写作能力强，适合正文撰写 |
| **Claude (Anthropic)** | `fetch` 调用 `/v1/messages` | 长文本理解好，适合自检优化 |
| **DeepSeek** | 兼容 OpenAI 协议，直接替换 baseURL | 中文语料丰富，适合小红书风格 |
| **通义千问 (Qwen)** | 阿里云 DashScope API | 国内访问稳定，中文表达自然 |
| **Kimi (Moonshot)** | `fetch` 调用 `/v1/chat/completions` | 长上下文支持好，适合多轮优化 |
| **混元 (腾讯)** | 腾讯云 API | 与微信/小红书平台生态契合 |

### 接入示意（以 OpenAI 为例）

```javascript
async function callAI(prompt) {
  const res = await fetch('https://api.openai.com/v1/chat/completions', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': `Bearer ${YOUR_API_KEY}`
    },
    body: JSON.stringify({
      model: 'gpt-4o',
      messages: [{ role: 'user', content: prompt }],
      stream: true   // 流式输出，实现打字机效果
    })
  });
  // 处理 SSE 流式返回...
}
```

### 其他扩展方向

- **多模型路由** — 不同子任务分配最适合的模型（如标题用 GPT，正文用 DeepSeek）
- **流式输出** — 接入 SSE/Stream API，实现实时打字机效果
- **历史记录** — 本地 IndexedDB 存储生成历史，支持二次编辑
- **图片配图建议** — 结合 DALL·E / Stable Diffusion 生成封面图灵感
- **爆款数据分析** — 接入小红书热榜 API，实时分析当日热门选题
- **多平台适配** — 一键将内容改写为微博、公众号、抖音文案风格

## 📄 License

MIT
