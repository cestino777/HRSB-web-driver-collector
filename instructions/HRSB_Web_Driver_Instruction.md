# HRSB Web Driver Instruction

## Objective

Collect and summarize public web information about US market drivers from yesterday to now for use in Hiro's HRSB Strategy Builder. The output should explain what changed, what is driving markets, and which risks may matter over the next 24-72 hours.

This workflow is for public market-driver research and structured summary output only. It must not create or request API keys, connect to Hiro's VPS, connect to Google Drive, include secrets, use private portfolio data, or make trading recommendations.

## Research Focus

Cover the following areas when relevant and source-supported:

- Broad US equity market direction, including SPX and Nasdaq.
- VIX and volatility context.
- Rates and Treasury curve moves.
- Credit spreads or credit-risk tone.
- US dollar and major FX context.
- Commodities, especially oil and gold when market-relevant.
- Options-flow and market-structure context.
- Major macro, policy, earnings, geopolitical, liquidity, or positioning headlines.
- Difference between the headline explanation and the likely actual market driver.
- 24-72 hour scheduled and unscheduled risk events.
- Relevance to VIX portfolio strategy without using private portfolio data.

## Required Analytical Separation

Each report and JSON summary must separate:

- **Facts:** public, source-supported observations.
- **Interpretations:** analyst assessment or explanation.
- **Confidence:** confidence level and explanation of uncertainty.

Do not state that dealers, CTAs, volatility-control funds, risk-parity funds, or other large players actually traded unless directly supported by cited sources. If evidence is incomplete, describe these only as market-structure risks, positioning risks, or likely flow risks.

## Expected JSON File

Future structured summaries should be written to:

`output/HRSB_Web_Driver_Summary_Latest.json`

A dated copy should also be archived as:

`archive/HRSB_Web_Driver_YYYY-MM-DD.json`

## Expected JSON Schema

The JSON summary should follow this schema shape:

```json
{
  "schema_version": "1.0",
  "report_type": "HRSB_Web_Driver_Summary",
  "generated_at_utc": "YYYY-MM-DDTHH:MM:SSZ",
  "coverage_window": {
    "start_utc": "YYYY-MM-DDTHH:MM:SSZ",
    "end_utc": "YYYY-MM-DDTHH:MM:SSZ",
    "description": "Public market-driver information from yesterday to now."
  },
  "market_session_context": {
    "current_session_date": "YYYY-MM-DD",
    "previous_session_date": "YYYY-MM-DD",
    "market_status_at_generation": "pre_market | regular_session | after_hours | closed | unknown",
    "holiday_or_special_session_notes": []
  },
  "executive_summary": {
    "one_sentence_summary": "",
    "top_drivers": [
      {
        "rank": 1,
        "driver": "",
        "asset_classes_affected": ["equities", "volatility", "rates"],
        "fact_summary": "",
        "interpretation": "",
        "confidence": "high | medium | low",
        "confidence_notes": "",
        "sources": [
          {
            "title": "",
            "publisher": "",
            "url": "",
            "published_at": "YYYY-MM-DDTHH:MM:SSZ"
          }
        ]
      }
    ]
  },
  "what_changed_from_previous_session": [
    {
      "topic": "",
      "previous_state": "",
      "current_state": "",
      "why_it_matters": "",
      "confidence": "high | medium | low",
      "sources": []
    }
  ],
  "asset_context": {
    "spx": {
      "facts": [],
      "interpretations": [],
      "confidence": "high | medium | low",
      "sources": []
    },
    "nasdaq": {
      "facts": [],
      "interpretations": [],
      "confidence": "high | medium | low",
      "sources": []
    },
    "vix_volatility": {
      "facts": [],
      "interpretations": [],
      "confidence": "high | medium | low",
      "sources": []
    },
    "rates": {
      "facts": [],
      "interpretations": [],
      "confidence": "high | medium | low",
      "sources": []
    },
    "credit": {
      "facts": [],
      "interpretations": [],
      "confidence": "high | medium | low",
      "sources": []
    },
    "fx": {
      "facts": [],
      "interpretations": [],
      "confidence": "high | medium | low",
      "sources": []
    },
    "commodities": {
      "facts": [],
      "interpretations": [],
      "confidence": "high | medium | low",
      "sources": []
    },
    "options_flow_market_structure": {
      "facts": [],
      "interpretations": [],
      "flow_risk_language": "Use market-structure risk or likely flow risk unless actual trading is source-supported.",
      "confidence": "high | medium | low",
      "sources": []
    }
  },
  "headline_vs_actual_driver": [
    {
      "headline_narrative": "",
      "actual_or_more_likely_driver": "",
      "evidence": [],
      "interpretation": "",
      "confidence": "high | medium | low",
      "sources": []
    }
  ],
  "risk_events_24_72h": [
    {
      "event_name": "",
      "scheduled_time_utc": "YYYY-MM-DDTHH:MM:SSZ or null",
      "event_type": "macro | central_bank | earnings | geopolitical | treasury_supply | options_expiration | liquidity | other",
      "expected_relevance": "",
      "volatility_relevance": "",
      "confidence": "high | medium | low",
      "sources": []
    }
  ],
  "vix_portfolio_strategy_relevance": {
    "public_context_only": true,
    "summary": "",
    "possible_implications_without_recommendation": [],
    "risks_to_monitor": [],
    "not_trading_advice": true
  },
  "source_log": [
    {
      "title": "",
      "publisher": "",
      "url": "",
      "published_at": "YYYY-MM-DDTHH:MM:SSZ",
      "accessed_at_utc": "YYYY-MM-DDTHH:MM:SSZ",
      "notes": ""
    }
  ],
  "quality_controls": {
    "facts_interpretations_confidence_separated": true,
    "no_trading_recommendations": true,
    "no_private_portfolio_data_used": true,
    "no_secrets_or_api_keys_included": true,
    "no_unsupported_claims_of_actual_large_player_trading": true,
    "limitations": []
  }
}
```

## Markdown Report Expectations

Future markdown reports should be written to:

`output/HRSB_Web_Driver_Report_Latest.md`

A dated copy should also be archived as:

`archive/HRSB_Web_Driver_YYYY-MM-DD.md`

The markdown report should include:

1. Title and coverage window.
2. Executive summary.
3. Top market drivers.
4. What changed from the previous session.
5. Asset context sections for SPX, Nasdaq, VIX, rates, credit, FX, commodities, and options-flow or market-structure context.
6. Headline explanation versus actual or more likely driver.
7. 24-72 hour risk events.
8. VIX portfolio strategy relevance using public context only and no trading recommendations.
9. Source list.
10. Limitations and confidence notes.
