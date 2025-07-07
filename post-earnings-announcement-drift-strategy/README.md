# Post-Earnings Announcement Drift (PEAD) Strategy

**🇯🇵 [日本語版はこちら](#日本語版説明)**

![PEAD Strategy](PEAD%20Strategy.png)

## OVERVIEW

This strategy trades the classic post-earnings announcement drift (PEAD).
It goes long only when the market gaps up after a positive EPS surprise.

**📊 [View on TradingView](https://www.tradingview.com/script/tKPgsKss-PEAD-strategy/)**

---

## LOGIC

1. **Earnings filter** — EPS surprise > epsSprThresh %
2. **Gap filter** — first regular 5-minute bar gaps ≥ gapThresh % above yesterday's close
3. **Timing** — only the first qualifying gap within one trading day of the earnings bar
4. **Momentum filter** — last perfDays trading-day performance is positive
5. **Risk management**
   - Fixed stop-loss: stopPct % below entry
   - Trailing exit: price < Daily EMA(emaLen)

---

## INPUTS

| Parameter | Default | Description |
|-----------|---------|-------------|
| **Gap up threshold (%)** | 1 | Gap size for entry |
| **EPS surprise threshold (%)** | 5 | Minimum positive surprise |
| **Past price performance** | 20 | Look-back bars for trend check |
| **Fixed stop-loss (%)** | 8 | Hard stop distance |
| **Daily EMA length** | 30 | Trailing exit length |

**Note** — Back-tests fill on the second 5-minute bar (Pine limitation).  
Live trading: enable `calc_on_every_tick=true` for first-tick entries.

---

## RELEASE NOTES

### April 27
**Fixed EPS-Surprise calculation** – now divides by `abs(epsEstimate)` so cases with a negative estimate (e.g., estimate < 0, actual > 0) return the correct positive surprise.

### May 3
**Enhanced Features:**
- **Fixed stop logic enhanced**: Changed from a simple fixed stop-loss to a dynamic stop that moves to breakeven once price reaches +2R profit from entry price.
- **Added maximum hold period**: Implemented a new feature that forces position closure after a specified number of bars (default 50) have elapsed since entry.
- **EMA exit logic changed**: Modified from "exit when price is below EMA" to the more precise "exit only when price crosses under the EMA," requiring a specific signal rather than just price position.

### May 4
**Chart & Order Improvements:**
- **Entry/Exit chart labels enhanced**
- **Fixed-stop orders** now submit only above stop level; breakeven shift after ≥ 2R

---

## 日本語版説明

本ストラテジーは決算後の **PEAD（Post-Earnings Announcement Drift）** を狙い、EPS サプライズがプラス かつ 寄付きギャップアップ が発生した銘柄をスイングで買い持ちします。

**📊 [TradingViewで表示](https://www.tradingview.com/script/tKPgsKss-PEAD-strategy/)**

---

## ロジック

1. **決算フィルター** — EPS サプライズ > epsSprThresh %
2. **ギャップフィルター** — レギュラー時間最初の 5 分足が前日終値＋gapThresh %以上
3. **タイミング** — 決算当日または翌営業日の最初のギャップのみエントリー
4. **モメンタムフィルター** — 過去 perfDays 営業日の騰落率がプラス
5. **リスク管理**
   - 固定ストップ：エントリー − stopPct %
   - 利確：終値が日足 EMA(emaLen) を下抜け

---

## 入力パラメータ

| パラメータ | デフォルト値 | 説明 |
|-----------|-------------|------|
| **Gap up threshold (%)** | 1 | ギャップ条件 |
| **EPS surprise threshold (%)** | 5 | EPS サプライズ最小値 |
| **Past price performance** | 20 | パフォーマンス判定日数 |
| **Fixed stop-loss (%)** | 8 | 固定ストップ幅 |
| **Daily EMA length** | 30 | 利確用 EMA 期間 |

**注意** — Pine の仕様上、バックテストでは寄付き 5 分足の次バーで約定します。  
実運用で寄付き成行に合わせたい場合は `calc_on_every_tick=true` を有効にしてください。

---

## リリースノート

### 4月27日
**EPS サプライズ計算の修正** – `abs(epsEstimate)` で除算するように変更し、予想が負の場合（例：予想 < 0、実績 > 0）でも正しい正のサプライズを返すようになりました。

### 5月3日
**機能強化:**
- **ストップロス機能の強化**: 単純な固定ストップロスから、エントリー価格から+2Rの利益に達すると損益分岐点（ブレイクイーブン）に移動する動的ストップに変更
- **最大保有期間の追加**: エントリーから指定バー数（デフォルト50バー）が経過すると強制的にポジションを終了する機能を実装
- **EMA出口ロジックの変更**: 「価格がEMA以下の場合に決済」から、より厳密な「価格がEMAを下方クロス（crossunder）した時のみ決済」に変更

### 5月4日  
**チャート＆オーダー改善:**
- **エントリー／エグジットのラベル強化**
- **固定ストップ** は水準超えで発注、ブレークイーブン移動は 2R 以上

---

ご意見や質問があればお気軽にコメントください。  
**Happy trading!**