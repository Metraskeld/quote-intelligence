<div align="center">
<img src="https://metraskeld.pages.dev/brand-icon.png" width="88" alt="Metraskeld logo" />

# Quote Intelligence

**Supplier quote comparison & arithmetic audit for AI agents**

[Try on Apify](https://apify.com/hushed_saddlebag/metraskeld-quote-intelligence) · [Developer guide](https://metraskeld.pages.dev/developers) · [Metraskeld](https://github.com/Metraskeld)

</div>

## Why use it?

Compare 2–5 structured supplier offers against a purchase request. Detect missing lines, audit declared totals and return machine-readable decision guidance instead of guessing. Keep human approval in the loop.

**Fictional demo:** EUR 1,300 vs EUR 1,170 before VAT → EUR 130 potential savings (10%). Not a customer case or guaranteed saving.

| Scenario | Expected result |
| --- | --- |
| [Complete offers](https://apify.com/hushed_saddlebag/metraskeld-quote-intelligence/examples/compare-supplier-quotes) | CONCLUANT |
| [Missing item](https://apify.com/hushed_saddlebag/metraskeld-quote-intelligence/examples/detect-missing-quote-items) | PARTIEL |
| [Equal totals](https://apify.com/hushed_saddlebag/metraskeld-quote-intelligence/examples/compare-equal-price-quotes) | EX_AEQUO_PRIX |

## Developer quickstart

1. Review [pricing and input schema](https://apify.com/hushed_saddlebag/metraskeld-quote-intelligence). Start with fictional data.
2. Download [example input](examples/quotes.json). Use your own Apify account.
3. See [REST API guide](docs/rest-api.md) or [MCP and automation guide](docs/mcp-automation.md).
4. Store the run ID, poll status, retrieve the dataset and separate billing receipt. Do not blindly retry an uncertain start request.
5. Inspect the result before taking any business action.

| Business status | Meaning |
| --- | --- |
| CONCLUANT | Lowest comparable offer identified |
| EX_AEQUO_PRIX | Equal lowest prices; no selected winner |
| PARTIEL | Insufficient comparison evidence; request clarification |

Read `agent_result.status`, `all_offers_comparable`, `independent_audit`, `selected_offer_index` (1-based), and `can_auto_purchase`. A successful run alone does not prove a valid comparison or payment settlement.

## Pricing & scope

USD 0.05 per eligible completed comparison, including verified price ties. Separate runs may generate separate charges; storage access may incur ordinary Apify fees. Check current Apify pricing and usage.

Structured quotes only, one supported currency (EUR/USD/GBP), recoverable VAT. No PDF ingestion, OCR, supplier discovery, source authenticity certification, technical equivalence certification, FX or automatic purchases.

This repository contains integration resources only, not the proprietary comparison engine. Integration recipes are not a claim of end-to-end validation in all clients.

## Support

Use the [Actor issue channel](https://apify.com/hushed_saddlebag/metraskeld-quote-intelligence/issues). Do not publish credentials, confidential quotes or personal data.
