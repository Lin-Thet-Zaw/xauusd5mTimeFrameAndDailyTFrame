# Uploaded New Hight Performance EA -> Gold Flip EA - Premium MetaTrader 5 Expert Advisor

Gold Flip EA is a high-performance, fully automated trading robot specifically designed for **XAUUSD (Gold)** on the **MetaTrader 5 (MT5)** platform. It utilizes a proprietary advanced breakout algorithm with built-in dynamic risk management and smart trailing stop mechanisms to maximize profit while keeping drawdowns low.

---

## 📊 Backtesting Results & Performance
Validated through strict multi-year backtests (2025 - 2026) using **100% Real Ticks Data**, the EA demonstrated exceptional market stability:
- **Total Net Profit:** +55.7% Profit
- **Win Rate:** 62.70% (79 Wins / 47 Losses)
- **Profit Factor:** 1.38
- **Max Equity Drawdown:** 13.26% (Very Safe)

---

## 🛠️ Features & Settings (Inputs)
For optimum stability, run the EA on **XAUUSD** using the **M5** or **M15** Timeframe with the following default parameters:

| Parameter | Default Value | Description |
| :--- | :--- | :--- |
| `InpLotMode` | `MODE_FIXED_LOT` | Set `0` for Fixed Lot, `1` for Risk % Lot |
| `InpLotSize` | `0.01` | Default lot for Cent or standard micro accounts |
| `InpRiskPercent` | `2.5` | Risk percent per trade (If Risk Mode is on) |
| `InpStopLoss` | `500` | 500 Points (50 pips) protective stop |
| `InpTakeProfit` | `1500` | 1500 Points (150 pips) targeting a 1:3 Risk-to-Reward |
| `InpMaxSpread` | `25` | Max allowed spread filter optimized for live conditions |
| `InpServerTimeOffset`| `0` | Hour offset to match broker server differences |
| `InpTrailingStart`| `400` | Starts trailing when trade reaches profit target |
| `InpTrailingStep` | `50` | Trailing step distance in points |

---

## 🕒 Timezone Management Guide

### Default time zone used
The EA uses the broker server time from `TimeCurrent()` as its default time zone. It does not use your computer clock or a fixed GMT time. That means each broker can have a different effective time for the EA.

### Why Exness needs `InpServerTimeOffset`
Because Exness server time is not the same as your VT broker’s server time.
- If the EA is configured for a session window using VT server hours, but you run it on Exness, the same hour values will shift by the broker time difference.
- `InpServerTimeOffset` lets you correct that difference so the EA uses the same intended session window on any broker.

### What the input means
- `InpServerTimeOffset = 0` → use the broker server time exactly as it is.
- If Exness is 3 hours behind VT, use `InpServerTimeOffset = 3`.
- If Exness is 3 hours ahead of VT, use `InpServerTimeOffset = -3`.

### How to use it
1. Open EA inputs in MetaTrader.
2. Find `InpServerTimeOffset`.
3. Check Exness server time and compare it to VT server time.
4. Enter the hour difference:
   - positive if Exness is behind VT
   - negative if Exness is ahead of VT

### Example
- VT server time = `6:37`
- Exness server time = `3:37`
- Exness is 3 hours behind VT
- Set `InpServerTimeOffset = 3`

Then the EA will treat Exness `3:37` as if it were `6:37` when applying `InpStartHour` and `InpEndHour`.

---

## 🚀 Installation & Usage
1. Download the `Gold_Flip_EA.mq5` file from this repository.
2. Open MetaTrader 5, go to `File -> Open Data Folder`.
3. Navigate to `MQL5 -> Experts` and paste the file inside.
4. Restart MT5 or refresh the Navigator window.
5. Drag the EA onto a **XAUUSD** Chart.
6. Ensure **"Allow Algo Trading"** is enabled in both MT5 and the EA settings.

---

## 👤 Developer & Support
- **Developer:** Lin Thet Zaw
- **Facebook:** [Linthetzaw0](https://facebook.com)
- **Telegram Support:** `@lernthert`

---
*Disclaimer: Forex and Gold trading carry high risks. Always test on a demo or cent account before running on a live standard account.*
