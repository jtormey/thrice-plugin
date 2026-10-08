---
name: shop-for-the-plan
description: Build the user's Thrice shopping list from their meal plan or chosen recipes, skipping what's already in the pantry. Use when the user asks to shop for the week, add a recipe's ingredients to their list, or get ready for a grocery run.
---

# Shop for the plan

1. Find the recipes: `get_meal_plan` for the week (or the days the user names), or the recipes they mention by name via `search_recipes`.
2. Add each recipe's ingredients with `add_to_shopping_list` (`recipe_id`), one call per recipe. Thrice merges duplicates across recipes itself, by name and unit, so don't pre-combine them.
3. Check `get_pantry` and tell the user which listed items they likely already have, rather than leaving them off silently. They decide.
4. Add anything extra the user asks for as free text: `add_to_shopping_list` with `items` (`["2 lemons", "olive oil"]`).
5. Read the result back with `get_shopping_list` and summarize it by aisle. After the shop, `check_off_shopping_items` marks what they bought, and `add_pantry_items` stocks the pantry if they'd like.
