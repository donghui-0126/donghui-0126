# Hi, I'm Donghui 👋

Crypto Quant Researcher based in Seoul, Korea.

Julia로 알파 리서치 파이프라인을 만들고, 시그널을 발굴하고, 백테스트하고 있습니다.
빗썸 수수료 0bp 기간에 누적 거래대금 10억원 이상을 달성한 경험이 있습니다.

## What I Do

- **Alpha Research** - Cross-sectional alpha screening with HAC t-stats, triple-barrier labeling, signal path analysis
- **Backtesting** - Vectorized cross-sectional backtester, rolling ML models, decay-based alpha modeling
- **Data Pipeline** - Julia-first parallel computation, ClickHouse/Parquet data layer, Streamlit dashboards
- **Market Microstructure** - Limit order book modeling, online estimation, HFT research

## Highlights

**통계 기반 리서치**
- Newey-West HAC 기반 alpha t-stat screening으로 spurious alpha 필터링
- Triple-barrier labeling + signal path analysis로 시그널의 시간적 구조 분석
- Rolling quantile smoothing, cross-sectional rank/percentile normalization 등 다양한 아이디어 기반 분석 파이프라인 구축

**Julia 엔지니어링**
- GC가 있는 언어에서의 성능 최적화 경험 - `@view`, `@inbounds`, pre-allocation, 심볼별 배치 처리 후 `GC.gc()` 호출 등 메모리 관리 패턴 적용
- Julia 패키지 한계를 DLL(`ccall`)로 우회하여 문제를 해결한 경험 — 이후 이 경험이 OMS-v2 Rust 마이그레이션의 동기가 됨
- Julia 멀티스레딩(`Threads.@threads`, `@spawn`) 기반 병렬 연산 파이프라인 구축

**Rust 시스템 엔지니어링**
- Julia + Rust DLL 하이브리드 OMS를 순수 Rust로 마이그레이션 (FFI 경계 제거, GC 압박 해소)
- 27개 크레이트 Cargo workspace, 211개 테스트, 0 warnings
- 11개 거래소 WebSocket/REST 통합 (빗썸, 업비트, 코인원, 바이낸스, 바이비트, OKX, 비트겟 등)
- 거래소별 상이한 인증 체계 구현 (HS256/HS512 JWT, HMAC-SHA256/SHA512 헤더, 리슨 키)
- Tick-to-trade pipeline: **p50 4.23us, 218K tps** (117개 온라인 피쳐 연산 포함)
- zero-alloc 주문 상태머신 (~50개 전이), `simd-json` 고속 파싱, `DoubleBuffer` lock-free read

**Claude Code 기반 개발**
- Claude Code(AI agent)를 활용한 데이터 분석 및 리서치 인프라 구축
- AI 에이전트 기반 EDA 자동화, 알파 리서치 파이프라인 설계, Streamlit 대시보드 개발
- 멀티 에이전트 오케스트레이션으로 분석-구현-검증 워크플로우 자동화

**실전 트레이딩**
- 빗썸 수수료 0bp 기간 누적 거래대금 10억원+ 달성
- Multi-exchange live trading system 운영 (Binance, Upbit, Bithumb, Coinone)

## Tech Stack

**Core:** Julia (alpha research), Rust (execution infra), Python (visualization)

**Data:** Polars, Parquet, ClickHouse, Arrow, DataFrames.jl

**Analysis:** Newey-West HAC, rolling quantiles, EMA, cross-sectional rank/percentile normalization, triple-barrier

**Infra:** tokio, WSL, tmux, Streamlit, Claude Code

## Current Projects

