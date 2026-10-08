---
name: cook-from-pantry
description: Suggest what the user can cook now with what's in their Thrice pantry, from their saved recipes first and new ideas second, using up what expires soonest. Use when the user asks what to make tonight, what they can cook with what they have, or how to use something up.
---

# Cook from the pantry

1. Read `get_pantry`: what's on hand by category, plus what expires in the next three days.
2. Read candidates with `search_recipes`, then `get_recipe` for the most promising few. Compare ingredient names yourself: pantry staples like salt, oil and spices count as on hand unless the pantry is clearly sparse.
3. Lead with saved recipes the user can make now or nearly (missing one or two things), and say exactly what's missing. Favor ones that use what expires soonest.
4. Then offer one or two new ideas that use the same ingredients. If the user picks one, save it with the save-a-recipe skill.
5. Offer the next step: add the missing items to the shopping list (`add_to_shopping_list` with `items`), plan it for tonight (`plan_meal`), or record the cook afterwards (`record_cook`).
