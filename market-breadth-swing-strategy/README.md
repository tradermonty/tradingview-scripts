# Market Breadth Swing Strategy

**🇯🇵 [日本語版はこちら](#ストラテジー概要日本語版)**

![Breadth-Driven Swing Strategy](Breadth-Driven%20Swing%20Strategy.png)

## What it does

This script trades the S&P 500 purely on market breadth extremes:
- **Data source**: INDEX:S5TH = % of S&P 500 stocks above their own 200-day SMA (range 0–100).
- **Buy** when breadth is washed-out.
- **Sell** when breadth is overheated.

It is **long-only** by design; shorting and ATR trailing stops have been removed to keep the logic minimal and transparent.

**📊 [View on TradingView](https://www.tradingview.com/script/dBKk4Awg-Breadth-Driven-Swing-Strategy/)**

---

## Signals in plain English

### 1. Long entry
**A.** A 200-EMA trough in breadth is printed and the trough value is ≤ 40 %.

**or**

**B.** A 5-EMA trough appears, its prominence passes the user threshold, and the lowest breadth reading in the last 20 bars is ≤ 20 %.  
(Toggle this secondary trigger on/off with **"Enter also on 5-EMA trough"**.)

### 2. Exit (close long)
First 200-EMA peak whose breadth value is ≥ 70 %.

### 3. Risk control
A fixed stop-loss (% of entry price, default 8 %) is attached to every long trade.

---

## Key parameters (defaults shown)

| Parameter | Default Value | Description |
|-----------|---------------|-------------|
| **Long EMA length** | 200 | Period for long-term trend |
| **Short EMA length** | 5 | Period for short-term trend |
| **Peak prominence** | 0.5 pct-pts | Threshold for peak detection |
| **Trough prominence** | 3 pct-pts | Threshold for trough detection |
| **Peak level** | 70 % | Minimum breadth value for exit |
| **Trough level** | 40 % | Maximum breadth value for 200-EMA entry |
| **5-EMA trough level** | 20 % | Maximum breadth value for 5-EMA entry |
| **Fixed stop-loss** | 8 % | Stop-loss percentage below entry |
| **Enter also on 5-EMA trough** | true | Allow additional entries on extreme momentum reversals |

Feel free to tighten or relax any of these thresholds to match your risk profile or account for different market regimes.

---

## How to use it

1. **Load the script** on a daily SPX / SPY chart.  
   (The price chart drives order execution; the breadth series is pulled internally and does not need to be on the chart.)

2. **Verify the breadth feed**.  
   INDEX:S5TH is updated after each session; your broker must provide it.

3. **Back-test across several cycles**.  
   Two decades of daily data is recommended to see how the rules behave in bear markets, range markets, and bull trends.

4. **Adjust position sizing** in the Properties tab.  
   The default is "100 % of equity"; change it if you prefer smaller allocations or pyramiding caps.

---

## Why it can help

- **Breadth signals often lead price**, allowing entries before index-level momentum turns.
- **Simple, rule-based exits** prevent "waiting for confirmation" paralysis.
- **Only one input series**—easy to audit, no black-box math.

## Trade-offs

- **Relies on a single breadth metric**; other internals (advance/decline, equal-weight returns, etc.) are ignored.
- **May sit in cash during shallow pullbacks** that never push breadth ≤ 40 %.
- **Signals arrive at the end of the session** (breadth is EoD data).

---

## ストラテジー概要（日本語版）

本スクリプトは **S&P500 のマーケットブレッド（内部需給）** だけを手がかりに、指数をスイングトレードします。

- **ブレッドデータ**: INDEX:S5TH（S&P500 採用銘柄のうち、それぞれの 200 日移動平均線を上回っている銘柄比率。0–100 %）
- **買い**: ブレッドが極端に売られたタイミング
- **売り**: ブレッドが過熱状態に達したタイミング

余計な機能を削り、**ロングオンリー & 固定ストップ** のシンプル設計にしています。

**📊 [TradingViewで表示](https://www.tradingview.com/script/dBKk4Awg-Breadth-Driven-Swing-Strategy/)**

### シグナルの流れ

#### 1. ロングエントリー
- **条件 A**: 200-EMA がトラフを付け、その値が 40 % 以下
- **条件 B**: 5-EMA がトラフを付け、
  - プロミネンス条件を満たし
  - 直近 20 本のブレッドス最小値が 20 % 以下
- B 条件は「5-EMA トラフでもエントリー」を ON にすると有効

#### 2. ロング決済
最初に出現した **200-EMA ピーク** で、かつ値が **70 % 以上** のバーで手仕舞い。

#### 3. リスク管理
各トレードに **固定ストップ**（初期価格から 8 %）を設定。

### 主なパラメータ（デフォルト値）

| パラメータ | デフォルト値 | 説明 |
|-----------|-------------|------|
| **長期 EMA 長さ** | 200 | 長期トレンド用 |
| **短期 EMA 長さ** | 5 | 短期トレンド用 |
| **ピーク判定プロミネンス** | 0.5 %pt | ピーク検出閾値 |
| **トラフ判定プロミネンス** | 3 %pt | トラフ検出閾値 |
| **ピーク水準** | 70 % | 決済用ブレッド値 |
| **トラフ水準** | 40 % | 200-EMA エントリー用 |
| **5-EMA トラフ水準** | 20 % | 5-EMA エントリー用 |
| **固定ストップ** | 8 % | ストップロス率 |
| **5-EMA トラフでもエントリー** | ON | 追加エントリー許可 |

相場環境やリスク許容度に合わせて閾値を調整してください。

### 使い方

1. **日足の SPX / SPY チャート** にスクリプトを適用
2. **ブレッドデータの供給** (INDEX:S5TH) がブローカーで利用可能か確認
3. **20 年以上の期間でバックテスト** し、強気相場・弱気相場・レンジ局面での挙動を確認
4. **資金配分** は プロパティ → 戦略実行 で調整可能（初期値は「資金の 100 %」）

### 強み

- **ブレッドは価格より先行** することが多く、天底を早期に捉えやすい
- **ルールベースの出口** で「もう少し待とう」と迷わずに済む
- **入力 series は 1 本のみ**、ブラックボックス要素なし

### 注意点・弱み

- **単一指標に依存**。他の内部需給（A/D ライン等）は考慮しない
- **40 % を割らない浅い押し目** では機会損失が起こる
- **ブレッドは終値ベースの更新**。ザラ場中の変化は捉えられない

---

## 免責事項

本スクリプトは **学習目的** で提供しています。投資助言ではありません。  
実取引の前に必ず自己責任で十分な検証とリスク管理を行ってください。

**Disclaimer**: This script is provided for educational purposes only and is not financial advice. Markets are risky; test thoroughly and use your own judgment before trading real money.