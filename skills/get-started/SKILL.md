---
name: get-started
description: Connect Xmanmobi and run an initial read-only advertising analysis when a user installs the plugin or asks how to begin using it.
---

# Xmanmobi Setup

Help the user connect their Xmanmobi account and confirm that authorized advertising data is available.

1. If the Xmanmobi MCP connection is not authenticated, ask the user to complete the OAuth sign-in flow in the browser. Never ask the user to paste a password, access token, refresh token, API key, or authorization code into the conversation.
2. Call `list_customers` to confirm the customer scope available to the connected account.
3. If more than one customer is available and the user's target is unclear, ask which customer to analyze. Do not infer access to customers absent from the response.
4. Call `get_ad_overview` for the selected customer and the last seven days. Use `platform: all` unless the user requested Google or Facebook specifically.
5. Summarize spend, impressions, clicks, conversions, conversion value, and data freshness. Clearly distinguish missing or stale data from true zero values.
6. Offer a relevant next read-only analysis such as campaign performance, period comparison, creative analysis, search-term analysis, conversion funnel review, or data-quality checks.

All Xmanmobi tools in this plugin are read-only. Do not claim that a campaign, ad, keyword, budget, account, or report was created, edited, paused, published, or deleted. Base conclusions on tool results, preserve the user's customer permissions, and state when the requested data is unavailable.
