# Trust Me Bro Strategy

A Pine Script v6 trading strategy built on an **RSI 50 state machine**: it waits for RSI to cross the 50 level, then a **pullback/retest** of that level, then **hidden divergence** on RSI — and only enters when the setup is confirmed by a stack of toggleable confluence filters (**EMA touch**, **Fibonacci retracement zone**, and **Ichimoku cloud**).

Stop Loss is placed at the last swing point, and Take Profit is a configurable Risk/Reward multiple of the risk.

> 🔗 **[Live on TradingView →](https://www.tradingview.com/script/JYIf5J93-Trust-Me-Bro-Strategy-v1/)**

## ✨ Features

* **RSI state machine** with four phases:
  * **State 0** — waiting for RSI to cross `50` (up → long bias, down → short bias).
  * **State 1** — RSI must move away from the trigger by a configurable **buffer**, then **retest** it.
  * **State 2 → 3** — a **hidden divergence** confirms the setup (bullish: higher low in price + lower low in RSI; bearish: lower high in price + higher high in RSI).
  * Setups **expire** after a configurable number of bars (`30` by default).
* **Confluence filters**, each individually toggleable:
  * **EMA filter** — price must touch the `20` EMA while the setup is armed.
  * **Fibonacci filter** — price must retrace into the `0.5 – 0.618` zone of the last swing leg.
  * **Ichimoku filter** — cloud touch mode, or price strictly above (long) / below (short) the cloud.
* **Long / Short** can be enabled or disabled independently.
* **Risk management**:
  * Stop Loss at the last swing low (long) / swing high (short).
  * Take Profit = risk × configurable **Risk/Reward** (default `2`).
* **Visuals**: EMA line, divergence lines, the Fib leg and retracement bands, the full Ichimoku cloud, and a background color showing the current state-machine phase.
* Includes an RSI pane plotted under the main chart.

## ⚙️ Inputs

| Group | Input | Description | Default |
|---|---|---|---|
| Filters | Use EMA / Fib / Ichimoku filter | Toggle each confluence filter | `true` |
| EMA | EMA Length | Trend EMA length | `20` |
| RSI | RSI Length | RSI period | `14` |
| RSI | RSI Trigger Level | Level to cross and retest | `50.0` |
| RSI | RSI retest buffer | Required distance before a valid retest | `5.0` |
| RSI | Setup expiry | Bars before an unfinished setup is dropped | `30` |
| Pivots | Pivot left / right bars | Swing point detection for divergence, Fib leg, and Stop Loss | `5` / `5` |
| fibo | Fib level 1 / 2 | Retracement zone boundaries | `0.5` / `0.618` |
| — | Reward:Risk | Take Profit as a multiple of risk | `2.0` |
| — | Trade Long / Trade Short | Enable each direction | `true` |
| Display | Show EMA / Divergence / Fib Leg / Fib Bands / Ichimoku | Toggle chart drawings | varies |

## 🚀 How to Use

1. Open [TradingView](https://tradingview.com) and go to **Pine Editor**.
2. Paste the contents of [`trust-me-bro-strategy.pine`](./trust-me-bro-strategy.pine).
3. Click **Add to chart** and pick your symbol/timeframe.
4. Watch the background color to follow the setup phase, and configure the filters in the strategy settings.

## ⚠️ Disclaimer

This strategy is written for **educational purposes** as part of my Pine Script learning journey. It is **not financial advice** — always backtest thoroughly before using any strategy with real money.
