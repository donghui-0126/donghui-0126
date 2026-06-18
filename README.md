# Hi, I'm Donghui 👋

Crypto Quant Researcher & HFT Systems Engineer based in Seoul, Korea.

High Frequency 알파 리서치 파이프라인을 만들고, 시그널을 발굴하고, 백테스트하고 있습니다.
빗썸 수수료 0bp 기간에 누적 거래대금 10억원 이상을 달성한 경험이 있습니다.

🔗 **Portfolio — https://donghui-0126.github.io**

## What I Do

- **Alpha Research** — Model-based High Frequency Alpha
- **ForwardTest** — Virtual Exchange Forward Test
- **BackTest** — Event-Driven Backtest, Vectorized cross-sectional Backtest
- **Market Microstructure** — Limit order book modeling, online estimation, HFT research

## Highlights

**Rust 시스템 엔지니어링**
- Julia + Rust DLL 하이브리드 OMS를 순수 Rust로 마이그레이션 (FFI 경계 제거, GC 압박 해소)
- 11개 거래소 WebSocket/REST 통합 (빗썸, 업비트, 코인원, 바이낸스, 바이비트, OKX, 비트겟 등)
- 거래소별 상이한 인증 체계 구현 (HS256/HS512 JWT, HMAC-SHA256/SHA512 헤더, 리슨 키)
- Tick-to-trade pipeline: **p50 4.23us, 218K tps** (117개 온라인 피쳐 연산 포함)
- zero-alloc 주문 상태머신 (~50개 전이), `simd-json` 고속 파싱, `DoubleBuffer` lock-free read
- [ Feeder → Matching Engine → Feature Store → Pricing Layer → OMS ] pipeline 구축

**Julia 엔지니어링**
- GC가 있는 언어에서의 성능 최적화 — `@view`, `@inbounds`, pre-allocation 메모리 관리 패턴 적용
- Julia 패키지 한계를 DLL(`ccall`)로 우회 — 이후 OMS-v2 Rust 마이그레이션의 동기가 됨
- Julia 멀티스레딩(`Threads.@threads`, `@spawn`) 기반 병렬 연산 파이프라인 구축
- Julia Heap Allocation을 극한까지 줄여본 경험

**LLM × Research / 실전 트레이딩**
- Claude Code(AI agent) 기반 데이터 분석·리서치 인프라 구축
- Graph-RAG 지식 엔진 / LLM 휴리스틱 진화 / 뉴스→시장 인과 분석을 Rust·Python으로 직접 구현
- 빗썸 수수료 0bp 기간 누적 거래대금 10억원+ 달성

## Tech Stack

**Core:** Rust (execution infra), Julia (alpha research), Python (ML/research)

**Data:** Polars, Parquet, Arrow, DataFrames

**Infra:** OMS, tokio, Claude Code, Supabase, Render

## Featured Projects

| Project | Description | Stack |
|---------|-------------|-------|
| amuredo-OMS-v2 | **Pure Rust OMS** — 27 crates, 11 exchanges, Feeder→Matching→FeatureStore→Pricing→OMS, ML market making. **p50 4.23µs tick-to-trade · 218K tps** | `Rust` `Private` |
| [StoryQuant](https://github.com/donghui-0126/StoryQuant) | News-driven KR equity app — LLM(gpt-4o-mini) headline classification + graph-RAG attribution. **Honest validation: filters 70~90% noise.** Supabase·Render 실배포 · [live ↗](https://donghui-0126.github.io/StoryQuant/) | `Python` `JS` `LLM` |
| [heuristiX](https://github.com/donghui-0126/heuristiX-v2) | LLM dispatching-rule evolution for dynamic FJSSP — EoH 4-operator 진화, 6-mode RAG ablation, Rust DES sim + 대시보드 · [live ↗](https://heuristix.onrender.com) | `Python` `Rust` `LLM` |
| [amure-do](https://github.com/donghui-0126/amure-do) / [amure-db](https://github.com/donghui-0126/amure-db) | Rust graph-RAG 지식 엔진 — 임베딩+그래프 3-layer 검색, 도메인 불문 가설 기반 연구 엔진으로 일반화 | `Rust` |
| AMuReDoTrade | Live trading system — multi-exchange execution (Binance, Upbit, Bithumb, Coinone) | `Private` |

## Alpha Research Tooling

| Project | Description | Stack |
|---------|-------------|-------|
| [amuredo-EDA](https://github.com/donghui-0126/amuredo-EDA) | Alpha research & backtest tooling — signal screening, path analysis, Streamlit dashboard | `Julia` `Python` |
| [amuredo-alphago](https://github.com/donghui-0126/amuredo-alphago) | Alpha factory — 1D/2D alpha screening, cross-sectional analysis, rolling ML | `Julia` `Python` |
| [amuredo-StrategyStore](https://github.com/donghui-0126/amuredo-StrategyStore) | Strategy storage & management | `Julia` |

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
- Hyeong-jin Son, **Lim Donghui**, & Young-woo Han. (2023). *Reinforcement learning portfolio optimization based on portfolio theory.* 한국정보처리학회 학술대회논문집, 30(2), 961-962.

**Experience**
- KHU AIMS LABS - Undergraduate Researcher (2024) : Combinatorial Optimization with RL (TSP, VRP)
- 모두의 연구소 PISTAR LAB (2024) : Algorithm Trading with AI
- KHUDA 3-4기 Financial Track (2023) : 경희대 데이터분석/AI 동아리
- 금융공학 학회 UFEA 36기

## Side Projects & Archive

<details>
<summary>Side projects & 2022-2024 아카이브</summary>

**Side Projects (2026)**
- [better-than-tomorrow](https://github.com/donghui-0126/better-than-tomorrow) — 대화 기록에서 일일 개발 블로그를 생성하는 Claude Code 플러그인
- [drawing-run](https://github.com/donghui-0126/drawing-run) — 실제 도로망 위에 도형을 그리는 GPS 아트 러닝 경로 PoC

**2022-2024 Projects**
- Causal Inference: Factor of Happiness [(2024)](https://github.com/donghui-0126/Causal-Inference-Factor-of-Happiness)
- Sentiment Analysis by BERT [(2023)](https://github.com/donghui-0126/mini-project/tree/main/khuda)
- Virtual Trading Based on TA [(2023)](https://github.com/donghui-0126/team1_fin_portfolio-ta/tree/main)
- Predict Resell Price of Shoes [(2023)](https://github.com/donghui-0126/mini-project/tree/main/shoes-project)
- Dacon: Lettuce Growth Forecast AI [(2022)](https://github.com/donghui-0126/machine-learning/tree/main/dacon)
- What is important Stats in NBA? [(2022)](https://github.com/donghui-0126/mini-project)

**Code Archive:** [Algorithm](https://github.com/donghui-0126/baekjoon-algorithm) | [ML/DL](https://github.com/donghui-0126/machine-learning) | [RL](https://github.com/donghui-0126/Reinforce-Learning) | [Data Structure](https://github.com/donghui-0126/Data-structure) | [Rust](https://github.com/donghui-0126/Hello-RUST-World)
</details>

---

📫 lukedonghui@gmail.com &nbsp;·&nbsp; 🔗 [Portfolio](https://donghui-0126.github.io) &nbsp;·&nbsp; [StoryQuant Demo](https://donghui-0126.github.io/StoryQuant/)
