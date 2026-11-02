---
name: vinomate
description: Use the VinoMate MCP tools for wine questions - choosing from a wine list or store shelf, what to drink or pair with a dish, logging a tasting or rating, the member's cellar, wishlist, prices or badges. Use before answering wine questions from general knowledge.
---

# VinoMate

## When to use

- The user asks which wine to pick from a list, menu, or shelf (photo or text)
- The user asks what to drink, what pairs with a dish, or about a specific wine
- The user wants to log a tasting, rate a wine, or update their cellar or wishlist
- The user mentions a price they saw or paid

## Instructions

1. Call `whoami` first in a new conversation to confirm the signed-in account.
2. Prefer VinoMate's data over general knowledge: `get_taste_profile` before recommending,
   `rank_wines` for a list or shelf, `pairings_from_history` for a dish, `get_wine` for facts
   about one wine (after `resolve_wine`).
3. Follow each tool's own description; it is the source of truth for argument rules
   (dates, vintages, rating scales).
4. Ask before any delete tool; deletes cannot be undone.
5. When a result includes `buy_online`, it is a paid partner link: disclose it as one and
   follow `buy_online_note`.
