# HRSB Web Driver Collector

HRSB Web Driver Collector is a public market-driver research repository for Hiro's HRSB Strategy Builder. The project is intended to collect and summarize public web information about US market drivers from yesterday to now, then produce structured report and JSON outputs that can be reviewed or ingested by the HRSB workflow.

## Purpose

The repository supports daily market-context collection for US markets, with emphasis on what changed from the previous session and what may matter over the next 24-72 hours. It is designed for research organization only and does not make trading recommendations.

## Analyst Role

The project follows the `HRSB Market Driver Analyst` role defined in `AGENTS.md`. The analyst focuses on:

- What is driving US markets from yesterday to now.
- What changed from the previous session.
- SPX, Nasdaq, VIX, rates, credit, FX, commodities, and options-flow context.
- Headline explanation versus actual market driver.
- Upcoming 24-72 hour risk events.
- Relevance to VIX portfolio strategy without using private portfolio data.

## Repository Structure

```text
.
├── AGENTS.md
├── README.md
├── instructions/
│   └── HRSB_Web_Driver_Instruction.md
├── output/
│   └── .gitkeep
└── archive/
    └── .gitkeep
```

## Future Outputs

The project is expected to generate the following files in later workflow iterations:

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

## Reporting Standards

Every report should clearly separate:

1. **Facts** — source-supported observations, market moves, events, and public data.
2. **Interpretations** — analyst assessment of why the facts may matter.
3. **Confidence** — confidence level and uncertainty notes.

Market-structure commentary must be carefully worded. Do not state that dealers, CTAs, volatility-control funds, risk-parity funds, or other large players actually traded unless supported by sources. When direct evidence is unavailable, describe them as market-structure risks, positioning risks, or likely flow risks only.
