# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Architecture

This is a TradingView Pine Script repository containing three main trading strategies with corresponding educational content and articles. The repository is bilingual (English/Japanese) and focuses on systematic, data-driven trading approaches using market breadth analysis.

### Core Components

**Pine Script Strategies (3 main folders):**
1. `market-breadth-indicator/` - Pine Script v6 indicator for S&P 500 market breadth analysis
2. `market-breadth-swing-strategy/` - Pine Script v5 strategy that trades based on breadth extremes
3. `post-earnings-announcement-drift-strategy/` - Pine Script v5 strategy for post-earnings drift trading

**Educational Content:**
- `articles/` - Contains blog content and quality checklists for content creation
- Each strategy folder contains detailed README.md documentation and visual examples

### Key Data Dependencies

- **INDEX:S5TH** - S&P 500 market breadth data (percentage of stocks above 200-day SMA)
- **Earnings data** - Required for PEAD strategy implementation
- **TradingView Pro/Pro+/Premium** subscription recommended for full functionality

## Content Creation Workflow

### Blog Article Development
When creating or editing blog content, use the provided checklists:

1. **General Blog Content**: Follow `articles/blog_checklist.md` for SEO, readability, and engagement
2. **note.com Specific Content**: Follow `articles/note_checklist.md` for platform-specific optimization

### Key Content Requirements
- **Bilingual documentation** (English first, Japanese translations)
- **Risk disclaimers** must be prominently featured in all educational content
- **Backtesting methodology** should be transparently documented
- **Code explanations** should be accessible to Pine Script beginners

## Pine Script Development Guidelines

### Version Standards
- New indicators: Use Pine Script v6
- Existing strategies: Maintain Pine Script v5 compatibility unless migration required
- All scripts must include Mozilla Public License 2.0 header

### Code Organization Pattern
Each strategy folder follows this structure:
```
strategy-name/
├── README.md           # Bilingual documentation
├── script.txt          # Pine Script source code
└── [Strategy Name].png # Visual example/chart
```

### Market Breadth Integration
The core indicator (S5TH) serves as the foundation for the swing strategy. When modifying breadth-related code:
- 200-period EMA represents long-term trend
- 5-period EMA for short-term swing detection
- Standard thresholds: 70% (overbought), 40% (oversold)
- Peak/trough detection uses prominence filters

## Strategy Relationships

**Dependency Flow:**
1. Market Breadth Indicator → provides analysis foundation
2. Breadth Swing Strategy → implements trading rules based on indicator signals
3. PEAD Strategy → independent earnings-based approach

When updating the breadth indicator, consider impact on swing strategy parameters and documentation.

## Educational Content Philosophy

All content follows these principles:
- **Transparency over complexity** - simple, rule-based approaches preferred
- **Risk-first mindset** - stop-losses and risk management prominently featured
- **Educational focus** - content designed for learning, not financial advice
- **Practical implementation** - step-by-step guidance for TradingView users

## Working with Articles

The `articles/` folder contains blog content optimized for different platforms. When editing:
- Use the appropriate checklist (blog_checklist.md or note_checklist.md)
- Maintain consistent terminology across English/Japanese versions
- Include proper attribution for data sources and statistical claims
- Ensure all code examples are tested and functional

## Common Content Patterns

- **Code explanations** should include line-by-line breakdowns for beginners
- **Backtesting results** must include methodology, assumptions, and limitations
- **Risk disclaimers** should be prominent and comprehensive
- **User guidance** should account for both desktop and mobile TradingView users

This repository prioritizes educational value and transparency in systematic trading approaches, with all content designed to help traders understand and implement data-driven strategies responsibly.