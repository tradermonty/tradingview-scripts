# Market Breadth Indicator (S5TH)

**🇯🇵 [日本語版はこちら](#日本語版解説)**

![Market Breadth Peaks & Troughs Indicator](Market%20Breadth%20Peaks%20&%20Troughs%20Indicator.png)

## Indicator Overview

Market Breadth (S5TH) visualizes extremes of market strength and weakness by overlaying -
- a 200-period EMA (long-term trend)
- a 5-period EMA (short-term trend, user-adjustable)

on the percentage of S&P 500 constituents trading above their 200-day SMA (INDEX:S5TH).
Peaks (▼) and troughs (▲) are detected with prominence filters so you can quickly spot overbought and oversold conditions.

---

## Core Logic

| Component | Description |
|-----------|-------------|
| Breadth series | INDEX:S5TH — % of S&P 500 stocks above their 200-SMA |
| Long EMA | 200-EMA to capture the primary trend |
| Short EMA | 5-EMA (default, editable) for short-term swings |
| Peak detection | ta.pivothigh + prominence ⇒ major peaks marked with red ▼ |
| Trough detection (200 EMA) | ta.pivotlow + prominence + value < longTroughLvl ⇒ blue ▲ |
| Trough detection (5 EMA) | ta.pivotlow + prominence + value < shortTroughLvl ⇒ green ▲ |
| Background shading | Pink when 200 EMA slope is down and 5 EMA sits below 200 EMA |

---

## Adjustable Parameters

| Group | Variable | Default | Purpose |
|-------|----------|---------|---------|
| Symbol | breadthSym | INDEX:S5TH | Breadth index |
| Long EMA | longLen | 200 | Period of long EMA |
| Short EMA | shortLen | 5 | Period of short EMA |
| Pivot width (long) | pivotLen | 15 | Bars left/right for 200-EMA peaks/troughs |
| Pivot width (short) | pivotLenS | 10 | Bars for 5-EMA troughs |
| Prominence (long) | promThresh | 1.0 %-pt | Depth filter for 200-EMA pivots |
| Prominence (short) | promThreshS | 3.0 %-pt | Depth filter for 5-EMA pivots |
| Trough level (long) | longTroughLvl | 50 % | Max value to accept a 200-EMA trough |
| Trough level (short) | shortTroughLvl | 30 % | Max value to accept a 5-EMA trough |

---

## Signal Guide

| Marker / Color | Meaning | Typical reading |
|----------------|---------|-----------------|
| Red ▼ | Major breadth peak | Overbought / possible top |
| Blue ▲ | Deep 200-EMA trough | End of mid-term correction |
| Green ▲ | Shallow 5-EMA trough (early) | Short-term rebound setup |
| Pink background | Long-term down-trend and short-term weak | Risk-off phase |

---

## Typical Use Cases

### 1. Counter-trend timing
- **Fade greed**: trim longs on red ▼
- **Buy fear**: scale in on green ▲; add on blue ▲

### 2. Trend filter
- Avoid new longs while the background is pink; wait for a trough & recovery.

### 3. Risk management
- Reduce exposure when peaks appear, reload partial size on confirmed troughs.

---

## Notes & Tips

- **INDEX:S5TH** is sourced from TradingView and may be back-adjusted when index membership changes.
- **Fine-tune** pivotLen, promThresh, and level thresholds to match current volatility before relying on alerts or automated rules.
- **Slope thresholds** (±0.10 %-pt) that trigger background shading can also be customized for different market regimes.

---

## 日本語版解説

Market Breadth (S5TH) は、S&P500 構成銘柄の「200 日 SMA を上回る銘柄比率」をベースに
- 長期トレンド用 200 EMA
- 短期トレンド用 5 EMA（任意で 8 EMA や他の日数にも変更可）

を重ね合わせ、ピーク（▼）とトラフ（▲） を検出して相場の過熱・売られ過ぎ局面を可視化する Pine Script v6 インジケーターです。

### 主要ロジック

| 要素 | 内容 |
|------|------|
| S5TH | INDEX:S5TH — S&P500 銘柄のうち 200 SMA を上回る銘柄比率 (%) |
| Long EMA | 200 EMA で長期トレンドを把握 |
| Short EMA | 既定 5 EMA で短期トレンドを把握（入力で変更可） |
| ピーク検出 | ta.pivothigh ＋ プロミネンス判定 → 大きな山のみ赤▼ |
| トラフ検出 (200 EMA) | ta.pivotlow ＋ プロミネンス ＋ 値が longTroughLvl (%) 未満 → 青▲ |
| トラフ検出 (5 EMA) | ta.pivotlow ＋ プロミネンス ＋ 値が shortTroughLvl (%) 未満 → 緑▲ |
| 背景色 | 200 EMA が下降傾向かつ 5 EMA が 200 EMA を下回る期間をピンクでハイライト |

### パラメータ一覧（すべて input() で可変）

| 区分 | 変数 | 既定値 | 説明 |
|------|------|--------|------|
| 指標シンボル | breadthSym | INDEX:S5TH | 市場ブレッドス指標 |
| 長期 EMA | longLen | 200 | 200 EMA |
| 短期 EMA | shortLen | 5 | 5 EMA（任意で変更可） |
| ピボット幅 (長期) | pivotLen | 15 | 山谷判定バー数 (200 EMA) |
| ピボット幅 (短期) | pivotLenS | 10 | 山谷判定バー数 (5 EMA) |
| プロミネンス (長期) | promThresh | 1.0 (%pt) | 山・谷の"深さ"しきい値 |
| プロミネンス (短期) | promThreshS | 3.0 (%pt) | 同上 (5 EMA) |
| トラフ水準 (長期) | longTroughLvl | 50 % | 200 EMA トラフ採用閾値 |
| トラフ水準 (短期) | shortTroughLvl | 30 % | 5 EMA トラフ採用閾値 |

### シグナルの読み方

| マーク / 色 | 意味 | 典型的解釈 |
|------------|------|-----------|
| 赤▼ | ブレッドス指標の大きなピーク | 過熱警戒・天井摸索 |
| 青▲ | 200 EMA ベースの深いトラフ | 中長期の調整完了サイン |
| 緑▲ | 5 EMA ベースの浅めトラフ（早期シグナル） | 短期リバウンド期待 |
| ピンク背景 | 長期下降＋短期弱気 | 弱気フェーズ継続リスク |

### 代表的な使い方

#### 1. 逆張りタイミングの計測
- 緑▲で先行エントリー、青▲で本格買いを検討

#### 2. トレンドフィルター
- ピンク背景中はロングを控え、トラフからの反転を待つ

#### 3. リスク管理
- 赤▼出現でポジション縮小、急落時の緑▲で部分買い戻しを検討

### 注意点

- **INDEX:S5TH** は TradingView 提供のデータです。構成銘柄入れ替えなどで遡及修正される場合があります。
- **ピボット幅やプロミネンス閾値** は相場環境により最適値が変わるため、ヒストリカル検証でチューニングすることを推奨します。
- **背景判定の傾き閾値**（±0.10 ％ポイント）は市場ボラティリティに合わせて調整可能です。