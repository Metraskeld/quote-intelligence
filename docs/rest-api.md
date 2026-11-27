# REST API quickstart

Use the [fictional sample](../examples/quotes.json). Run from the repository root. Keep your own APIFY_TOKEN in a server-side secret store. Never put a real token in Git, browser code or public messages.

## Start once

Only start after approving the cost. A complete eligible comparison costs USD 0.05; storage access may cost extra. The cap is not a guarantee of all account costs. Check current [Actor pricing](https://apify.com/hushed_saddlebag/metraskeld-quote-intelligence/pricing).

```sh
curl -X POST 'https://api.apify.com/v2/actors/hushed_saddlebag~metraskeld-quote-intelligence/runs?maxTotalChargeUsd=0.05' \
  -H "Authorization: Bearer $APIFY_TOKEN" \
  -H 'Content-Type: application/json' \
  --data-binary @examples/quotes.json
```

Persist data.id (the run ID). If the response is uncertain, reconcile your run history rather than repeating the POST.

## Poll and retrieve

```sh
curl -H "Authorization: Bearer $APIFY_TOKEN" \
  'https://api.apify.com/v2/actor-runs/RUN_ID'
```

Replace RUN_ID with the saved ID. After SUCCEEDED, retrieve the defaultDatasetId and defaultKeyValueStoreId from the run response.

```sh
curl -H "Authorization: Bearer $APIFY_TOKEN" \
  'https://api.apify.com/v2/datasets/DATASET_ID/items'
curl -H "Authorization: Bearer $APIFY_TOKEN" \
  'https://api.apify.com/v2/key-value-stores/STORE_ID/records/METRASKELD_BILLING_RECEIPT'
```

Inspect the returned agent_result, audit, completeness and decision status. For the fictional example, expect CONCLUANT and selected_offer_index 2. Do not treat SUCCEEDED or SDK_RECORDED as proof of commercial settlement; check account usage. Never purchase automatically.

This recipe has not been executed against production as part of this documentation publication. Use the current Apify API docs and review storage access settings before submitting real data.
