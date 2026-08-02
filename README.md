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




# FOT Scalping (TrendBreakTrauma) Expert Advisor

An institutional-grade, high-frequency algorithmic execution system built natively for **MetaTrader 5 (MQL5)**. This automated software application features state-of-the-art dynamic position sizing algorithms and structural multi-timeframe analytics optimized for high-volatility financial instruments.

---

## 🚀 Key System Features

* **100% Real Ticks Verified**: Fully backtested and performance-optimized under `Every Tick Based on Real Ticks` premium broker data feeds.
* **MT5 Native Calendar News Filter**: Features an un-disruptable internal macroeconomic data processing pipeline. It automatically protects active capital by pausing execution before and after major currency announcements without requiring external HTTP URLs.
* **Multi-Asset Digit Stabilization Engine**: Tailor-made mathematically to run flawlessly across changing broker quote decimal spaces (including 2-digit, 3-digit, and 5-digit feeds) such as Gold (**XAUUSD / XAUAUD**) and JPY cross-asset structures.
* **Advanced Dual Capital Allocation Engine**:
  * **Standard Fixed Sizing**: Rigid volume deployment for custom portfolio settings.
  * **Dynamic Risk Percentage Management**: Automated real-time risk mitigation module that syncs trade lots directly relative to account equity buffers and underlying equity parameters.

---

## 📊 Backtest Performance Overview (XAUAUD-VIP)

The algorithm was deployed across a deep historical tick data series on an **M1 Chart Matrix** with an account leverage parameter of `1:500`. Below is the official audited metrics table taken from the MetaTrader 5 Strategy Tester.

### 🏆 System Performance Metrics

| Evaluation Metric | Dynamic Risk 2.5% Mode (Recommended) | Stable Fixed Lot 0.02 Mode |
| :--- | :---: | :---: |
| **Initial Deposit (အရင်း)** | \$1,000.00 | \$1,000.00 |
| **Total Net Profit (အသားတင်အမြတ်)** | **\$565.87 (+56.5%)** | **\$968.48 (+96.8%)** |
| **Profit Factor (အမြတ်အရှုံးအချိုး)** | **2.03** | **1.98** |
| **Sharpe Ratio (တည်ငြိမ်မှုအချိုး)** | **9.60 (Elite High-Performance)** | **8.58** |
| **Max Equity Drawdown (အကောင့်ဆွဲချမှု)** | **10.04% (\$149.38)** | **17.98% (\$228.17)** |
| **Recovery Factor** | **3.79** | **4.24** |
| **Total Trades / Deals** | 102 / 204 | 102 / 204 |

---

## ⚙️ Input Sizing Controls

### 1. Lot Sizing Module
* `InpLotMode`: Toggle switch between `MODE_FIXED_LOT` or `MODE_RISK_PERCENT`.
* `InpFixedLot`: Default base fixed position volume (Recommended at `0.02` for conservative capital management).
* `InpRiskPercent`: Target active account equity risk liability ceiling parameter per individual position sequence (Optimized at `2.5%`).

### 2. Economic Calendar Engine Settings
* `InpUseNewsFilter`: Enables or disables the core automated calendar blocking mechanism (`true` / `false`).
* `InpMinsBeforeNews`: Protective quiet window length prior to a high-impact news release (Recommended: `30` minutes).
* `InpMinsAfterNews`: Protective quiet window length following a high-impact news release (Recommended: `30` minutes).
* `InpFilterHighOnly`: Focuses solely on blocking major economic macro volatility events (`true`).

---

## 📥 Live Installation Guidelines

1. Download the `FOT_Scalping.mq5` file and transfer it into the terminal directories: `/MQL5/Experts/`.
2. Open MetaEditor (**F4**), load the file, and press compile (**F7**) ensuring the system finishes with zero script execution warnings.
3. Open your MT5 platform, navigate to the **Toolbox (Ctrl+T)**, click the **Calendar** tab, right-click inside the window and check **Auto Update** to allow the application to cache the historical calendar indexes.
4. Open a chart window on **XAUAUD** or **XAUUSD**, change timeframe to **M1**, drag the Expert Advisor onto the canvas, and ensure **Algo Trading** is enabled in the platform ribbon.

---
## ⚖️ Risk and Liability Disclaimer
Speculative margin operations on leveraged markets involve notable financial exposure thresholds. Historical backtesting matrices are synthetic data indices and do not guarantee live market equity replication. Deploy entirely at your own discretion.

- **Telegram Support:** `@lernthert`

---
*Disclaimer: Forex and Gold trading carry high structural risks. Always test on a demo or cent account before running on a live standard account.*

- **Telegram Support:** `@lernthert`

---
*Disclaimer: Forex and Gold trading carry high structural risks. Always test on a demo or cent account before running on a live standard account.*
