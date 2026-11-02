# VinoMate for Cursor

VinoMate is an AI sommelier that lives inside your AI assistant. This plugin connects Cursor to
the VinoMate MCP server so the agent can answer wine questions from your own tasting history,
taste profile, and cellar, backed by VinoMate's wine catalogue, instead of guessing.

Learn more at [vinomate.ai](https://vinomate.ai).

## What it does

The plugin adds one remote MCP server (`vinomate`, shown in Cursor as `plugin-vinomate-vinomate`)
and one small skill that tells the agent when to use it.

| Area | What you can ask | Main tools |
| --- | --- | --- |
| Taste profile | "What do I like?" "What's my favorite Chardonnay?" | `get_taste_profile`, `get_preferences`, `set_preferences`, `start_taste_survey` |
| Wine list or shelf | Paste or photograph a list: "Which one should I get?" | `rank_wines` |
| Tastings and ratings | "Log the Ridge Zin, 92, great with the burger" | `log_tasting`, `rate_wine`, `update_tasting`, `get_tasting_history`, `get_ratings` |
| Cellar and wishlist | "Add 6 bottles to my cellar." "What should I drink soon?" | `add_to_cellar`, `get_cellar`, `log_drink`, `drink_soon`, `add_to_wishlist`, `get_wishlist` |
| Wine facts | Producer, region, grapes, critic scores, vintages | `resolve_wine`, `get_wine`, `compare_vintages` |
| Recommendations | "Something new under $25?" (critic-based for new members) | `recommend_wines` |
| Pairings | "What goes with lasagna tonight?" (from your own history) | `pairings_from_history` |
| Prices | Report a shelf tag, menu line, or receipt | `report_price`, `report_prices`, `get_price_reports` |
| Buy online | "Find me a red I can order" | `shop_online` |
| Badges | Badges for tasting, noting, and price scouting | `get_badges`, `share_badge` |
| Account | Connected apps, sign out, privacy requests | `whoami`, `list_connected_apps`, `disconnect_app`, `sign_out`, `request_account_deletion` |

### Partner links

`shop_online` (and some `get_wine` / `recommend_wines` results) can include a `buy_online` link
to a VinoMate retail partner (currently Wine.com, shipping within the US). **These are paid
affiliate links**: VinoMate may earn a commission if you buy. Per VinoMate's tool rules, the agent
discloses them as paid links, and the link never changes which wines are picked or their order.
Price and stock are on the partner's page.

## Setup

1. Install the plugin from the Cursor Marketplace.
2. The first time the agent calls a VinoMate tool, Cursor opens a sign-in page. Sign in to
   VinoMate and approve access.
3. Ask a wine question. The agent calls `whoami` first to confirm your account.

There are no API keys, environment variables, or plugin variables to configure.

### Authentication details

- Server: `https://mcp.vinomate.ai/mcp` (Streamable HTTP)
- OAuth 2.0 authorization code flow with PKCE (S256) and dynamic client registration; Cursor
  registers itself as a public client
- Protected resource metadata: `https://mcp.vinomate.ai/.well-known/oauth-protected-resource/mcp`
- Scopes: `taste:read`, `cellar:read`, `cellar:write`, `history:read`

To sign out, ask the agent to "sign out of VinoMate" (`sign_out`), or remove the sign-in for the
server under Customize in Cursor.

## Privacy

- VinoMate stores what you ask the agent to record: ratings, tasting notes, reviews, cellar and
  wishlist entries, and prices you report.
- Reported prices are kept in your own log. Whether they also go into VinoMate's anonymous,
  aggregated price data depends on your price-sharing setting (`whoami` shows it,
  `set_price_sharing` changes it).
- VinoMate's tools are designed not to record health information (allergies, medications,
  reactions).
- To get a copy of your data, correct it, or delete your account, ask the agent; it calls
  `request_account_deletion`, which gives you VinoMate's request page.
- Delete tools (tastings, ratings, cellar, prices) cannot be undone. The agent should ask first, and
  Cursor asks you to approve MCP tool calls by default.

Full policy: [Privacy Policy](https://vinomate.ai/privacy) and
[Connector Terms](https://vinomate.ai/terms).

## Support

TODO: add a support contact (email or URL).

## License

TODO: choose a license and add a `LICENSE` file and a `license` field in `.cursor-plugin/plugin.json`.
