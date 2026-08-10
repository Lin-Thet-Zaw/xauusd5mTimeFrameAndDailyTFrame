# MM FLIP Auto Trade AI (MT4 EA)

An advanced algorithmic Expert Advisor (EA) designed for MetaTrader 4, featuring multi-timeframe trend filtering, smart post-news volatility checks, live dashboard telemetry, and robust risk management.

---

## 📊 Strategy & Timeframes Overview
- **H1 (`PERIOD_H1`):** Macro Trend Filter (EMA & ADX Trend Strength)
- **M15 (`PERIOD_M15`):** Trend Confirmation (RSI 50 Level Filter)
- **M5 (`PERIOD_M5`):** Execution, Pending Order Buffer Entry, & Trade Management

---

## 📈 Backtesting Results
- **Symbol:** XAUUSD-VIP (Gold vs USD)
- **Period:** 5 Minutes (M5) | 2026.08.03 - 2026.08.07
- **Model:** Every tick (90.00% quality)
- **Initial Deposit:** 10.00
- **Total Net Profit:** 3976.02
- **Profit Factor:** 1.58
- **Maximal Drawdown:** 279.98 (6.99%)
- **Total Trades:** 2231 (69.57% Win Rate)

### Key Parameters Used in Test
- `RiskPercent = 1.0`
- `UseADX_TrendFilter = true` (Level: 25)
- `TrendMA_Period = 200` | `Trend_EntryMA = 20`
- `ServerProfitPips = 300` | `ServerLossPips = 150`
- `UseTrailingStop = true` | `UseBreakEven = true`

---

## 📥 Installation Guide

Follow these simple steps to install the EA and its required indicators on your MetaTrader 4 terminal:

### Step 1: Prepare Your Files
1. Download or clone this repository to your local computer.
2. Locate your compiled files:
   - **Expert Advisor (`.ex4` or `.mq4`):** `MM_FLIP_AI.ex4`
   - **Required Indicator:** `FFCal2.ex4` (Required for the Real News Filter)

### Step 2: Open MetaTrader 4 Data Folder
1. Open your MT4 terminal.
2. On the top monitor/menu, click on **File** > **Open Data Folder**.
3. A Windows Explorer window will pop up showing your MT4 root data directory. Navigate to `MQL4/`.

### Step 3: Place Files into Correct Folders
- **For the Expert Advisor:**
  - Open the `Experts` folder inside `MQL4/`.
  - Paste your `MM_FLIP_AI.ex4` (or source file) here.
- **For the Custom Indicator:**
  - Open the `Indicators` folder inside `MQL4/`.
  - Paste the `FFCal2.ex4` file here (Note: The News Filter relies on this indicator to fetch calendar events).

### Step 4: Refresh MT4 Terminal
1. Go back to your MetaTrader 4 platform.
2. Look at the **Navigator** panel on the left side.
3. Right-click anywhere inside the **Expert Advisors** or **Indicators** list and select **Refresh** (or restart your MT4 terminal).

### Step 5: Attach EA to Chart
1. Open a chart window for your target asset (e.g., **XAUUSD**, M5 timeframe recommended).
2. Drag and drop `MM_FLIP_AI` from the Navigator panel onto the chart.
3. In the popup window settings:
   - Go to the **Common** tab and check **"Allow live trading"** and **"Allow DLL imports"** (if required).
   - Go to the **Inputs** tab to configure your License Key, Terminal ID, Risk %, and other parameters.
4. Click **OK**. The Live Dashboard should now appear cleanly on the top-left corner of your chart.

---

## ⚙️ Recommended Settings
- **Account Type:** ECN / Raw Spread (Supports both Standard and Cent accounts)
- **Leverage:** 1:500 recommended for risk management calculation.
- **Default Parameters:** Optimized for standard market conditions on M5 execution timeframe.

---

## ⚠️ Important Risk Warning & Disclaimer
- **Not Financial Advice:** This software and its documentation are provided for **educational and informational purposes only**. They do not constitute financial, investment, or trading advice.
- **Use At Your Own Risk:** Trading foreign exchange, CFDs, and cryptocurrencies on margin carries a high level of risk and may not be suitable for all investors. Past performance (including backtest results) does not guarantee future results.
- **Be Smart, Not Greedy:** Never risk capital you cannot afford to lose. Always test strategies thoroughly on a Demo account under live market conditions before deploying real funds.




# FibRetracementEA (Gold Optimized Scalper Engine) 🚀