| Project | Description | Stack |
|---------|-------------|-------|
| [amuredo-EDA](https://github.com/donghui-0126/amuredo-EDA) | Alpha research & backtest tooling - signal screening, path analysis, Streamlit dashboard | Julia, Python |
| [amuredo-alphago](https://github.com/donghui-0126/amuredo-alphago) | Alpha factory platform - 1D/2D alpha screening, cross-sectional analysis, rolling ML | Julia, Python |
| [amuredo-StrategyStore](https://github.com/donghui-0126/amuredo-StrategyStore) | Strategy storage & management | Julia |
| amuredo-OMS-v2 | Pure Rust OMS - 27 crates, 11 exchanges, p50 4.23us tick-to-trade | Rust, Private |
| AMuReDoTrade | Live trading system - multi-exchange execution (Binance, Upbit, Bithumb, Coinone) | Private |

## Research Projects

| Project | Topic |
|---------|-------|
| [ML-HFT](https://github.com/donghui-0126/ML-HFT) | High-frequency trading framework with machine learning for futures |
| [deepOBs](https://github.com/donghui-0126/deepOBs) | Short-term predictability in order book markets via deep learning |
| [lob-world-models](https://github.com/donghui-0126/lob-world-models) | Model-based RL for LOB prediction |
| [lob-deep-learning](https://github.com/donghui-0126/lob-deep-learning) | Deep learning models for limit order book |
| [online_estimation](https://github.com/donghui-0126/online_estimation) | Online rolling estimation (mean, weighted mean, std, skew) |
| [JaneStreetKaggle](https://github.com/donghui-0126/JaneStreetKaggle) | Jane Street real-time market data forecasting |
| [Machine-Learning-for-Factor-Investing](https://github.com/donghui-0126/Machine-Learning-for-Factor-Investing) | ML techniques for factor investing |
| [crypto-scalping-RL-Agent](https://github.com/donghui-0126/crypto-scalping-RL-Agent) | RL-based crypto scalping agent with custom chart env |

## Awards

| Year | Competition | Result |
|------|------------|--------|
| 2025 | Jane Street - Real-Time Market Data Forecasting (Kaggle) | Bronze Medal |
| 2024 | BDA X ASCEND - Bitcoin Volatility Prediction | 우수상 |
| 2023 | WorldQuant Alphaton Korea | 3rd Place |
| 2023 | FSI Data Challenge - EV Customer Prediction | 우수상 |

## Research & Experience

**Publication**
- Hyeong-jin Son, **Lim Donhui**, & Young-woo Han. (2023). *Reinforcement learning portfolio optimization based on portfolio theory.* 한국정보처리학회 학술대회논문집, 30(2), 961-962.

**Experience**
- KHU AIMS LABS - Undergraduate Researcher (2024) : Combinatorial Optimization with RL (TSP, VRP)
- 모두의 연구소 PISTAR LAB (2024) : Algorithm Trading with AI
- KHUDA 3-4기 Financial Track (2023) : 경희대 데이터분석/AI 동아리
- 금융공학 학회 UFEA 36기

## Past Projects

<details>
<summary>2022-2024 프로젝트 아카이브</summary>

- Causal Inference: Factor of Happiness [(2024)](https://github.com/donghui-0126/Causal-Inference-Factor-of-Happiness)
- Sentiment Analysis by BERT [(2023)](https://github.com/donghui-0126/mini-project/tree/main/khuda)
- Virtual Trading Based on TA [(2023)](https://github.com/donghui-0126/team1_fin_portfolio-ta/tree/main)
- Predict Resell Price of Shoes [(2023)](https://github.com/donghui-0126/mini-project/tree/main/shoes-project)
- Dacon: Lettuce Growth Forecast AI [(2022)](https://github.com/donghui-0126/machine-learning/tree/main/dacon/%EC%83%81%EC%B6%94%EC%9D%98%20%EC%83%9D%EC%9C%A1%20%ED%99%98%EA%B2%BD%20%EC%83%9D%EC%84%B1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C)
- What is important Stats in NBA? [(2022)](https://github.com/donghui-0126/mini-project/blob/main/What%20is%20important%20NBA%20stats%20_2022%20%EC%9B%B9%ED%8C%8C%EC%9D%B4%EC%8D%AC%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%20%ED%85%80%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8.ipynb)

**Code Archive:** [Algorithm](https://github.com/donghui-0126/baekjoon-algorithm) | [ML/DL](https://github.com/donghui-0126/machine-learning) | [RL](https://github.com/donghui-0126/Reinforce-Learning) | [Data Structure](https://github.com/donghui-0126/Data-structure) | [Rust](https://github.com/donghui-0126/Hello-RUST-World) | [Julia](https://github.com/donghui-0126/Hello-Julia-World)
</details>

---

📫 lukedonghui@gmail.com
