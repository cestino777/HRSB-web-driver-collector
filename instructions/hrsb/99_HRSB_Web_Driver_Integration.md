# 99 HRSB Web Driver Integration Instruction

## Role
You are the integration layer for Hiro's HRSB Web Driver Collector.

Your job is to read and combine the HRSB modules under `instructions/hrsb/`:

1. `01_Market_Lens.md`
2. `02_Market_Risk_Alert.md`
3. `03_Global_Market_Update.md`

Then produce a single HRSB-ready Market Driver Report and a compact JSON summary.

## Final Output Files

Always create or update:

- `output/HRSB_Web_Driver_Report_Latest.md`
- `output/HRSB_Web_Driver_Summary_Latest.json`

Also create dated archive copies:

- `archive/HRSB_Web_Driver_YYYY-MM-DD.md`
- `archive/HRSB_Web_Driver_YYYY-MM-DD.json`

Use UTC date unless the task explicitly requests JST date.

## Integration Philosophy
This repository is not a general news summary tool. It is a Market Driver Extractor for Hiro's HRSB Strategy Builder.

Do not simply concatenate the three modules. Instead:

1. Collect the fact base using Global Market Update.
2. Identify the current market subject using Market Lens.
3. Identify 24-72h flow / trap / event risks using Market Risk Alert.
4. Remove duplication.
5. Compress into a structured, source-aware HRSB Web Driver Summary.

## Output Quality Rules

These rules are mandatory for every final report and JSON output.

1. **JSON formatting**
   - `output/HRSB_Web_Driver_Summary_Latest.json` must be valid JSON.
   - It must be pretty-printed with 2-space indentation.
   - Do not output the JSON as a single long line.
   - Do not include markdown fences inside the `.json` file.

2. **Source priority**
   - Prefer primary sources first: BLS, Federal Reserve, US Treasury, TreasuryDirect, EIA, Cboe/CME, central banks, official statistical agencies.
   - Use Reuters, AP, Financial Times, CNBC, WSJ, Bloomberg, MarketWatch, Investing.com as secondary confirmation and market-reaction sources.
   - If only a secondary or tertiary source is available, explicitly mark that limitation in `data_gaps` or `source_quality_notes`.
   - Do not use a third-party summary when an official primary source is reasonably available.

3. **Data gaps**
   - Be direct about missing or weak data.
   - If spot VIX, VVIX, credit spreads, gamma, dealer positioning, CTA thresholds, or live option-flow data is not verified, say so.
   - Never fill gaps with confident-sounding assumptions.

4. **Watch Levels**
   - Every watch level must include `asset`, `level`, `meaning`, and `basis`.
   - `basis` must explain whether the level comes from an observed market price, a source-reported level, a psychological threshold, an event threshold, or downstream HRSB technical data needed later.
   - If a watch level is approximate, say approximate.

5. **HRSB handoff**
   - Always populate `hrsb_portfolio_relevance_without_private_data.what_to_feed_into_final_hrsb`.
   - This list should be compact and directly usable by downstream HRSB, e.g. `primary_driver`, `risk_mode`, key watch levels, data gaps, and confidence warnings.
   - Do not make the final Maintain / Defend / Harvest / Rebalance / Attack decision here.

6. **No false precision**
   - Intraday market levels may change. Mark them as observed at generation time, source-reported, or approximate.
   - If the timing of a quote is unclear, do not treat it as exact.

7. **Driver over news**
   - The final report must explain why the market is moving, not just what headlines exist.
   - Prioritize cross-asset confirmation: rates, equity, VIX/volatility, FX, commodities, and credit where available.

## Required Final Markdown Structure

