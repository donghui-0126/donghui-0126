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

## The Journey

데이터 분석으로 출발해 **강화학습에서 트레이딩에 빠진** 뒤, 매 단계마다 한계에 부딪히고 그걸 풀려고 다음 도구로 옮겨간 궤적입니다.
예측 → 의사결정 → 실행, Python → Julia → Rust.

**2022–2023 · AI · 데이터 분석**
- 🔴 **문제** — 데이터에서 어떻게 *의미 있는 패턴*을 뽑아낼까?
- 🟢 **해결** — 머신러닝·통계·EDA로 데이터 분석에 입문. 여러 도메인 데이터를 다루며 기초 체력을 쌓음.
- `machine-learning` · `mini-project` · `ML/DL 기초`

**2023–2024 · 강화학습 — 트레이딩에 빠지다**
- 🔴 **문제** — 분석에만 머물면 의미가 없다. 결국 *시장에서 사고팔며 행동*해야 한다 — 단발 예측으론 부족.
- 🟢 **해결** — 여기서부터 트레이딩에 본격적으로 빠짐. 매매를 *순차 의사결정 문제*로 보고 RL로 접근 — 커스텀 차트 환경·스캘핑 에이전트, 연구실에서 조합최적화 RL(TSP·VRP).
- `Reinforce-Learning` · `crypto-scalping-RL` · `Gym-Trading-Env` · `KHU AIMS LAB`

**2024 · 마켓 마이크로구조 · HFT**
- 🔴 **문제** — RL 백테스트가 실제 *체결·호가창 동역학*을 무시 → 시뮬과 실거래의 괴리.
- 🟢 **해결** — 오더북을 직접 모델링. LOB 딥러닝, online estimation, 고빈도 리서치. Jane Street(Kaggle Bronze 🥉).
- 🟣 **+Rust 입문** — 이 무렵 『The Rust Programming Language』를 소유권·스마트 포인터까지 완독. 훗날 OMS Rust 재작성의 씨앗.
- `lob-deep-learning` · `deepOBs` · `online_estimation` · `ML-HFT` · `Hello-RUST-World`

**2025 · Julia 알파 리서치**
- 🔴 **문제** — Python은 연구는 빠르지만 *대규모 백테스트·실시간 연산이 느리다.*
- 🟢 **해결** — Julia로 알파 리서치·백테스트 파이프라인 구축. `@view`·`@inbounds`·pre-alloc로 GC 최소화, 패키지 한계는 `ccall` DLL로 우회, 멀티스레딩 병렬화.
- `amuredo-EDA` · `amuredo-alphago` · `amuredo-StrategyStore`

**2025 · Julia OMS — 온몸 비틀기 최적화**
- 🔴 **문제** — 리서치를 실거래로. GC가 있는 Julia로 *마이크로초 핫패스*를 버틸 수 있나?
- 🟢 **해결** — Julia로 OMS를 직접 구현하고 성능을 극한까지 짜냄:
  - `@view` zero-copy 슬라이싱 · `@inbounds` 경계검사 제거
  - pre-allocation + in-place(`!`) 버퍼 재사용으로 **heap allocation 극한 감소**
  - type stability 확보(`@code_warntype`), 핫루프 박싱·동적 디스패치 제거
  - `Threads.@threads`·`@spawn` 병렬 연산 파이프라인
  - Julia 패키지·성능 한계는 `ccall` **Rust DLL**로 우회 (하이브리드)
- `Julia OMS · ccall FFI · Rust DLL hotpath`

**2026 · 현재 — 순수 Rust OMS** 🦀
- 🔴 **문제** — 온몸을 비틀어도 FFI 경계 오버헤드 + Julia *GC 압박*이 레이턴시·안정성의 병목.
- 🟢 **해결** — OMS 전면을 순수 Rust로 마이그레이션. zero-alloc 상태머신, 11개 거래소 통합 → **tick-to-trade p50 4.23µs · 218K tps**.
- 🔵 **진행중** — **2026년 1월**부터 Claude Code(AI 에이전트)로 개발 가속, 현재도 활발히 진행 중.
- `amuredo-OMS-v2 (Rust) · 102 commits / 2026`

## Featured Projects

