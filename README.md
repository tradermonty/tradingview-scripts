# TradingView Scripts Collection

**🇯🇵 [日本語版はこちら](#🇯🇵-日本語版説明)**

A collection of advanced Pine Script trading strategies and indicators for TradingView, focusing on market breadth analysis and earnings-driven trading opportunities.

## 📊 Scripts Overview

### 1. [Market Breadth Indicator (S5TH)](./market-breadth-indicator/)
An advanced Pine Script v6 indicator that visualizes market strength and weakness extremes by overlaying EMAs on the percentage of S&P 500 constituents trading above their 200-day SMA.

**Key Features:**
- 200-period EMA for long-term trend analysis
- 5-period EMA for short-term swing detection
- Peak (▼) and trough (▲) detection with prominence filters
- Background shading for bearish phases
- Customizable parameters for different market conditions

### 2. [Market Breadth Swing Strategy](./market-breadth-swing-strategy/)
**📊 [View on TradingView](https://www.tradingview.com/script/dBKk4Awg-Breadth-Driven-Swing-Strategy/)**

A long-only swing trading strategy that trades the S&P 500 purely based on market breadth extremes using INDEX:S5TH data.

**Key Features:**
- Entry on breadth washouts (200-EMA trough ≤ 40% or 5-EMA trough with extreme conditions)
- Exit on breadth overheating (200-EMA peak ≥ 70%)
- Fixed stop-loss risk management (default 8%)
- Simple, rule-based approach with minimal parameters

### 3. [Post-Earnings Announcement Drift (PEAD) Strategy](./post-earnings-announcement-drift-strategy/)
**📊 [View on TradingView](https://www.tradingview.com/script/tKPgsKss-PEAD-strategy/)**

A sophisticated strategy that captures the classic post-earnings announcement drift phenomenon, going long only when markets gap up after positive EPS surprises.

**Key Features:**
- EPS surprise filtering (>5% positive surprise)
- Gap-up detection (≥1% above previous close)
- Momentum confirmation (positive performance over lookback period)
- Dynamic stop-loss with breakeven adjustment
- Maximum hold period protection

---

## 🚀 Getting Started

1. **Clone or download** this repository
2. **Open TradingView** and navigate to the Pine Script editor
3. **Copy and paste** the script code from the desired strategy folder
4. **Configure parameters** according to your risk tolerance and market outlook
5. **Backtest thoroughly** before applying to live trading

## 📁 Repository Structure

```
tradingview-scripts/
├── README.md                                    # This file
├── market-breadth-indicator/
│   ├── README.md                               # Detailed indicator documentation
│   ├── Market Breadth Peaks & Troughs Indicator.png
│   └── script.txt                              # Pine Script code
├── market-breadth-swing-strategy/
│   ├── README.md                               # Strategy documentation
│   ├── Breadth-Driven Swing Strategy.png
│   └── script.txt                              # Pine Script code
└── post-earnings-announcement-drift-strategy/
    ├── README.md                               # Strategy documentation
    ├── PEAD Strategy.png
    └── script.txt                              # Pine Script code
```

## ⚠️ Risk Disclosure

**Important:** These scripts are provided for **educational purposes only** and do not constitute financial advice. Trading involves substantial risk of loss and may not be suitable for all investors. 

- **Backtest thoroughly** with historical data before live trading
- **Start with small position sizes** when testing strategies
- **Understand the logic** behind each script before implementation
- **Markets can change** - what worked in the past may not work in the future

## 🔧 Requirements

- **TradingView Pro/Pro+/Premium** account (for advanced features and real-time data)
- **Pine Script v5/v6** knowledge for customization
- **Market data access** for INDEX:S5TH (S&P 500 breadth data)
- **Earnings data** for PEAD strategy implementation

## 📚 Reference

- **Pine Script® Language Documentation:** [https://www.tradingview.com/pine-script-docs/welcome/](https://www.tradingview.com/pine-script-docs/welcome/)
  - Complete language specification and tutorials
  - Built-in functions and variables reference
  - Best practices and optimization guides
  - Migration guides for version updates

## 📈 Performance Notes

- Results shown are based on historical backtesting
- Past performance does not guarantee future results
- Slippage, commissions, and real-world execution may affect results
- Consider market regime changes when evaluating strategy performance

---

## 🇯🇵 日本語版説明

# TradingView スクリプトコレクション

TradingView用の高度なPine Scriptトレーディング戦略とインジケーターのコレクションです。マーケットブレッド分析と決算主導の取引機会に焦点を当てています。

## 📊 スクリプト概要

### 1. [マーケットブレッドインジケーター (S5TH)](./market-breadth-indicator/)
S&P500構成銘柄の200日SMAを上回る銘柄比率にEMAを重ね合わせて、相場の強弱の極値を可視化する高度なPine Script v6インジケーターです。

**主要機能:**
- 長期トレンド分析用200期間EMA
- 短期スイング検出用5期間EMA
- プロミネンスフィルター付きピーク・トラフ検出
- 弱気フェーズの背景色表示
- 様々な相場環境に対応するカスタマイズ可能パラメーター

### 2. [マーケットブレッドスイング戦略](./market-breadth-swing-strategy/)
**📊 [TradingViewで表示](https://www.tradingview.com/script/dBKk4Awg-Breadth-Driven-Swing-Strategy/)**

INDEX:S5THデータを使用してマーケットブレッドの極値のみでS&P500を取引するロングオンリーのスイングトレーディング戦略です。

**主要機能:**
- ブレッド底打ちでのエントリー（200-EMAトラフ≤40%または5-EMAトラフで極端条件）
- ブレッド過熱での決済（200-EMAピーク≥70%）
- 固定ストップロスによるリスク管理（デフォルト8%）
- 最小限のパラメーターでシンプルなルールベースアプローチ

### 3. [決算後株価ドリフト (PEAD) 戦略](./post-earnings-announcement-drift-strategy/)
**📊 [TradingViewで表示](https://www.tradingview.com/script/tKPgsKss-PEAD-strategy/)**

クラシックな決算後株価ドリフト現象を捉える洗練された戦略で、EPSサプライズ後のギャップアップ時のみロングポジションを取ります。

**主要機能:**
- EPSサプライズフィルタリング（5%超の正のサプライズ）
- ギャップアップ検出（前日終値から1%以上上昇）
- モメンタム確認（ルックバック期間でのプラスパフォーマンス）
- ブレイクイーブン調整付き動的ストップロス
- 最大保有期間保護

---

## 🚀 はじめ方

1. **このリポジトリをクローンまたはダウンロード**
2. **TradingViewを開き**、Pine Scriptエディターに移動
3. **希望する戦略フォルダからスクリプトコードをコピー&ペースト**
4. **リスク許容度と相場見通しに応じてパラメーターを設定**
5. **ライブトレーディング前に十分なバックテストを実施**

## ⚠️ リスク開示

**重要:** これらのスクリプトは**教育目的のみ**で提供されており、投資助言ではありません。トレーディングには多大な損失リスクが伴い、すべての投資家に適しているわけではありません。

- **ライブトレーディング前に過去データで十分なバックテストを実施**
- **戦略テスト時は小さなポジションサイズから開始**
- **実装前に各スクリプトのロジックを理解**
- **市場は変化します** - 過去に機能したものが将来も機能するとは限りません

## 🔧 必要要件

- **TradingView Pro/Pro+/Premium** アカウント（高度な機能とリアルタイムデータ用）
- **Pine Script v5/v6** の知識（カスタマイズ用）
- **INDEX:S5TH** への市場データアクセス（S&P500ブレッドデータ）
- **決算データ**（PEAD戦略実装用）

## 📚 参考資料

- **Pine Script® 言語仕様:** [https://www.tradingview.com/pine-script-docs/welcome/](https://www.tradingview.com/pine-script-docs/welcome/)
  - 完全な言語仕様とチュートリアル
  - 組み込み関数と変数のリファレンス
  - ベストプラクティスと最適化ガイド
  - バージョン更新のマイグレーションガイド

## 📈 パフォーマンス注意事項

- 表示される結果は過去のバックテストに基づいています
- 過去のパフォーマンスは将来の結果を保証するものではありません
- スリッページ、手数料、実際の執行が結果に影響を与える可能性があります
- 戦略パフォーマンス評価時には市場レジーム変化を考慮してください

---

## 📞 Contact & Contributions

For questions, suggestions, or contributions, please feel free to:
- Open an issue in this repository
- Submit pull requests for improvements
- Share your backtesting results and optimizations

**Happy Trading! / ハッピートレーディング！** 