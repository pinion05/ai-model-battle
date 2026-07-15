将此 Markdown 文档翻译成中文。保留所有 Markdown 格式、URL、代码块、表格结构、数字、模型名称（GPT、GLM、Fable、Claude、Grok、Opus、Sonnet）和技术术语（API、token、UI、3D、prompt 等）为英文。只翻译自然语言文本：

# AI 模型大战分析

> Claude Fable 5 vs GLM 5.2 vs GPT 5.6 vs Grok 4.5 — 46 个 YouTube 视频转录本经 AI 分析

**[实时演示](https://pinion05.github.io/ai-model-battle/)** | **[한국어](README.ko.md)** | **[日本語](README.ja.md)** | **[中文](README.zh-CN.md)** | **[Español](README.es.md)**

## 概述

| 指标 | 数据 |
|---|---|
| 分析视频数 | 46 |
| 转录本 | 619KB (634,014 字符) |
| 总观看次数 | 1M+ |
| 测试用例 | 117 |
| 语言 | EN / KO / CN / RU / PT |

## 赢家分布

| 赢家 | 视频数 | 优势 |
|---|---|---|
| **Fable 5** | 14 | 设计、3D、自主工作、创造力 |
| **平局** | 18 | 没有单一的最佳模型 |
| **GLM 5.2** | 5 | 价值、开源、游戏构建 |
| **无** | 5 | 分析/评论格式 |
| **GPT 5.6** | 3 | 一次性编码、成本效益 |
| **Grok 4.5** | 1 | 意外获胜 |

## 主要发现

### 价格冲击
- GLM 5.2：$1.40/M 输入（开源，免费下载）
- GPT 5.6 Sol：~$2.00/M 输入
- Fable 5：$5.00/M 输入，$25/M 输出（比 GLM 贵 **11 倍**）
- 一个任务：GLM $2，Fable $14，GPT 5.5 $37

### “没有单一的最佳模型”
- 18 个视频（39%）得出结论：“赢家取决于任务”
- 基准分数 92 与 88 的差异在实际使用中微乎其微
- 最常见的结论：“为工作选择合适的模型”

### 开源反击
- GLM 5.2（免费）经常与高级模型匹敌或超越
- Minecraft 克隆、3D 太阳系、网页设计 — GLM 占据主导地位
- “叫我疯子吧，我有点喜欢这个胜过 Claude Fable 5 制作的”

## 方法论

1. **视频收集**：YouTube 搜索 49 个对比视频
2. **转录本提取**：yt-dlp + bgutil PO Token + tor SOCKS 代理（46/49 成功）
3. **AI 分析**：Xiaomi MiMo-V2.5-Pro API，1 个视频 = 1 次串行分析（完整转录本）
4. **翻译**：通过 OpenRouter 使用 Google Gemini 2.5 Flash
5. **网站生成**：内联 JSON + 深色主题卡片组件

### 转录本提取流程

绕过 YouTube 的 4 层反机器人系统：

```
yt-dlp (metadata, direct IP)
    -> caption URL + signature
tor SOCKS5 proxy (caption download, different IP)
    -> json3 caption data
bgutil-ytdlp-pot-provider (PO Token generation)
    -> bot detection bypass
```

## 技术栈

- **分析**：Xiaomi MiMo-V2.5-Pro
- **翻译**：Google Gemini 2.5 Flash (OpenRouter)
- **提取**：yt-dlp + tor + bgutil-ytdlp-pot-provider
- **基础设施**：GJC v0.10.1

## 许可证

MIT — 分析数据汇总自 YouTube 创作者的主观评估。