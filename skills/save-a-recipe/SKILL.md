---
name: save-a-recipe
description: Write a recipe into the user's Thrice library as cooklang, from a dish discussed in chat, a description, or text the user pastes. Use when the user asks to save, add or create a recipe in Thrice, or to change one they already have.
---

# Save a recipe to Thrice

1. Check the user's units first: `get_overview` returns `preferred_units` (metric or imperial). Write quantities in those units.
2. Write the recipe in cooklang:
   - Metadata lines at the top: `>> title: …`, `>> servings: 4`, `>> prep time: 15 minutes`, `>> cook time: 30 minutes`, `>> tags: weeknight, chicken`, and `>> source: <url>` when it came from a page.
   - Ingredients inline in the steps as `@name{quantity%unit}` (`@olive oil{2%tbsp}`, `@eggs{3}`). A multi-word name needs the braces even without a quantity: `@black pepper{}`.
   - Cookware as `#name{}` (`#cast iron skillet{}`), timers as `~{10%minutes}`.
   - One step per paragraph, separated by a blank line.
3. Measure the way cooks do: count whole items ("2 chicken breasts", "1 onion"), use volume for rice, flour and liquids, and weight only for things bought by weight like ground meat.
4. Save it with `create_recipe` (`cooklang`). It returns the recipe's id and a link: share the link. Thrice estimates its nutrition in the background a minute later.
5. To change an existing recipe, read it with `get_recipe`, edit the full cooklang, and send all of it back with `update_recipe`. A `cooklang` value replaces the whole recipe text.
6. Don't copy a published recipe word for word. Write it in your own words and keep the source link.
