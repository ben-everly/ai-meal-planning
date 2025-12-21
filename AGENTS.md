# AI Meal Planning Agent Guidelines

This document outlines the requirements and constraints for the AI agents responsible for generating weekly meal plans.

- **Directory Structure:**
    - Weekly plans are stored in the `plans/` directory.
    - Internal recipes are stored in the `recipes/` directory. The `recipes/` directory must remain flat (no subdirectories).
    - **Note:** Internal recipes should ONLY be saved to the `recipes/` directory if explicitly prompted by the user. Otherwise, use inline recipes or external links.

## Meal Plan Structure

- **Duration:** Weekly (Sunday Dinner to Sunday Lunch).
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

## Dietary Restrictions & Guidelines

- **Participants:** Mom, Dad, and a 9-month-old baby.
- **Baby Specifics:**
    - **Low Sodium:** Minimal added salt.
    - **Low Sugar:** No added refined sugars.
    - **Safety:** No honey, no whole nuts (choking hazard).
    - **Allergens:** Ensure exposure to all major allergens (peanuts, tree nuts, dairy, egg, soy, wheat, fish, shellfish, sesame) at least 2 times per week.
- **Adults:** Balanced, nutritious meals that are satisfying and varied.

## Time Constraints

- **Breakfast:** Max 10 minutes prep/cook.
- **Lunch:** Max 20 minutes prep/cook.
- **Dinner:** Max 30 minutes prep/cook.
- **Wednesday Dinner:** Max 15 minutes prep/cook (High-speed requirement).
- **Sunday Prep:** Up to 2 hours allowed on Sunday afternoon for bulk prep (chopping, batch cooking, etc.).

**Note on Timing:** Agents must account for _actual_ time spent. Most recipes underestimate prep time; the constraints above refer to the total real-world time from start to finish. Choose recipes that are genuinely fast or utilize the Sunday prep session to ensure weekday meals fit these windows.

## Meal Plan Specifications

### Meal Plan File Specification

```markdown
# Meal Plan: Week of [Date]

## Sunday Prep (2-hour session)

- [ ] Task 1
- [ ] Task 2

## Weekly Snacks

- Snack 1: [Meal Specification]
- Snack 2: [Meal Specification]

## Weekly Dessert

- **Dessert:** [Meal Specification]

## Sunday

- **Dinner:** [Meal Specification]
    - _Note:_ Prep for tomorrow's lunch.

## Monday

- **Breakfast:** [Meal Specification]
- **Lunch:** [Meal Specification]
- **Dinner:** [Meal Specification]
- **Sides:** [Meal Specification]

## Tuesday

- **Breakfast:** [Meal Specification]
- **Lunch:** [Meal Specification]
- **Dinner:** [Meal Specification]

## Wednesday

- **Breakfast:** [Meal Specification]
- **Lunch:** [Meal Specification]
- **Dinner:** [Meal Specification]

## Thursday

- **Breakfast:** [Meal Specification]
- **Lunch:** [Meal Specification]
- **Dinner:** [Meal Specification]

## Friday

- **Breakfast:** [Meal Specification]
- **Lunch:** [Meal Specification]
- **Dinner:** [Meal Specification]

## Saturday

- **Breakfast:** [Meal Specification]
- **Lunch:** [Meal Specification]
- **Dinner:** [Meal Specification]

## Sunday

- **Breakfast:** [Meal Specification]
- **Lunch:** [Meal Specification]

## Shopping list

### [Ingredient Category]

- [ ] Ingredient 1
- [ ] Ingredient 2
```

### Meal Specification

Each meal in the plan must follow one of these formats:

#### 1. External Recipe Link

Use for recipes hosted on external websites.

- **Format:** `[Meal Name](https://example.com/recipe-url)`

#### 2. Internal Recipe Link

Use for recipes stored within this repository.

- **Format:** `[Meal Name](../../recipes/recipe-file.md)`

#### 3. Inline Recipe

Use for simple meals or when a quick reference is better than a separate file. Must include ingredients and preparation steps.

- **Format:**
    ```markdown
    - **Dinner:** Meal Name
        - **Ingredients:**
            - Ingredient 1
            - Ingredient 2
        - **Preparation:**
            1. Step 1
            2. Step 2
    ```

#### 4. Leftovers

Explicitly state which meal the leftovers are from.

- **Format:** `(Leftovers from [Day] [Meal])`

#### 5. Eating Out

Indicate that the meal will be eaten out.

- **Format:** `(Eat Out)`

## Agent Instructions for Selection

1. **Prioritize Seasonality:** Use ingredients that are in season.
2. **Minimize Waste:** Ensure ingredients bought for one meal are utilized in others or can be stored.
3. **Consistency:** Ensure the markdown structure remains consistent for easy parsing.