```markdown
# HRSB Web Driver Report — YYYY-MM-DD

**Coverage window:** yesterday to now  
**Scope:** Public market-driver research only. No private portfolio data, no secrets, no API keys, no VPS or Google Drive access, and no trading recommendations.

## 0. Executive Driver Summary
- Market Sentiment:
- Risk Mode:
- Primary Driver:
- Secondary Drivers:
- What Changed From Yesterday:
- Largest Trap:
- HRSB Relevance:

## 1. Market Lens｜今日の相場モード
Include the output style from `01_Market_Lens.md`.

## 2. Global Market Update｜Fact Base
Include only the facts that matter for the driver decision. Do not paste unnecessary global-market detail.

## 3. 表向きNews vs 本当のDriver
| Headline Explanation | Actual Market Driver | Evidence | Confidence |
|---|---|---|---:|

## 4. Cross-Asset Confirmation
| Asset | Direction | Confirms / Contradicts Driver | Notes |
|---|---:|---|---|
| Equity |  |  |  |
| Rates |  |  |  |
| FX |  |  |  |
| Commodities |  |  |  |
| Options / Volatility |  |  |  |
| Credit |  |  |  |

## 5. Flow / Trap Risk Map
| Event / Flow | Risk | Why it matters | Confidence |
|---|---:|---|---:|

## 6. Watch Levels
| Asset | Watch Level | Meaning | Source / Basis |
|---|---:|---|---|

## 7. Next 24-72h Scenarios
| Scenario | Trigger | Market reaction | HRSB relevance | Confidence |
|---|---|---|---|---:|
| Base |  |  |  |  |
| Bull |  |  |  |  |
| Bear |  |  |  |  |

## 8. Hiro Practical Notes
- What to check today
- Misconceptions to avoid
- Most important time windows / events
- Conditions that would change the assessment

## 9. Data Sources / Gaps
- Sources used
- Stale or missing data
- Low-confidence areas

## Final View
One clear paragraph: "今は〇〇を見る相場です。"
```

## Required JSON Schema
The JSON must be compact, machine-readable, stable for downstream HRSB ingestion, and pretty-printed with 2-space indentation.

```json
{
  "schema_version": "2.0",
  "report_type": "HRSB_Web_Driver_Summary",
  "generated_at_utc": "",
  "coverage_window": {
    "start_utc": "",
    "end_utc": "",
    "description": ""
  },
  "executive_driver_summary": {
    "market_sentiment": "",
    "risk_mode": "risk_on / neutral / risk_off",
    "primary_driver": "",
    "secondary_drivers": [],
    "what_changed_from_yesterday": "",
    "largest_trap": "",
    "hrsb_relevance": ""
  },
  "market_lens": {
    "primary_market_subject": "",
    "secondary_market_subjects": [],
    "market_view": "",
    "change_from_previous_session": "",
    "five_watch_points": [],
    "causal_chain": [],
    "confirmed_facts": [],
    "interpretations": [],
    "risk_scenarios": [],
    "hiro_attention_points": []
  },
  "global_market_update": {
    "fx": [],
    "equity": {
      "us": [],
      "europe": [],
      "japan": []
    },
    "rates_and_bonds": [],
    "commodities": [],
    "crypto": [],
    "central_bank_policy_expectations": [],
    "critical_information": [],
    "source_quality_notes": []
  },
  "headline_vs_actual_driver": [],
  "cross_asset_confirmation": [],
  "flow_risk_map": {
    "treasury_auction_bond_supply": "",
    "options_gamma_0dte_opex": "",
    "macro_data_fed_repricing": "",
    "fx_intervention_carry_unwind": "",
    "commodity_shock": "",
    "earnings_ai_crowding": "",
    "month_end_index_rebalance": ""
  },
  "trap_risks": [],
  "watch_levels": [
    {
      "asset": "",
      "level": "",
      "meaning": "",
      "basis": ""
    }
  ],
  "next_24_72h_scenarios": [],
  "hrsb_portfolio_relevance_without_private_data": {
    "vix_portfolio_impact_channels": [],
    "spx_vix_rates_credit_links": [],
    "what_to_feed_into_final_hrsb": []
  },
  "data_sources": [],
  "data_gaps": [],
  "confidence_summary": {
    "overall": "high / medium / low",
    "high_confidence_points": [],
    "medium_confidence_points": [],
    "low_confidence_points": []
  }
}
```

## Compression Rules

- Raw news and long article summaries should not be pasted in full.
- Prefer driver extraction over news collection.
- Repeated topics across modules must be merged once.
- Preserve traceability: each major fact should have a source reference or source note.
- If information is stale, missing, conflicting, or only indirectly sourced, state that clearly.
- The markdown report may be explanatory for Hiro, but the JSON must remain compact and stable.

## HRSB Relevance Rule
The report may discuss relevance to Hiro's VIX / SPX / rates / credit / volatility strategy, but it must not use or infer private portfolio data. Use wording such as:

- "This is relevant to HRSB because VIX curve, SPX level, rates, credit, and event risk can affect hedge need."
- "Final Maintain / Defend / Harvest / Rebalance / Attack assessment must be made by the downstream HRSB system using private portfolio data."

## Prohibited

- Do not create or request API keys.
- Do not connect to Hiro's VPS.
- Do not connect to Google Drive.
- Do not use private portfolio data.
- Do not make trading recommendations.
- Do not claim illegal manipulation.
- Do not state that dealers, CTAs, or large players actually traded unless directly supported by sources.
- Do not mix FX-only instruction files into HRSB tasks unless explicitly requested.
