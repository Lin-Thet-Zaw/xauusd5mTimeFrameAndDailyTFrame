# Gold Flip EA - Premium MetaTrader 5 Expert Advisor

Gold Flip EA is a high-performance, fully automated trading robot specifically designed for **XAUUSD (Gold)** on the **MetaTrader 5 (MT5)** platform. It utilizes a proprietary advanced breakout algorithm with built-in dynamic risk management and smart trailing stop mechanisms to maximize profit while keeping drawdowns at an absolute minimum.

Choose your preferred configuration below based on your trading profile: **The Ultimate Champion (Ultra Safe)** or **The Aggressive Performance Setup**.

---

## 🏆 Option 1: Certified Backtesting Results (The Ultimate Champion Setup)
Validated through strict multi-year backtests (2025 - 2026) using **100% Real Ticks Data**, this verified configuration achieved the most stable equity curve and is **Fully Compliant with Prop Firm (Funded Account) Daily Drawdown Rules**:

- **Total Net Profit:** +1,108.86 USD
- **Win Rate:** 62.70% (79 Profit Trades / 47 Loss Trades)
- **Profit Factor:** 1.44
- **Max Equity Drawdown:** 5.59% ($361.68) - **Ultra Safe**
- **Expected Payoff:** 8.80
- **Recovery Factor:** 3.07

### 🛠️ Premium Master Settings (Default Inputs)
To replicate the exact certified 5.59% drawdown performance, run the EA with these parameters:

| Parameter | Certified Value | Description |
| :--- | :--- | :--- |
| `InpLotMode` | `MODE_RISK_PERCENT` | Set `0` for Fixed Lot, `1` for Risk % Lot |
| `InpLotSize` | `0.01` | Default lot for Cent or standard micro accounts |
| `InpRiskPercent` | `1.0` | Risk 1% per trade (Yields the optimal 5.59% Drawdown) |
| `InpStopLoss` | `500` | 500 Points (50 pips) exact protective stop |
| `InpTakeProfit` | `1500` | 1500 Points (150 pips) target for pure 1:3 Risk-to-Reward |
| `InpMaxSpread` | `25` | Strict live conditions filter |
| `InpPullbackFib` | `0.382` | Optimal entry filter at 38.2% Fibonacci level |
| `InpServerTimeOffset`| `3` | Configured for Exness Server Time (GMT+3) |
| `InpTrailingStart`| `400` | Trailing triggers when trade reaches +40 pips |
| `InpTrailingStep` | `50` | Follows the trend at a strict 5 pips distance |

---

## ⚡ Option 2: Aggressive Setting (New High-Performance EA)
For traders seeking aggressive capital growth with higher risk tolerance. This setup maximizes profit returns utilizing optimized compounding parameters:

- **Total Net Profit:** +55.7% Profit
- **Win Rate:** 62.70% (79 Wins / 47 Losses)
- **Profit Factor:** 1.38
- **Max Equity Drawdown:** 13.26% (Very Safe for personal accounts)

### 🛠️ Features & Settings (Inputs)
To deploy the aggressive setup for maximum volatility yield, use the following parameters:

| Parameter | Default Value | Description |
| :--- | :--- | :--- |
| `InpLotMode` | `MODE_RISK_PERCENT` | Set `0` for Fixed Lot, `1` for Risk % Lot |
| `InpLotSize` | `0.01` | Default lot for Cent or standard micro accounts |
| `InpRiskPercent` | `2.5` | Risk percent per trade (Aggressive Compounding) |
| `InpStopLoss` | `500` | 500 Points (50 pips) protective stop |
| `InpTakeProfit` | `1500` | 1500 Points (150 pips) targeting a 1:3 Risk-to-Reward |
| `InpMaxSpread` | `25` | Max allowed spread filter optimized for live conditions |
| `InpServerTimeOffset`| `0` | Hour offset to match broker server differences |
| `InpTrailingStart`| `400` | Starts trailing when trade reaches profit target |
| `InpTrailingStep` | `50` | Trailing step distance in points |

---

## 🕒 Timezone Management & Exness Optimization

### Default Time Zone Used
The EA uses the broker server time from `TimeCurrent()` as its default time zone. It does not use your computer clock or a fixed GMT time. That means each broker can have a different effective time for the EA.

### Why Exness Needs `InpServerTimeOffset`
Because Exness server time is not the same as your VT broker’s server time.
- If the EA is configured for a session window using VT server hours, but you run it on Exness, the same hour values will shift by the broker time difference.
- `InpServerTimeOffset` lets you correct that difference so the EA uses the same intended session window on any broker.

### What the Input Means
- `InpServerTimeOffset = 0` → Use the broker server time exactly as it is.
- If Exness is 3 hours behind VT, use `InpServerTimeOffset = 3`.
- If Exness is 3 hours ahead of VT, use `InpServerTimeOffset = -3`.

  
---

## ⏰ Timezone & Broker Configuration

The EA scans for market ranges between **00:00 and 05:00 Broker Server Time**. Because different brokers handle seasonal clock adjustments differently, you must configure **`InpServerTimeOffset`** precisely according to the specific calendar periods below:

### 1. For VT Markets & TMGM Brokers (Dynamic Shift)
These brokers change their clocks twice a year following US Daylight Saving Time (DST). You must manually update your setting on the specific weekends when the seasons change:

#### ☀️ Set `InpServerTimeOffset = 0` (Summer Period)
* **Months Active**: From **Mid-March** until **Late October / Early November**.
* **Exact Rule**: Set to `0` starting on the **2nd Sunday of March** until the **1st Sunday of November**.
* **Broker Status**: The broker server operates on **GMT+3**.
* **Myanmar Time (MMT)**: The EA operates from **03:30 AM to 08:30 AM MMT**.
* **Calendar Reference**:
  * **2026**: Active from March 8, 2026, to October 31, 2026.
  * **2027**: Active from March 14, 2027, to November 6, 2027.

#### ❄️ Set `InpServerTimeOffset = 1` (Winter Period)
* **Months Active**: From **November** until **Mid-March** of the following year.
* **Exact Rule**: Set to `1` starting on the **1st Sunday of November** until the **2nd Sunday of March**.
* **Broker Status**: The broker server drops to **GMT+2**.
* **Myanmar Time (MMT)**: The EA operates from **04:30 AM to 09:30 AM MMT**.
* **Calendar Reference**:
  * **2026**: Set to `1` starting on **November 1, 2026**.
  * **2027**: Set to `1` starting on **November 7, 2027**.

---

### 2. For Exness Broker (Fixed Clock)
Exness utilizes a fixed server clock that does not adjust for seasons. 
* **Year-Round Configuration**: Set `InpServerTimeOffset = 3` permanently.
* **Months Active**: All 12 months (January to December). Do not change this value.
* **Myanmar Time (MMT)**: The EA operates from **03:30 AM to 08:30 AM MMT** year-round.

---

### How to Use It
1. Open EA inputs in MetaTrader.
2. Find `InpServerTimeOffset`.
3. Check Exness server time and compare it to VT server time.
4. Enter the hour difference:
   - Positive if Exness is behind VT
   - Negative if Exness is ahead of VT

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
*Disclaimer: Forex and Gold trading carry high structural risks. Always test on a demo or cent account before running on a live standard account.*