An institutional-grade, multi-threaded Fibonacci 0.618 Retracement Expert Advisor tailored explicitly for trading Gold (**XAUUSD**) on the MetaTrader 5 (MQL5) platform. 

This EA utilizes advanced structural micro-fractal analysis to isolate major market swings, calculates highly sensitive Fibonacci retracement points, and executes trades based on exact candle momentum confirmation variables.

---

## 📈 Performance Highlights (H1 Backtest Verified)
During strict long-term automated execution testing matching **100% Real Ticks** on historical Gold data, the optimized configuration produced world-class stability metrics:

*   **Profit Factor:** `2.30` 🔥
*   **Sharpe Ratio:** `9.60` 💎 (Exceptional systemic stability)
*   **Recovery Factor:** `4.45`
*   **Max Consecutive Losses:** Restricted to a maximum of `3` trades.
*   **Total Net Profit Growth:** Generated **+$2,461.93** on a baseline standard $1,000 deployment account.

---

## 🛠️ Key Architectural Features

*   **Dual In-Memory Swing Memory Slots:** Tracks up to 2 independent nesting market swings concurrently. This prevents the EA from losing structural data blocks during highly volatile multi-directional Gold market sweeps.
*   **Precision Anti-Doji Filter:** Computes absolute body-to-range ratios ($|Close - Open| \div |High - Low|$) to block market-maker wick-manipulation entries and low-liquidity market phases.
*   **Dynamic Points-Based Trade Management:** Protects live floating equity instantly via point-based Breakeven systems and automated Trailing Stop parameters.
*   **Asynchronous Trade Ticket Assignment:** Bypasses standard server execution lag by processing structural order ticket tracking via `Trade.ResultOrder()` directly, guaranteeing active orders are never unmanaged.

---

## ⚙️ Fully Optimized Input Parameters

To replicate the record-shattering `Profit Factor 2.30` performance, configure your MT5 Expert parameters exactly as detailed below:

### 1. Swing Detection

| Parameter | Value | Description |
| :--- | :--- | :--- |
| `InpFractalBars` | `5` | Fractal configuration bar window matching market structures. |
| `InpMinSwingATR` | `2.0` | Volatility filter multiplier determining valid structural swings. |
| `InpMaxRetraceBars` | `10` | Maximum structural bars allowed before setup momentum is flagged dead. |
| `InpATRPeriod` | `14` | Average True Range analysis horizon. |

### 2. Entry Confirmation

| Parameter | Value | Description |
| :--- | :--- | :--- |
| `InpMaxConfirmBars` | `2` | Maximum immediate bars allowed to close after a 0.618 level sweep. |
| `InpMinBodyPct` | `25.0` | Minimum candle body closure threshold to validate structural reversal. |

### 3. Stop Loss & Take Profit

| Parameter | Value | Description |
| :--- | :--- | :--- |
| `InpSLMode` | `2` | Advanced structured target alignment parameters. |
| `InpSL_ATR_Mult` | `1.8` | Adaptive stop loss scaling metric. |
| `InpSLPct` | `0.8` | Percentage protection gap protecting account equity from raw spikes. |
| `InpTPPct` | `1.6` | Fixed risk reward percentage distribution. |
| `InpRiskReward` | `2.0` | Target mathematical risk-to-reward ratio profile. |

### 4. Risk & Trade Management

| Parameter | Value | Description |
| :--- | :--- | :--- |
| `InpLotSize` | `0.05` | Recommended lot configuration for a standard $1,000 capital baseline. |
| `InpBreakEven` | `true` | Engages trailing break-even safety parameters. |
| `InpBEPct` | `0.3` | Minimum percentage move required to roll target stops to baseline entries. |
| `InpCloseOnCandle` | `false` | Prevents intra-candle noise from generating premature structural exits. |
| `InpTrailingStop` | `true` | Engages automatic trend lock management protocols. |
| `InpTrailingStart`| `0.5` | Holds stops open during early execution to capture large trends. |
| `InpTrailingStep` | `0.3` | Steps trailing boundaries smoothly behind structural market shifts. |

---

## 🚀 Deployment & Installation Guidance

1. Download the complete file asset directly as a `.mq5` document format.
2. Open MetaTrader 5, choose `File` $\rightarrow$ `Open Data Folder`.
3. Move the compiled source code document into `MQL5` $\rightarrow$ `Experts`.
4. Press `F4` to load MetaEditor, search for your file, and click **`Compile`**.
5. Return to the terminal workspace, navigate to the Navigator Panel, right-click `Experts`, and select `Refresh`.
6. Drag **`FibRetracementEA`** onto any **XAUUSD (Gold)** chart window, select the **H1 (1-Hour)** timeframe, and toggle the **Algo Trading** security switch on your terminal toolbar.

