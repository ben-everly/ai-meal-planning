# AI Meal Planning Agent Guidelines

This document outlines the requirements and constraints for the AI agents responsible for generating weekly meal plans.

- **Directory Structure:**
    - Weekly plans are stored in the `plans/` directory.
    - Internal recipes are stored in the `recipes/` directory. The `recipes/` directory must remain flat (no subdirectories).
    - **Note:** Internal recipes should ONLY be saved to the `recipes/` directory if explicitly prompted by the user. Otherwise, use inline recipes or external links.

## Meal Plan Structure

- **Duration:** Weekly (Monday Breakfast to Sunday Dinner).
- **Format:** Markdown file per week.
- **Logistics:**
    - Shopping is done Sunday afternoon; agents should prioritize ingredient freshness when planning meals for later in the week.
- **Daily Meals:** Breakfast, Lunch, Dinner, and Sides (if applicable).
- **Snacks:** 2-3 snack options available for the week.
- **Dessert:** 1 dessert option available for the week for adults to enjoy at their discretion.
- **Shopping List:** Each meal plan must include a consolidated shopping list of all ingredients needed for the week.
- **Eating Out:**
    - Breakfast: ~1 time/week.
    - Lunch: ~1 time/week.
    - Dinner: ~1-2 times/week.
- **Leftovers:** The plan must explicitly account for leftovers (e.g., using Sunday dinner for Monday lunch).
- **Leftover Variety:** When using leftovers, prefer some variation (e.g., repurposing roast chicken into chicken salad).

## Dietary Restrictions & Guidelines

- **Participants:** Mom, Dad, and a 9-month-old baby.
- **Baby Specifics:**
    - **Low Sodium:** Minimal added salt.
    - **Low Sugar:** No added refined sugars.
    - **Safety:** No honey, No milk, no whole nuts (choking hazard).
    - **Allergens:** Ensure exposure to all major allergens (peanuts, tree nuts, dairy, egg, soy, wheat, fish, shellfish, sesame) at least 2 times per week.
- **Adults:** Balanced, nutritious meals that are satisfying and varied.

## Time Constraints

- **Breakfast:** Max 10 minutes prep/cook.
- **Lunch:** Max 20 minutes prep/cook.
- **Dinner:** Max 30 minutes prep/cook.
- **Wednesday Dinner:** Max 15 minutes prep/cook (High-speed requirement).
- **Sunday Prep:** Up to 2 hours allowed on Sunday afternoon for bulk prep (chopping, batch cooking, etc.).

**Note on Timing:** Agents must account for _actual_ time spent. Most recipes underestimate prep time; the constraints above refer to the total real-world time from start to finish. Choose recipes that are genuinely fast or utilize the Sunday prep session to ensure weekday meals fit these windows.

## Format Specifications

### Document Schema

The meal plan is a Markdown document with the following structure. `[]` indicates optional and `<>` indicates a placeholder to be filled in. `#` is a comment and should not appear in the final output:

```markdown
# Meal Plan: Week of <YYYY-MM-DD>

## Sunday Prep (2-hour session)

<Checklist>

## Weekly Highlights

<Meal Entry> #snack
<Meal Entry> #snack
[<Meal Entry> #snack]
<Meal Entry> #dessert

## Daily Meals

<Day Plan> #Monday

<Day Plan> #Tuesday

<Day Plan> #Wednesday

<Day Plan> #Thursday

<Day Plan> #Friday

<Day Plan> #Saturday

<Day Plan> #Sunday

## Shopping List

[### Produce
<Checklist>]

[### Dairy
<Checklist>]

[### Meat
<Checklist>]

[### Pantry
<Checklist>]

[### Other
<Checklist>]
```

### Day Plan

```Markdown
## <Day of the Week>
[<Meal Entry> #breakfast]
[<Meal Entry> #lunch]
[<Meal Entry> #dinner]
```

### `<Meal Entry>`

```Markdown
**<Meal Type>:** <Meal>
    [- **Side**: <Meal>]
    [- _Note:_ <Optional Note>]
```

### `<Meal Type>`

One of:

- `Breakfast`
- `Lunch`
- `Dinner`
- `Snack <#>`
- `Dessert`

### `<Meal>`

- **External Link:** `[Meal Name](URL)`
- **Internal Link:** `[Meal Name](../../recipes/filename.md)`
- **Leftovers:** `(Leftovers from [Day] [Meal])`
- **Eating Out:** `(Eat Out)`
- **Inline Recipe:**
    ```markdown
    - <Recipe Name>
        - **Ingredients:**
            <Checklist>
        - **Preparation:**
            <Preparation Steps>
    ```

### `<Checklist>`

A list of items using the Markdown checkbox syntax:

```
- [ ] <Item Name>
[- [ ] <Item Name>
[...]]
```

### `<Preparation Steps>`

```
1. <Instruction Step>
[2. <Instruction Step>
[...]]
```

## Agent Instructions for Selection

1. **Variety:** Check the previous two meal plans in the `plans/` directory to ensure meals and ingredients are varied and not repetitive.
2. **Prioritize Seasonality:** Prioritize ingredients that are in season.
3. **Minimize Waste:** Ensure ingredients bought for one meal are utilized in others or can be stored.
4. **Consistency:** Ensure the markdown structure remains consistent for easy parsing.
5. **Food Longevity:** Consider the shelf life of store-bought ingredients (prioritizing perishable items earlier in the week) and ensure leftovers are scheduled to be consumed while still fresh.
