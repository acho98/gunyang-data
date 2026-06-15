# 데이터 출처 및 라이선스 (data/)

학생 배포 시 출처를 함께 안내하기 위한 메모. 모든 데이터는 **무인증(로그인 없이)** 접근 가능하거나 강의용으로 동봉되었습니다.

| 파일 | 내용 | 출처 | 취득 방법/비고 |
|---|---|---|---|
| `world_happiness_owid.csv` | 세계 행복 점수 패널 **2011–2025** (158개국, 2025년 기준) | Our World in Data — "Self-reported life satisfaction" (Cantril ladder). 원자료: World Happiness Report / Gallup World Poll | OWID grapher의 공개 CSV 내보내기로 취득(무인증). 컬럼: `entity, code, year, cantril_ladder_score` |
| `apt_realprice_202105.csv` | 아파트 매매 실거래가 (2021년 5월, 전국, 약 6.8만 건) | 국토교통부 실거래가 공개시스템(rt.molit.go.kr) | 강사 수집본. 한글 컬럼 + 거래금액에 천단위 쉼표(예: `"18,300"`) → **3장 정제 데모용** |
| `btc_usd_daily.csv` | 비트코인(BTC/USD) 일별 OHLCV | CryptoDataDownload (Gemini 거래소) | 1행은 메타데이터 → `pd.read_csv(..., skiprows=1)`. **1장 동기부여 차트용** |
| `gold_5y.csv` | 금 시세 시계열 (`ds`, `y` 형식) | 강사 수집본 | 1장 보조/5장 시계열 예시 |
| `BMDOHYEON.ttf` | 한글 폰트 (배민 도현체) | 우아한형제들 — 상업적 이용 무료 폰트 | 4장 시각화 한글 깨짐 방지. try/except 폴백으로 사용 |
| `raw_source/world_happiness_2017.csv` | 행복 보고서 2017 (요인별 컬럼: Economy/Family/Health 등) | World Happiness Report 2017 | **폴백·참고용.** 최신판(OWID)이 점수 중심이라, 요인 상관 설명이 필요하면 보조로 사용 |

## 데이터셋 운용 원칙
- **실습 백본은 seaborn 내장 데이터**(`titanic`, `tips`, `penguins`) — 다운로드/경로 문제 없이 항상 실행.
- 동봉 CSV는 노트북에서 **상대경로 `../data/파일명`** 으로 로드(코랩 사용 시 업로드 안내 포함).
- 모든 로드 코드는 실제 실행 검증을 거침(검증 로그: `data/VALIDATION_LOG.txt`).
