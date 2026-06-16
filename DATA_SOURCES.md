# 데이터 출처 및 라이선스

학생 배포 시 출처를 함께 안내하기 위한 메모. 모든 데이터는 **무인증(로그인 없이)** 접근 가능하거나 강의용으로 동봉되었습니다.

| 파일 | 내용 | 출처 | 취득 방법/비고 |
|---|---|---|---|
| `world_happiness_owid.csv` | 세계 행복 점수 패널 **2011–2025** (158개국, 2025년 기준) | Our World in Data — "Self-reported life satisfaction" (Cantril ladder). 원자료: World Happiness Report / Gallup World Poll | OWID grapher의 공개 CSV 내보내기로 취득(무인증). 컬럼: `entity, code, year, cantril_ladder_score` |
| `apt_realprice_202105.csv` | 아파트 매매 실거래가 (2021년 5월, 전국, 약 6.8만 건) | 국토교통부 실거래가 공개시스템(rt.molit.go.kr) | 강사 수집본. 한글 컬럼 + 거래금액에 천단위 쉼표(예: `"18,300"`) → **3교시 정제 실습용** |
| `btc_usd_daily.csv` | 비트코인(BTC/USD) 일별 OHLCV | CryptoDataDownload (Gemini 거래소) | 1행은 메타데이터 → `pd.read_csv(..., skiprows=1)`. **1교시 동기부여 차트용** |
| `gold_5y.csv` | 금 시세 시계열 (`ds`, `y` 형식) | 강사 수집본 | 1교시 보조 · 4교시 선그래프 예시 |
| `worldcup_results.csv` | 국제 축구 A매치 결과 **1872–2026** (49,477경기, 한국 1,010경기 포함) | martj42/international_results (GitHub 공개 데이터셋) | 강사 스냅샷본(라이브 데이터 드리프트 방지). **2026 월드컵 진행분 포함 → 미실시 경기는 결측 = 결측 학습 소재.** 컬럼: `date, home_team, away_team, home_score, away_score, tournament, city, country, neutral`. **5교시 캡스톤(풀 파이프라인)용** |
| `spotify_tracks.csv` | Spotify 트랙 **114,000곡** × 20열 (track_genre 114종, 오디오 피처: danceability/energy/valence/tempo/loudness/acousticness 등, popularity 0~100, duration_ms). BTS 등 K-pop 포함 | maharshipandya/spotify-tracks-dataset (Hugging Face / Kaggle, **BSD 라이선스**) | Spotify Web API 수집본. 한 곡이 여러 장르에 중복 수록(고유 track_id 89,741) → **중복 제거 학습 소재**. **5교시 프로젝트(음악 분석)용.** 주의: 발매연도 컬럼 없음, popularity는 스트리밍 횟수가 아닌 0~100 인기점수 |
| `BMDOHYEON.ttf` | 한글 폰트 (배민 도현체) | 우아한형제들 — 상업적 이용 무료 폰트 | 모든 차트 한글 깨짐 방지. try/except 폴백으로 사용 |
| `raw_source/world_happiness_2017.csv` | 행복 보고서 2017 (요인별 컬럼: Economy/Family/Health 등) | World Happiness Report 2017 | **폴백·참고용.** 최신판(OWID)이 점수 중심이라, 요인 상관 설명이 필요하면 보조로 사용 |

## 데이터셋 운용 원칙
- **실습 백본은 seaborn 내장 데이터**(`titanic`, `tips`, `penguins`) — 다운로드/경로 문제 없이 항상 실행. 이 저장소엔 동봉하지 않음(seaborn이 인터넷에서 직접 로드).
- 동봉 데이터는 노트북의 **`data_path()` 헬퍼**로 로드: **로컬(`../data/`, `data/`)에 있으면 로컬, 없으면 이 저장소의 raw URL** 에서 자동 취득. → **코랩 수강생은 업로드 불필요**, 노트북만 열면 됨.
  - raw 베이스: `https://raw.githubusercontent.com/acho98/gunyang-data/main/`
  - 한글 폰트도 로컬에 없으면 같은 URL에서 자동 다운로드.
  - `worldcup_results.csv`는 항상 raw URL에서 직접 로드(캡스톤).
- 모든 로드 코드는 실제 실행 검증을 거침(강사 측 검증 로그: `intro_data_analysis/data/VALIDATION_LOG.txt`).
