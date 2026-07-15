# Análisis de Batalla de Modelos de IA

> Claude Fable 5 vs GLM 5.2 vs GPT 5.6 vs Grok 4.5 — 46 transcripciones de videos de YouTube analizadas por IA

**[Live Demo](https://pinion05.github.io/ai-model-battle/)** | **[한국어](README.ko.md)** | **[日本語](README.ja.md)** | **[中文](README.zh-CN.md)** | **[Español](README.es.md)**

## Resumen

| Métrica | Datos |
|---|---|
| Videos Analizados | 46 |
| Transcripciones | 619KB (634,014 chars) |
| Vistas Totales | 1M+ |
| Casos de Prueba | 117 |
| Idiomas | EN / KO / CN / RU / PT |

## Distribución de Ganadores

| Ganador | Videos | Fuerza |
|---|---|---|
| **Fable 5** | 14 | Design, 3D, autonomous work, creativity |
| **Split** | 18 | No single best model |
| **GLM 5.2** | 5 | Value, open-source, game builds |
| **None** | 5 | Analysis/review format |
| **GPT 5.6** | 3 | One-shot coding, cost efficiency |
| **Grok 4.5** | 1 | Unexpected wins |

## Hallazgos Clave

### Impacto en el Precio
- GLM 5.2: $1.40/M input (open-weight, free download)
- GPT 5.6 Sol: ~$2.00/M input
- Fable 5: $5.00/M input, $25/M output (**11x** más caro que GLM)
- Una tarea: GLM $2, Fable $14, GPT 5.5 $37

### "No Hay Un Único Mejor Modelo"
- 18 videos (39%) concluyeron que "el ganador depende de la tarea"
- La diferencia de puntuación de referencia de 92 vs 88 es imperceptible en el uso real
- Conclusión más común: "Elige el modelo adecuado para el trabajo"

### El Código Abierto Contraataca
- GLM 5.2 (gratis) con frecuencia igualó o superó a los modelos premium
- Clon de Minecraft, sistema solar 3D, diseño web — GLM dominó
- "Llámame loco, pero me gusta más esto que lo que hizo Claude Fable 5"

## Metodología

1. **Recopilación de Videos**: Búsqueda en YouTube de 49 videos de comparación
2. **Extracción de Transcripciones**: yt-dlp + bgutil PO Token + tor SOCKS proxy (46/49 éxitos)
3. **Análisis de IA**: Xiaomi MiMo-V2.5-Pro API, 1 video = 1 análisis serial (transcripción completa)
4. **Traducción**: Google Gemini 2.5 Flash via OpenRouter
5. **Generación del Sitio**: JSON en línea + componentes de tarjeta con tema oscuro

### Pipeline de Extracción de Transcripciones

Bypass del sistema anti-bot de 4 capas de YouTube:

```
yt-dlp (metadata, direct IP)
    -> caption URL + signature
tor SOCKS5 proxy (caption download, different IP)
    -> json3 caption data
bgutil-ytdlp-pot-provider (PO Token generation)
    -> bot detection bypass
```

## Tech Stack

- **Análisis**: Xiaomi MiMo-V2.5-Pro
- **Traducción**: Google Gemini 2.5 Flash (OpenRouter)
- **Extracción**: yt-dlp + tor + bgutil-ytdlp-pot-provider
- **Infraestructura**: GJC v0.10.1

## Licencia

MIT — Los datos de análisis se agregan a partir de las evaluaciones subjetivas de los creadores de YouTube.