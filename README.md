# AI Model Battle Analysis

> Claude Fable 5 vs GLM 5.2 vs GPT 5.6 vs Grok 4.5 — 46 YouTube video transcripts analyzed by AI


**[한국어](README.ko.md)** | **[日本語](README.ja.md)** | **[中文](README.zh-CN.md)** | **[Español](README.es.md)**
**[Live Demo](https://pinion05.github.io/ai-model-battle/)** | **[한국어](README.ko.md)** | **[日本語](README.ja.md)** | **[中文](README.zh-CN.md)** | **[Español](README.es.md)**

## Overview

| Metric | Data |
|---|---|
| Videos Analyzed | 46 |
| Transcripts | 619KB (634,014 chars) |
| Total Views | 1M+ |
| Test Cases | 117 |
| Languages | EN / KO / CN / RU / PT |

## Winner Distribution

| Winner | Videos | Strength |
|---|---|---|
| **Fable 5** | 14 | Design, 3D, autonomous work, creativity |
| **Split** | 18 | No single best model |
| **GLM 5.2** | 5 | Value, open-source, game builds |
| **None** | 5 | Analysis/review format |
| **GPT 5.6** | 3 | One-shot coding, cost efficiency |
| **Grok 4.5** | 1 | Unexpected wins |

## Key Findings

### Price Shock
- GLM 5.2: $1.40/M input (open-weight, free download)
- GPT 5.6 Sol: ~$2.00/M input
- Fable 5: $5.00/M input, $25/M output (**11x** more expensive than GLM)
- One task: GLM $2, Fable $14, GPT 5.5 $37

### "No Single Best Model"
- 18 videos (39%) concluded "winner depends on task"
- Benchmark score 92 vs 88 difference is imperceptible in real use
- Most common conclusion: "Pick the right model for the job"

### Open Source Strikes Back
- GLM 5.2 (free) frequently matched or beat premium models
- Minecraft clone, 3D solar system, web design — GLM dominated
- "Call me crazy, I kind of like this better than what Claude Fable 5 made"

## Methodology

1. **Video Collection**: YouTube search for 49 comparison videos
2. **Transcript Extraction**: yt-dlp + bgutil PO Token + tor SOCKS proxy (46/49 success)
3. **AI Analysis**: Xiaomi MiMo-V2.5-Pro API, 1 video = 1 serial analysis (full transcript)
4. **Translation**: Google Gemini 2.5 Flash via OpenRouter
5. **Site Generation**: Inline JSON + dark theme card components

### Transcript Extraction Pipeline

YouTube's 4-layer anti-bot system bypass:

```
yt-dlp (metadata, direct IP)
    -> caption URL + signature
tor SOCKS5 proxy (caption download, different IP)
    -> json3 caption data
bgutil-ytdlp-pot-provider (PO Token generation)
    -> bot detection bypass
```

## Tech Stack

- **Analysis**: Xiaomi MiMo-V2.5-Pro
- **Translation**: Google Gemini 2.5 Flash (OpenRouter)
- **Extraction**: yt-dlp + tor + bgutil-ytdlp-pot-provider
- **Infrastructure**: GJC v0.10.1

## License

MIT — Analysis data is aggregated from YouTube creators' subjective evaluations.
