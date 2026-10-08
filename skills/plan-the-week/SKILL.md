---
name: plan-the-week
description: Plan the user's meals for a week in Thrice from their own saved recipes, fitted to their macro goal, what's in their pantry and what they've cooked lately. Use when the user asks to plan the week, fill in dinners, or build a meal plan.
---

# Plan the week in Thrice

1. Start with `get_overview` for the user's macro goal, units and what's already planned. Read the week with `get_meal_plan` (pass any day of that week as `date`); its notes often say what the user wants ("quick dinners", "out Thursday").
2. Gather candidates: `search_recipes` (filter by `tag`, `cuisine` or `favorited`), `get_pantry` for what's on hand and what expires soon, and `get_cook_history` so you don't repeat last week.
3. Propose the plan before writing it: one line per meal with the recipe, why it fits (protein, uses the spinach before it turns, 25 minutes), and rough day totals against the goal. Leave days the user said they're out.
4. Once the user agrees, put each recipe in its slot with `plan_meal` (`date`, `meal`, `recipe_id`, optional `servings`). The first recipe in a slot is the main and later ones are its sides, so add the main first. Use `replace: true` only when the user asked to swap what's there.
5. If a dish they want isn't saved yet, write it with the save-a-recipe skill first, then plan it.
6. Finish with what was planned, and offer to add the missing ingredients to the shopping list (the shop-for-the-plan skill).
