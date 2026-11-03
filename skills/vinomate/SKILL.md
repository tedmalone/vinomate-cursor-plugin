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
- The user shares a photo of a wine list, a shelf, or a bottle's label

## Instructions

1. Call `whoami` first in a new conversation to confirm the signed-in account. When it says
   NEW MEMBER, follow the welcome in the server's instructions instead of listing tools.
2. Prefer VinoMate's data over general knowledge: `get_taste_profile` before recommending,
   `rank_wines` for a list or shelf, `pairings_from_history` for a dish, `get_wine` for facts
   about one wine (after `resolve_wine`).
3. A photo of a list or shelf needs no questions first: rank everything on it with one
   `rank_wines` call, name one bottle and say why, then record prices afterwards.
4. Follow each tool's own description and the server's instructions; they are the source of
   truth for argument rules (dates, vintages, rating scales) and override this skill.
5. Never send VinoMate anything about the member's health (allergies, medications, reactions).
6. Ask before any delete tool; deletes cannot be undone.
7. When a result includes `buy_online`, it is a paid partner link: disclose it as one and
   follow `buy_online_note`.
