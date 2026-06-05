# HRSB Web Driver Collector

HRSB Web Driver Collector is a public market-driver research repository for Hiro's HRSB Strategy Builder. The project collects and summarizes public web information about market drivers from yesterday to now, then produces structured markdown and JSON outputs that can be reviewed or ingested by the HRSB workflow.

The repository is designed for research organization only. It does not make trading recommendations and does not use private portfolio data.

## Purpose

The repository supports daily market-context collection with emphasis on:

- What is driving markets from the previous session to now.
- What changed from yesterday.
- Which cross-asset signals confirm or contradict the main driver.
- Which events, flow structures, and positioning-sensitive areas may matter over the next 24-72 hours.
- How public market drivers may be relevant to HRSB without using Hiro's private portfolio data.

## Analyst Role

The project follows the `HRSB Market Driver Analyst` role defined in `AGENTS.md`.

The analyst focuses on:

- Market subject / main driver identification.
- Global market fact collection.
- Headline explanation versus likely actual driver.
- Flow / trap / event risk detection.
- Stable markdown and JSON output for downstream HRSB use.

## Repository Structure

```text
.
├── AGENTS.md
├── README.md
├── instructions/
│   ├── HRSB_Web_Driver_Instruction.md        # legacy initial instruction
│   ├── hrsb/
│   │   ├── 01_Market_Lens.md
│   │   ├── 02_Market_Risk_Alert.md
│   │   ├── 03_Global_Market_Update.md
│   │   └── 99_HRSB_Web_Driver_Integration.md
│   └── fx/
│       └── 01_FX_Market_News_Browsing.md
├── output/
│   ├── HRSB_Web_Driver_Report_Latest.md
│   └── HRSB_Web_Driver_Summary_Latest.json
└── archive/
    ├── HRSB_Web_Driver_YYYY-MM-DD.md
    └── HRSB_Web_Driver_YYYY-MM-DD.json
```

## HRSB Instruction Modules

### `instructions/hrsb/01_Market_Lens.md`
Identifies the current market subject / main driver, explains what Hiro should watch first, and creates the Market Lens section.

### `instructions/hrsb/02_Market_Risk_Alert.md`
Analyzes headline explanations versus likely actual drivers, legal flow risks, Trap Risk, Watch Levels, and 24-72h scenarios.

### `instructions/hrsb/03_Global_Market_Update.md`
Collects the global market fact base: FX, equity, rates, commodities, crypto, central banks, and critical macro information.

### `instructions/hrsb/99_HRSB_Web_Driver_Integration.md`
Integrates the above modules, removes duplication, and produces the final HRSB markdown report and compact JSON summary.

## Future FX Module

### `instructions/fx/01_FX_Market_News_Browsing.md`
Stored for future A-system / B-system use. It collects FX-related news and sentiment for USD, EUR, GBP, AUD, JPY, and Gold.

HRSB tasks should not use this FX module unless explicitly requested.

## Expected HRSB Outputs

- `output/HRSB_Web_Driver_Report_Latest.md` — latest human-readable market-driver report.
- `output/HRSB_Web_Driver_Summary_Latest.json` — latest structured summary for downstream use.
- `archive/HRSB_Web_Driver_YYYY-MM-DD.md` — dated markdown report archive.
- `archive/HRSB_Web_Driver_YYYY-MM-DD.json` — dated structured JSON archive.

## Research Boundaries

This repository is only for public market-driver research and structured summary output.

The workflow must not:

- Create or request API keys.
- Connect to Hiro's VPS.
- Connect to Google Drive.
- Include secrets or private credentials.
- Use private portfolio data.
- Make trading recommendations or provide investment advice.
- Claim illegal market manipulation, collusion, or hidden coordination.

## Reporting Standards

Every report should clearly separate:

1. **Facts** — source-supported observations, market moves, events, and public data.
2. **Interpretations** — analyst assessment of why the facts may matter.
3. **Scenarios** — conditional risk paths and watch conditions.
4. **Confidence** — confidence level and uncertainty notes.

Market-structure commentary must be carefully worded. Do not state that dealers, CTAs, volatility-control funds, risk-parity funds, macro funds, or other large players actually traded unless supported by sources. When direct evidence is unavailable, describe them as market-structure risks, positioning risks, or likely flow risks only.

## Downstream HRSB Use

This repository is a Market Driver Extractor, not the final HRSB portfolio-action engine.

The downstream HRSB system should combine:

- `output/HRSB_Web_Driver_Summary_Latest.json`
- A-system status and market data
- VIX / SPX / rates / credit / volatility data
- Hiro's private portfolio and hedge calculations

Only the downstream HRSB system should decide final Maintain / Defend / Harvest / Rebalance / Attack assessment.
