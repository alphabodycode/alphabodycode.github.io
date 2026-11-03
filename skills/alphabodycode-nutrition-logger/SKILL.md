---
name: alphabodycode-nutrition-logger
description: Record food, supplements, workouts and wearable-estimated energy expenditure in a user-authorized nutrition workbook using natural language. Use when the user wants to log meals, look up new food nutrition, assemble a one-off recipe, create a versioned recurring recipe, or review daily energy and nutrient intake. Preserve history, label estimates, verify workbook capabilities and never invent nutrition facts.
---

# AlphaBodyCode Nutrition Logger — Public Beta v0.1.0

## Scope and prerequisites

Operate on a workbook the user owns and has explicitly opened or authorized. This skill contains **instructions only**; it does not itself connect to Excel, retrieve WHOOP data, provide a nutrition database API, or execute spreadsheet writes. Before claiming that a record was saved, use an available spreadsheet-editing tool and verify the changed cells. If no editing capability is available, return a structured, ready-to-import draft rather than claiming success.

Never assume the user's workbook matches one specific private AlphaBodyCode file. Inspect sheet names, field mappings, units, validation rules, formulas, tables and naming conventions first. Obtain consent before structural changes, and work on a backed-up copy.

## Workflow

1. **Parse the request.** Extract the actual date, time (may be unknown), foods or ingredients, quantity, unit, brand, preparation method and whether the user wishes to log, research or save a recipe. Use the user's specified date, not an inferred date when ambiguous.
2. **Match before adding.** Search the workbook's food library and aliases. Match exact brands, preparation state and units. Never silently equate raw and cooked foods, different supplement products, or oatmeal with oat flour.
3. **Research missing food data.** Prefer manufacturer nutrition labels for branded foods and supplements; otherwise use authoritative food-composition data with documented provenance. Record the source and whether values are direct, derived or approximated. If live verification is unavailable, say so. Unknown is *not* zero. Ask only for essential missing information.
4. **Plan workbook edits.** Preview any new food-library entry with its unit, reference serving, nutrients, source, estimated/confirmed status, and duplicate check. Get approval before adding an unverified new entry. For routine known-food entries, batch writes when authorized.
5. **Record meals.** Append rows without overwriting existing records. Check likely duplicates using date, time, food and quantity. Preserve formulas, lists and formatting; verify that lookups, daily summary, and nutrient completeness update. Use zero only when positively established.
6. **Build temporary recipes.** For an ad hoc drink or mixed meal, create a unique record and itemized ingredient amounts. Calculate nutrient totals by ingredient, with unit conversion and proper serving quantities. Log the complete recipe as one meal entry and never also count its component ingredients separately. Store a dated composition and nutrition snapshot so history stays stable.
7. **Publish recurring recipes only on request.** Assign stable IDs and versions (V1, V2, ...). Never edit a published or history-locked version; duplicate into a new version and apply changes there. Verify both recipe totals and historical references.
8. **Log exercise and wearable estimates.** Each workout gets a distinct row; aggregate sessions by date. Record a wearable's full-day estimated expenditure separately. Daily estimated energy balance = food energy intake − wearable-estimated full-day energy expenditure. Do **not** subtract workout calories again. Treat partial-day, missing and incomplete days as distinct states.
9. **Validate and report.** Compare record counts before/after, test edited rows, check broken lookups and formula errors, and explicitly name unverified results. Give a concise summary of what was actually saved, what awaits confirmation, and whether dashboard calculations refreshed.

## Non-negotiable safeguards

- Protect private nutrition, medical and activity logs. Do not publish any user's workbook, real logs or proprietary product labels to a public repository without express permission.
- Nutrient intake is not equivalent to absorption or blood status. Wearable calories are estimates; do not claim a precise energy deficit, fat loss, disease prevention or diagnosis.
- Flag potentially overlapping supplement products or unusually high doses for professional review without making diagnoses.
- Never invent sources, records, completed actions, successful writes, device connections or supported features.
- If the workbook schema is incompatible, stop and explain the proposed safe migration before editing.

## Example prompts

- “记录11月2日早餐：贝果1个，牛油果90克，咖啡250毫升。”
- “新增蒸南瓜到食物库，先展示来源和每100克营养数据。”
- “今天11点喝了牛奶250毫升、蛋白粉10克、胶原蛋白5克和抹茶3克，作为一次性饮品记录。”
- “把刚才的饮品保存为抹茶拿铁V1；V1历史数据不要修改。”
- “今天两场运动各45分钟和30分钟，WHOOP全天估算消耗2100千卡，检查能量收支。”