> ⚠️ **Account Scale Warning:** This automated profile is fully validated for $1,000 balances utilizing fixed 0.05 lot parameters. If deploying on micro accounts scaled to $200 or $300 capital allocations, manually scale your volume input settings directly down to **`0.01`** lots to prevent high initial drawdowns.

---

## 📄 License
This repository is open-source software provided under the [MIT License](LICENSE).



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




# FOT Scalping Expert Advisor

An institutional-grade, high-frequency algorithmic execution system built natively for **MetaTrader 5 (MQL5)**. This automated software application features state-of-the-art dynamic position sizing algorithms, advanced macro-news protection modules, and a cloud-based authentication system optimized for standard and cent portfolio setups.

---

## 🚀 Key System Features

* **100% Real Ticks Verified**: Fully backtested and performance-optimized under `Every Tick Based on Real Ticks` premium broker data feeds.
* **Automated Web News Filter**: Integrated live parsing framework that hooks directly into the global economic calendar feed via FairEconomy JSON endpoints. Dynamically pauses new market order execution during High-Impact news intervals to prevent drawdown spikes.
* **Cloud License Authentication**: Secure cloud-linked license validation module powered by an encrypted Google Apps Script architecture to verify license keys and account states dynamically.
* **Multi-Asset Digit Stabilization Engine**: Tailor-made mathematically to run flawlessly across changing broker quote decimal spaces (including 2-digit, 3-digit, and 5-digit feeds) such as Gold (**XAUUSD / XAUAUD**) and JPY cross-asset structures.
* **Advanced Dual Capital Allocation Engine**: Fully responsive and optimized to calculate sizing accurately on both Standard and Cent terminal accounts.

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

## ⚙️ Core Inputs Configuration Guide

### 1. Lot Management System
* `InpLotMode`: Toggle switch between `MODE_FIXED_LOT` or `MODE_RISK_PERCENT`.
* `InpFixedLot`: Default base fixed contract volume (Optimized at `0.02` for conservative handling).
* `InpRiskPercent`: Target active account equity risk liability threshold allocation per individual position sequence (Optimized at `2.5%`).

### 2. Economic Web News Filter Settings
* `InpUseWebNewsFilter`: Enables or disables the live JSON economic calendar parsing gateway (`true` / `false`).
* `InpMinsBeforeNews`: Restrictive cool-down window length prior to a matching calendar event (Recommended: `30` minutes).
* `InpMinsAfterNews`: Restrictive quiet window padding length following a matching calendar event (Recommended: `30` minutes).
* `InpNewsURL`: The structural endpoint URL for downloading weekly updates (`https://faireconomy.media`).
* `InpNewsCheckMinutes`: Interval pacing configuration for verifying database updates (Recommended: `5` minutes).

### 3. Cloud License System
---

## 📥 Live Installation & WebRequest Setup Guidelines

To enable the automated News Filter and Cloud Authentication systems, the terminal requires explicit permission to communicate with external data streams.

1. Open your MT5 Terminal and navigate to the top main menu: **Tools -> Options**.
2. Click on the **Expert Advisors** tab inside the Options window panel.
3. Check the box labeled **"Allow WebRequest for listed URL:"**.
4. Double-click the **`<add new URL here>`** field and add the following two mandatory URLs exactly as shown:
   * `https://faireconomy.media` (For downloading live macroeconomic calendar news)
   * `https://script.google.com` (For processing the remote cloud server license keys verification)
   * `https://script.googleusercontent.com` (For processing the remote cloud server license keys verification)
5. Click **OK** to save and apply your terminal changes.
6. Transfer your `FOT_Scalping.ex5` file into the terminal directories path: `/MQL5/Experts/`.
7. Open MetaEditor (**F4**), load the code, and compile it (**F7**) ensuring there are zero errors.
8. Drag the EA onto an **M1 Chart** of **XAUAUD** or **XAUUSD**, input your authorized `InpLicenseKey`, and make sure **Algo Trading** is enabled in the platform ribbon.

---
## ⚖️ Risk and Liability Disclaimer
Speculative margin operations on leveraged markets involve notable financial exposure thresholds. Historical backtesting matrices are synthetic data indices and do not guarantee live market equity replication. Deploy entirely at your own discretion.

- **Telegram Support:** `@lernthert`

---
*Disclaimer: Forex and Gold trading carry high structural risks. Always test on a demo or cent account before running on a live standard account.*

