---
name: log-meals
description: Log what the user ate to their Thrice food log with macros, and report progress against their daily goal. Use when the user says what they had for a meal, asks to log food, or asks how they're doing on calories or protein today.
---

# Log meals in Thrice

1. For something they cooked from a saved recipe, find it with `search_recipes` and log it with `log_meal` (`meal`, `recipe_id`, `servings`). Thrice uses the recipe's own nutrition estimate.
2. For anything else, estimate the macros yourself and log it with `log_meal` (`meal`, `description`, `calories`, `protein`, `fat`, `carbs` in grams). If a saved recipe has no estimate yet, Thrice refuses the recipe form: log it by description instead.
3. `meal` is breakfast, lunch, dinner or snack. Use `date` (YYYY-MM-DD) when it wasn't today.
4. Say what you logged and the numbers you used, so the user can correct them. Estimates are estimates; don't present them as exact.
5. For "how am I doing", read `get_diary` (or `get_overview` for today) and answer with what's left against the goal, then one practical suggestion for the next meal. Change the goal itself with `set_macro_goal` only when the user asks.
