# Xmanmobi MCP

[中文文档](docs/README.zh-CN.md) | [Website](https://ai.xmanmobi.com/mcp.html) | [Support](https://ai.xmanmobi.com/mcp-support.html)

Xmanmobi is a read-only MCP integration for Google Ads and Meta Ads analytics. It lets compatible AI clients inspect advertising performance, compare reporting periods, analyze creatives and search terms, review conversion funnels, and check data quality within the connected user's authorized customer scope.

## What it can do

- Summarize Google Ads and Meta Ads performance.
- Compare current and previous reporting periods.
- Rank campaigns, ad groups, ads, keywords, and search terms.
- Analyze creative performance and metadata quality.
- Review conversion funnels and reporting freshness.
- Diagnose campaign performance without changing advertising resources.

All 15 tools are read-only. Xmanmobi cannot create, edit, pause, publish, or delete campaigns through this plugin.

## Connect

The hosted MCP endpoint is:

```text
https://ai.xmanmobi.com/mcp
```

### Codex CLI

Add the server to your Codex MCP configuration:

```toml
[mcp_servers.xmanmobi]
url = "https://ai.xmanmobi.com/mcp"
auth = "oauth"
```

Then authenticate:

```bash
codex mcp login xmanmobi
```

Your browser will open the Xmanmobi OAuth page. Sign in and approve the read-only advertising analytics permission. Never paste passwords, access tokens, refresh tokens, or authorization codes into a chat.

### Plugin package

This repository is itself a portable plugin package. Download a release ZIP or clone the repository, then use the plugin installation flow supported by your client. The package points to the hosted MCP service; it does not run the private Xmanmobi backend locally.

## Example prompts

```text
Use Xmanmobi to analyze my Google Ads performance for the last 7 days and list campaigns that need attention.
```

```text
Compare my Google and Facebook advertising performance this month.
```

```text
Analyze my Google Ads search terms for the last 30 days and identify converting terms and possible negative keywords.
```

```text
Check my advertising data quality and identify stale synchronization or missing conversion values.
```

More examples are available in [docs/examples.md](docs/examples.md).

## Available tools

| Tool | Purpose |
| --- | --- |
| `list_customers` | List customers available to the connected user |
| `list_delivery_projects` | List authorized delivery projects |
| `list_products` | List products in the authorized scope |
| `list_ad_accounts` | List connected Google and Meta ad accounts |
| `get_ad_overview` | Summarize advertising KPIs |
| `get_campaign_performance` | Analyze campaign performance |
| `get_ad_group_performance` | Analyze ad group or ad set performance |
| `get_ad_performance` | Analyze individual ad performance |
| `get_google_keyword_performance` | Analyze Google keyword performance |
| `analyze_google_search_terms` | Analyze Google search terms |
| `analyze_ad_creatives` | Analyze creative results and metadata |
| `analyze_conversion_funnel` | Review the conversion funnel |
| `compare_ad_periods` | Compare two reporting periods |
| `diagnose_ad_campaigns` | Diagnose campaign performance |
| `check_data_quality` | Check bindings, freshness, and missing values |

## Repository scope

This public repository contains:

- Plugin and MCP manifests.
- The onboarding skill.
- Public documentation and examples.
- Brand assets used by the plugin listing.

The hosted service implementation, database schema, customer data, credentials, and internal deployment configuration are intentionally not included.

## Privacy and security

- OAuth is used for user authorization.
- Tool results are restricted to customers assigned to the connected Xmanmobi account.
- The public tools are read-only.
- Do not report vulnerabilities in public issues. Follow [SECURITY.md](SECURITY.md).

See the [Privacy Policy](https://ai.xmanmobi.com/mcp-privacy.html) and [Terms of Service](https://ai.xmanmobi.com/mcp-terms.html).

## License

The files in this repository are available under the [MIT License](LICENSE). Use of the hosted Xmanmobi service remains subject to the Xmanmobi Terms of Service.
