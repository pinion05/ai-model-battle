# AI 모델 대결 분석

> Claude Fable 5 vs GLM 5.2 vs GPT 5.6 vs Grok 4.5 — 유튜브 영상 46개의 트랜스크립트를 AI가 분석한 종합 리포트

[대화형 분석 페이지 보기](https://pinion05.github.io/ai-model-battle/)

## 개요

| 항목 | 데이터 |
|---|---|
| 분석 영상 | 46개 |
| 트랜스크립트 | 619KB (634,014자) |
| 총 조회수 | 1M+ |
| 테스트 케이스 | 117개 |
| 분석 언어 | 한국어 / 영어 / 중국어 / 러시아어 / 포르투갈어 |

## 승자 분포

| 승자 | 영상 수 | 특징 |
|---|---|---|
| **Fable 5** | 14 | 디자인, 3D, 자율 작업, 창의성 |
| **Split (과제별)** | 18 | 단일 최강 모델 없음 |
| **GLM 5.2** | 5 | 가성비, 오픈소스, 게임 빌드 |
| **None** | 5 | 분석/리뷰 형식 |
| **GPT 5.6** | 3 | 원샷 코딩, 비용효율 |
| **Grok 4.5** | 1 | 예상치 못한 승리 |

## 핵심 발견

### 가격 충격
- GLM 5.2: $1.40/M input (오픈웨이트, 무료 다운로드 가능)
- GPT 5.6 Sol: ~$2.00/M input
- Fable 5: $5.00/M input, $25/M output (GLM 대비 **11배** 비싸다)
- 같은 작업에서 GLM이 $2, Fable이 $14, GPT 5.5가 $37 든 사례 존재

### "단일 최강 모델은 없다"
- 18개 영상(39%)이 "과제마다 승자가 다르다"는 결론
- 벤치마크 점수 92 vs 88 차이가 실제 사용에서는 체감 불가
- 코딩 유튜버들이 가장 많이 내린 결론: "용도에 맞게 골라 써라"

### 오픈소스의 역습
- GLM 5.2(무료)가 유료 모델과 동등하거나 더 나은 결과를 빈번히 생성
- Minecraft 클론, 3D 태양계, 웹 디자인 등에서 프리미엄 모델 압도
- "Call me crazy, I kind of like this better than what Claude Fable 5 made"

## 방법론

1. **영상 수집**: YouTube 검색으로 49개 비교 영상 발견
2. **트랜스크립트 추출**: yt-dlp + bgutil PO Token + tor SOCKS proxy로 46/49 성공
3. **AI 분석**: Xiaomi MiMo-V2.5-Pro API로 1영상=1순차 분석 (풀 트랜스크립트)
4. **한국어 번역**: Google Gemini 2.5 Flash via OpenRouter
5. **사이트 생성**: 인라인 JSON + 다크 테마 카드 컴포넌트

### 트랜스크립트 추출 기술 스택

YouTube의 4중 anti-bot 시스템(IP rate limit + bot detection + PO Token + tor 차단)을 돌파하기 위한 파이프라인:

```
yt-dlp (메타데이터 추출, 직접 IP)
    ↓ 자막 URL + signature 획득
tor SOCKS5 proxy (캡션 다운로드, 다른 IP)
    ↓ json3 포맷 캡션 데이터
bgutil-ytdlp-pot-provider (PO Token 생성)
    ↓ bot detection 우회
youtube-transcript-api (최종 검증)
```

## 기술 스택

- **분석**: Xiaomi MiMo-V2.5-Pro (Token Plan Singapore)
- **번역**: Google Gemini 2.5 Flash (OpenRouter)
- **추출**: yt-dlp 2026.07.04 + tor 0.4.8.10 + bgutil-ytdlp-pot-provider 1.3.1
- **인프라**: GJC v0.10.1 (gajae-code)

## 라이선스

MIT — 분석 데이터는 유튜브 크리에이터들의 주관적 평가를 집성한 것입니다.
