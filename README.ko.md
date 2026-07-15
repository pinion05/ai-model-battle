# AI 모델 전투 분석

> Claude Fable 5 vs GLM 5.2 vs GPT 5.6 vs Grok 4.5 — AI가 분석한 46개의 YouTube 비디오 스크립트

**[라이브 데모](https://pinion05.github.io/ai-model-battle/)** | **[한국어](README.ko.md)** | **[日本語](README.ja.md)** | **[中文](README.zh-CN.md)** | **[Español](README.es.md)**

**[English](README.md)** | **[日本語](README.ja.md)** | **[中文](README.zh-CN.md)** | **[Español](README.es.md)**

## 개요

| 지표 | 데이터 |
|---|---|
| 분석된 비디오 | 46 |
| 스크립트 | 619KB (634,014자) |
| 총 조회수 | 100만+ |
| 테스트 케이스 | 117 |
| 언어 | EN / KO / CN / RU / PT |

## 승자 분포

| 승자 | 비디오 | 강점 |
|---|---|---|
| **Fable 5** | 14 | 디자인, 3D, 자율 작업, 창의성 |
| **분할** | 18 | 단일 최고의 모델 없음 |
| **GLM 5.2** | 5 | 가치, 오픈 소스, 게임 빌드 |
| **없음** | 5 | 분석/리뷰 형식 |
| **GPT 5.6** | 3 | 원샷 코딩, 비용 효율성 |
| **Grok 4.5** | 1 | 예상치 못한 승리 |

## 주요 결과

### 가격 충격
- GLM 5.2: $1.40/M 입력 (오픈 가중치, 무료 다운로드)
- GPT 5.6 Sol: ~$2.00/M 입력
- Fable 5: $5.00/M 입력, $25/M 출력 (GLM보다 **11배** 비쌈)
- 한 가지 작업: GLM $2, Fable $14, GPT 5.5 $37

### "단일 최고의 모델은 없다"
- 18개 비디오 (39%)는 "승자는 작업에 따라 달라진다"고 결론 내렸다.
- 벤치마크 점수 92 vs 88의 차이는 실제 사용에서 인지할 수 없다.
- 가장 일반적인 결론: "작업에 적합한 모델을 선택하라"

### 오픈 소스의 반격
- GLM 5.2 (무료)는 프리미엄 모델과 자주 일치하거나 능가했다.
- Minecraft 클론, 3D 태양계, 웹 디자인 — GLM이 지배적이었다.
- "미쳤다고 할지 모르지만, Claude Fable 5가 만든 것보다 이게 더 좋다"

## 방법론

1. **비디오 수집**: 49개의 비교 비디오를 YouTube에서 검색
2. **스크립트 추출**: yt-dlp + bgutil PO Token + tor SOCKS 프록시 (46/49 성공)
3. **AI 분석**: Xiaomi MiMo-V2.5-Pro API, 1개 비디오 = 1회 직렬 분석 (전체 스크립트)
4. **번역**: OpenRouter를 통한 Google Gemini 2.5 Flash
5. **사이트 생성**: 인라인 JSON + 다크 테마 카드 구성 요소

### 스크립트 추출 파이프라인

YouTube의 4단계 봇 방지 시스템 우회:

```
yt-dlp (메타데이터, 직접 IP)
    -> 캡션 URL + 서명
tor SOCKS5 프록시 (캡션 다운로드, 다른 IP)
    -> json3 캡션 데이터
bgutil-ytdlp-pot-provider (PO Token 생성)
    -> 봇 감지 우회
```

## 기술 스택

- **분석**: Xiaomi MiMo-V2.5-Pro
- **번역**: Google Gemini 2.5 Flash (OpenRouter)
- **추출**: yt-dlp + tor + bgutil-ytdlp-pot-provider
- **인프라**: GJC v0.10.1

## 라이선스

MIT — 분석 데이터는 YouTube 크리에이터의 주관적인 평가를 집계한 것입니다.