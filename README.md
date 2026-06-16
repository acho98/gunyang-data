# gunyang-data

건양대 **초급 데이터 분석** 강의 실습용 데이터셋.
노트북에서 **다운로드·업로드 없이** raw URL로 자동 로드됩니다 (구글 코랩 OK).

## 수록 파일

| 파일 | 내용 | 쓰이는 곳 |
|---|---|---|
| `btc_usd_daily.csv` | 비트코인(BTC/USD) 일별 시세 (CryptoDataDownload) | 1교시 동기부여 차트 |
| `gold_5y.csv` | 금(Gold) 5년 시세 시계열 (`ds`, `y`) | 1교시 보조 · 4교시 선그래프 |
| `apt_realprice_202105.csv` | 국토부 아파트 실거래가 (2021-05, 전국 약 6.8만 건) | 3교시 정제 실습 (지저분한 데이터) |
| `world_happiness_owid.csv` | 세계 행복 점수 2011–2025 (158개국, Our World in Data) | 4교시 시각화 (막대·히스토그램) |
| `worldcup_results.csv` | 국제 축구 경기 결과 1872–2026 (49,477경기, martj42 스냅샷) | 5교시 캡스톤 (풀 파이프라인) |
| `spotify_tracks.csv` | Spotify 글로벌 트랙 114,000곡 × 오디오 피처 (114장르, BTS 포함) | 5교시 프로젝트 (음악 데이터 분석) |
| `BMDOHYEON.ttf` | 한글 폰트 (배민 도현체, 상업적 이용 무료) | 모든 차트 한글 깨짐 방지 |
| `raw_source/` | 원본·폴백 데이터 보관 | 참고용 |

> seaborn 내장 데이터(`titanic`·`tips`·`penguins`)는 이 저장소에 없습니다 — seaborn이 인터넷에서 직접 불러옵니다.

## 사용법 — 노트북에서 자동 로드

노트북은 `data_path()` 헬퍼로 **로컬에 파일이 있으면 로컬, 없으면 이 저장소의 raw URL** 에서 가져옵니다.
따라서 **코랩 수강생은 노트북만 열면 끝** — 파일 업로드가 필요 없습니다.

```python
import os
DATA_BASE = "https://raw.githubusercontent.com/acho98/gunyang-data/main/"
def data_path(fname):
    for _p in ("../data/" + fname, "data/" + fname):
        if os.path.exists(_p):
            return _p          # 로컬에 있으면 로컬 사용 (강사 환경)
    return DATA_BASE + fname   # 없으면 깃허브에서 바로 로드 (코랩/수강생)

import pandas as pd
df = pd.read_csv(data_path("world_happiness_owid.csv"))
```

한글 폰트(`BMDOHYEON.ttf`)도 로컬에 없으면 위 raw URL에서 자동 다운로드합니다.

자세한 출처·라이선스는 [DATA_SOURCES.md](DATA_SOURCES.md) 참고.
