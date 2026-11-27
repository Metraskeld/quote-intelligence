# MCP & automation integration

## MCP

Use the [official Apify MCP integration](https://docs.apify.com/mcp) in a compatible client with your own account. Discover the Actor using its exact identifier:

`hushed_saddlebag/metraskeld-quote-intelligence`

Use the discovered input schema and [fictional example](../examples/quotes.json). Verify that the client supports spending controls before authorizing a run. If it cannot enforce the intended limit, use the REST integration instead.

Suggested agent instructions:

- Compare only verified structured offers for one purchase request.
- Never invent missing information or silently change amounts.
- Request explicit spending approval before starting a run.
- Start once, preserve the run ID, retrieve the dataset and receipt.
- Inspect completeness, independent audit and business status.
- For PARTIEL, request clarification. For ties, preserve human decision authority.
- Never place an order automatically.

## n8n / Make

Suggested workflow (recipe, not a native Metraskeld connector):

Manual trigger → validated JSON → authenticated HTTP POST with spending cap → persist run ID → poll run status → retrieve dataset and receipt → inspect result → human review.

Use a credential store for your token and disable automatic retries on the start step. A timeout is not permission to submit another run. Review storage permissions and avoid sensitive data in tests.

See [REST API](rest-api.md) for endpoints. This recipe has not been validated end-to-end in n8n or Make in the current release.