| Project | Description | Stack |
|---------|-------------|-------|
| amuredo-OMS-v2 | **Pure Rust OMS** — 27 crates, 11 exchanges, Feeder→Matching→FeatureStore→Pricing→OMS, ML market making. **p50 4.23µs tick-to-trade · 218K tps** | `Rust` `Private` |
| [StoryQuant](https://github.com/donghui-0126/StoryQuant) | News-driven KR equity app — LLM(gpt-4o-mini) headline classification + RAG. **Honest validation: filters 70~90% noise.** Supabase·Render 실배포 · [live ↗](https://donghui-0126.github.io/StoryQuant/) | `Python` `JS` `LLM` |
| [heuristiX](https://github.com/donghui-0126/heuristiX-v2) | LLM dispatching-rule evolution for dynamic FJSSP — EoH 4-operator 진화, 6-mode RAG ablation, Rust DES sim + 대시보드 · [live ↗](https://heuristix.onrender.com) | `Python` `Rust` `LLM` |
| [amure-do](https://github.com/donghui-0126/amure-do) / [amure-db](https://github.com/donghui-0126/amure-db) | Rust graph-RAG 지식 엔진 — 임베딩+그래프 3-layer 검색, 도메인 불문 가설 기반 연구 엔진으로 일반화 | `Rust` |
| AMuReDoTrade | Live trading system — multi-exchange execution (Binance, Upbit, Bithumb, Coinone) | `Private` |

### 🦀 amuredo-OMS-v2 — deep dive

순수 Rust 멀티 거래소 OMS. 실시간 데이터 수집부터 주문 실행까지 한 시스템으로 수직 통합했습니다.
**2026년 102개 커밋**에 걸쳐 직접 설계·구현한 작업:

**Engine & Pipeline**
- Julia + Rust DLL 하이브리드 → **순수 Rust 마이그레이션** (FFI 경계·GC 압박 제거)
- `Feeder → Matching → Feature Store → Pricing → OMS` 5-stage 파이프라인 설계
- zero-alloc 주문 상태머신(~50 전이), `DoubleBuffer` lock-free read
- **SimExchange**(Phase 5) — 실거래 전 검증용 시뮬레이션 거래소

**Multi-exchange Data Infra**
- 11개 거래소 WS/REST 통합 + 거래소별 인증(`HS256/512 JWT`, `HMAC-SHA256/512`)
- Binance 선물 **577종목** data-save + watchdog(freeze 감지·PID dedup·WS timeout·stale feed)
- 9개 거래소 데이터 품질 버그 수정, parquet 품질 검증, `batch_capacity` 튜닝
- BinanceFeed `BTreeMap` depth book → **CPU −27%**

**Latency / Parsing**
- **tick-to-trade p50 4.23µs · 218K tps** (117 온라인 피처 연산 포함)
- 메시지 크기 기반 JSON 파싱 라우팅(serde 소형 / `simd-json` depth) 8개 거래소 롤아웃
- wire-to-order · multi-feeder · parse-decompose 벤치마크로 파싱 경로 최적화
- `PARSING_LATENCY_SPEC` — 파이프라인 레이턴시 명세 문서화

**ML Market Making (SOL / BTC)**
- SOL MM: Julia 모델(v3m_17/19/34), walk-forward 스윕(D×K×τ×fee), **sim↔forward parity 감사**
- **97-feature 스키마** + PricingSession 모델 로더, FeatureStore→inference end-to-end
- offline/online 피처 parity (`LookbackLog`, `OfiNet`, vol_60s 등)
- BTC fair-value: 모델 export → Rust loader → maker 전략 배포 / online Ridge · DOGE OLS · Ladder MR

**Execution Safety & Ops**
- missed fill 감지, WS 버퍼 만료 → **REST 검증 폴백**, stale CancelInFlight 정리
- graceful flatten(체결 대기 후 종료), dashboard Stop/Shutdown 제어 API
- 실시간 forward-test 대시보드, SignalEngine 게이트웨이 통합

**Quality & Docs**
- **4-pass 코드베이스 감사** — 22건 수정, 거래소 9곳 데이터 정합성 확보
- 계층형 `AGENTS.md` 문서화, MODEL_REGISTRY research→production 5-stage 체크리스트
- Strategy Playbook — 2-layer 트레이딩 시스템 가이드(15개 전략 예시)

## Engineering & Troubleshooting

`amuredo-OMS`(Julia+Rust)와 `amuredo-OMS-v2`(순수 Rust)를 만들며 부딪힌 실전 엔지니어링 고민과 해결의 기록 — 데이터 수집부터 실거래 정합성까지.
*(알파·시그널 내용은 제외, 시스템 설계와 트러블슈팅만)*

**01 · 데이터 수집** — `data-save` parquet archival
- 🔴 **문제** — 멀티 거래소 원시 틱을 손실 없이 보관하면서, *수집 부하 자체가 데이터를 오염시키지 않게* 하려면?
- 🟢 **해결** — **3,349 심볼 × 12 거래소**를 시간단위 Parquet 파티션(`<거래소>/<심볼>/<YYYYMMDD_HH>`)으로 아카이빙, watchdog 싱글톤으로 단일 인스턴스 강제. 60k msg/sec 고부하에서 OS NIC batching이 **RX→consumer lag p99를 1,140ms**까지 밀어 1Hz 스냅샷이 stale해지는 "silent contamination"을 측정으로 발견 → 프로세스당 **≤50k msg/sec ≈ 800심볼** 안전선으로 분할.

**02 · 피더 & 피처 스토어** — feeder · FeatureStore
- 🔴 **문제** — 초당 수만 메시지를 받아 *수십~수백 피처를 GC·락 없이* 실시간 계산하려면?
- 🟢 **해결** — 피더(WS producer) → MatchingEngine → Channel 경쟁 소비. 오브젝트 풀(`get_from_pool!`/`release_to_pool!`)·`StaticRingBuffer`로 **heap 할당 0**. FeatureStore는 3계층(Online/Offline/Cross), `ColumnStore` row-major f64 **zero-copy**, EMA 윈도우(갭 시 0 감쇠), **HeartBeat**가 1초 끊긴 피드 감지. → **online 99 features**(Brief 22 · Tick 21 · OrderFlow 56), FeatureStoreSession×4·FeedSession×4 병렬.

**03 · 모델 레이어** — PricingSession · DoubleBuffer
- 🔴 **문제** — 한 전략이 *수십~99개 피처를 읽고 여러 모델을 µs 단위로 추론*해야 한다. 전략이 피처를 직접 계산하면 sim↔live 정합성이 깨진다.
- 🟢 **해결** — PricingSession이 `DoubleBuffer`(dirty-index만 복사, lock-free)로 피처를 공급. 전략은 피처 계산 **금지** — `ctx.feature()`·`ctx.model()`·`ctx.feature_for(uid,name)` 읽기 전용 API만. 한 전략에 **여러 모델**(`HashMap<String,Model>`): RidgeOLS(static ~1µs) + OnlineRidge(매초 refit `β=(X'X+λI)⁻¹X'y`, rolling IC). → 실측 **5모델 feed→order p50 5.8µs · 10모델 7–11µs**.

**04 · 주문 제출** — order channel · state machine
- 🔴 **문제** — 전략 결정 → 거래소 REST까지, *핫패스에서 할당 없이* 주문 수명을 안전하게 관리하려면?
- 🟢 **해결** — 주문은 order Channel(Strategy→OMS)로 흘러 REST 워커가 제출. **상태머신**(`PlaceCreated→PlaceInFlight→Placed→Partial/Filled`, `CancelInFlight→Canceled`, `MaybeMissed`) — 정의되지 않은 전이는 identity로 **중복 이벤트를 흡수**. local↔exchange ID 양방향 매핑, **zero-alloc 오브젝트 풀**(v1 사전할당 50만 개).

**05 · 주문 경합** — contention · validation
- 🔴 **문제** — 취소가 *체결과 동시에* 날아오거나, 아직 ack 안 된 주문을 취소하거나, 같은 가격에 두 번 주문하면?
- 🟢 **해결** — 배치 전 **8가지 검증**(`validation.rs`): cancel-while-canceling, **SMP(자가체결 방지)**, duplicate-price, cancel-not-live, min qty/notional, NaN guard. `canceling_local_id_set`·`CancelInFlight`로 진행 중 취소를 추적하고, **stale-cancel sweep**가 30s+ 멈춘 취소를 강제 종료해 지갑 예약금 잠김을 해제. throttle·cancel-replace 케이던스(250ms·1Hz·10Hz).

**06 · 웹소켓 유저스트림** — out-of-order · gap · dedup
- 🔴 **문제** — 거래소 WS가 *체결을 ACK보다 먼저* 보내거나, 이벤트를 빠뜨리거나(gap), 같은 체결을 두 번 보내면?
- 🟢 **해결** —
  - **순서 역전** — `pending_ws_buffer`(64)가 early-fill을 버퍼링했다가 REST 매핑이 생기면 순서대로 replay
  - **누락** — `MissedFillDetector`가 체결틱이 내 호가를 관통하면 grace **2000ms** 대기 후 REST로 실체 확인
  - **끊김** — listen-key `keep_alive_loop` + 2–5s 백오프 auto-reconnect
  - **중복** — `processed_trade_id_set` trade_id dedup + 상태머신 중복 흡수

**07 · 백테스트 → 포워드 → 실거래 정합성** ⭐ — backtest · sim · live parity
- 🔴 **문제** — smoked 백테스트에서 좋던 전략이 *가상거래소 포워드 → 실거래*로 갈수록 무너진다. 어디서 새는지 어떻게 잡나?
- 🟢 **해결** — 3단계가 **같은 전략 바이너리**를 실행(backtest=MockExchange / forward=SimExchange 라이브 피드 / live). 시간 주입(`ctx.now_ms()`)으로 결정론 보장, fill 모델 사다리 EndOfQueue→QueueBased. 정합성은 **same-window 규칙** + yhat 분포 parity(`σ ratio∈[0.85,1.15]`, same-second `ρ≥0.85`) + `feat_hash` byte 일치로 검증.
- 🟣 **결과** — Rust↔Julia 예측 **Pearson 1.000000**(max diff 7e-9) 달성. 백테스트 +18.8bp인데 같은 구간 실거래 −29¢(~5bp 낙관 갭, 큐 포지션 미모델링)를 정직하게 기록 → "Sim PnL 숫자 자체는 믿지 말고 same-window로만 비교", 배포 전 **8단계 체크리스트** 통과 규약.

## Data Analysis & Quant Research

시스템 구축에서 끝내지 않고, 실제 데이터로 시그널을 검증하고 전략을 **forward test**까지 돌립니다.

**Market Microstructure**
- 오더북 **큐 마이크로구조** 리서치 + 분석 툴링 (빗썸)

**ML / 통계 분석**
- BTC·SOL **fair-value 모델링** — 피처 엔지니어링 + walk-forward 검증
- 팩터 분석 `IC · IR · hit ratio`, 뉴스 sentiment scoring
- sim↔forward **parity 감사**, fee sweep, EV table, calibration

**Forward Test (실거래 검증)**
- **BTC 낙주매매** — 급락 후 반등 dip-buy 전략
- **WLD** pair-reversion 전략
- **국내 거래소 MM** (빗썸 등) 마켓메이킹
- SOL · DOGE 모델 기반 MM, 실시간 forward-test 대시보드로 sim↔live 추적

## Archive

예전에 적극적으로 파고든 AI/ML · HFT 리서치 프로젝트들 — 지금의 작업으로 이어진 토대.

[ML-HFT](https://github.com/donghui-0126/ML-HFT) · [deepOBs](https://github.com/donghui-0126/deepOBs) · [lob-world-models](https://github.com/donghui-0126/lob-world-models) · [lob-deep-learning](https://github.com/donghui-0126/lob-deep-learning) · [online_estimation](https://github.com/donghui-0126/online_estimation) · [JaneStreetKaggle](https://github.com/donghui-0126/JaneStreetKaggle) (Kaggle Bronze 🥉) · [ML for Factor Investing](https://github.com/donghui-0126/Machine-Learning-for-Factor-Investing) · [crypto-scalping-RL](https://github.com/donghui-0126/crypto-scalping-RL-Agent)

## Awards

| Year | Competition | Result |
|------|------------|--------|
| 2025 | Jane Street - Real-Time Market Data Forecasting (Kaggle) | Bronze Medal |
| 2024 | BDA X ASCEND - Bitcoin Volatility Prediction | 우수상 |
| 2023 | WorldQuant Alphaton Korea | 3rd Place |
| 2023 | FSI Data Challenge - EV Customer Prediction | 우수상 |

## Education

- **경희대학교 산업경영공학과** (Kyung Hee University, Industrial & Management Systems Engineering) — 학부 재학 중 · 2027 졸업예정

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
