# AlphaBodyCode v0.3.0 workbook contract

Read this reference before matching nutrient targets, changing personal parameters, publishing recipes, or archiving a day. Inspect the actual workbook first; older versions may have different columns. Use the bundled `cns2023.json` to verify supported reference rows, not as a replacement for the user's workbook.

## Chinese reference matching

- Use 中国营养学会《中国居民膳食营养素参考摄入量（2023版）》. Coverage is adults 18+, with separate 18–29, 30–49, 50–64, 65–74 and 75+ groups, and pregnancy by trimester/lactation for ages 18–49. Do not apply adult rules to children. The implementation covers the workbook's core nutrients; it is not the full 70+ nutrient database.
- Match age, physiological sex, and life stage. Do not assume pregnancy, lactation, menopause, smoking status or menstrual loss. For women aged 50–64, iron RNI requires `有月经` or `无月经`; `绝经后` maps to no menstruation. Missing this input leaves iron's suggested amount unassigned while other references remain available.
- Read `个人参数!B3` age, B4 height, B5 weight, B6 sex, B8 stage. B7 is a formula. Manual fields are red; illustrative red text in column C never feeds calculations. Height, weight and smoking must not block demographic RNI matching. Height and weight are needed for the separate adult basal-metabolic estimate, not for assigning calcium RNI.
- Use `营养参考规则` as the active source. It contains exact official table URLs, units, source edition, reference types and match flags. Do not silently combine CNS RNI with NIH UL or add the US smoker vitamin-C adjustment. Chinese magnesium UL is unassigned; do not carry over 350 mg as a Chinese total-magnesium limit.
- Preserve RNI, AI, AMDR, EER and UL as different types. RNI/AI are population references, not a diagnosis of deficiency. AMDR high values are not UL. No UL does not mean unlimited intake is safe.
- Protein RNI is a separate value from its AMDR grams. Calculate carbohydrate/protein AMDR grams = confirmed energy × energy fraction ÷ 4. Fat grams = confirmed energy × fraction ÷ 9. Read the fractions from the matched source group; protein is 15–20% at 65+ versus 10–20% at 18–64. Do not encode all adult groups as one fixed protein range.
- `个人参数!B28` selects low/middle/high PAL category. B29 displays population EER from the official table, converted MJ × 1000 / 4.184. B30 explicitly adopts this reference; B31 is an optional positive user-confirmed energy target which takes precedence. B32 is the effective energy for AMDR grams. Never use basal metabolism as intake target. Missing/unsupported PAL or unconfirmed energy leaves gram ranges blank, while RNI/AI remain visible.
- Official older-adult tables do not supply high-PAL EER. Leave it unassigned rather than extrapolate. EER is a population estimate; individual goals need review against body size, activity and longitudinal records. Do not auto-create a caloric deficit for pregnancy or children.
- Ordinary adult EPA+DHA AMDR is 250–2000 mg/day, not a safety UL. Pregnancy/lactation AI is 250 mg/day with DHA 200 mg/day. The workbook stores only combined EPA+DHA; report that DHA adequacy cannot be checked from that total. Do not manufacture uniform Chinese targets for caffeine, CoQ10, theanine, curcumin, creatine or collagen.
- Preserve the personal training presets at `个人参数!A14:I19`. `G7=确认采用`, known day type and positive body weight enable the separate training panel `营养看板!A61:I68`. They do not overwrite the Chinese baseline references.

## Recording and completeness

- Preserve all 17 sheets and the original chain: 食物补剂库 → 配方原料 → 我的固定配方 → 配方快照 → 每日摄入 → 营养看板; 个人参数/营养参考规则 supply targets; 运动日志/每日能量收支 supply activity and full-day comparison; 每日归档 preserves history.
- Append daily intake inputs to A:D only: date, time, selected food/published recipe, quantity. E:AW contains lookup/results/completeness fields. Inspect capacities and expand tables, formulas, lists and named ranges together when needed. Never overwrite these formulas with a prose response or pasted totals.
- Match exact brand, raw/cooked state, serving unit and reference quantity. Unknown nutrients remain blank or marked unknown; zero requires evidence. A recipe with one known and one unknown calcium contribution retains its known subtotal AND a missing flag, so a known excess can still be flagged.
- Food rows use per-nutrient known flags; daily AF:AW contains missing flags. A successful food match does not mean the entire day's nutrition is complete.
- `每日能量收支!K` is the user's `全天饮食已记全` confirmation. Never infer `是` from a breakfast entry, absent later meals, a matched food name, or an AI-generated summary. Record wearable full-day expenditure in B. Workout expenditure is already included in full-day expenditure and must not be subtracted again. L is explicit day type/rest confirmation; no workout entry does not imply a rest day.
- Daily comparison requires full-day confirmation, valid expenditure, at least one intake item, no unresolved macro item and a unique day row. Incomplete days show known subtotals, and are excluded from complete-day energy averages. Unknown micronutrients prevent an adequacy claim even if macros are complete. A known amount exceeding an applicable upper value is still flagged before completeness evaluation.

## Frozen recipes and days

- Publish a recurring recipe only when requested. Assign stable ID/version; create a new version for changed ingredients or servings. Copy the selected `我的固定配方` A:AB row as VALUES to `配方快照` A:AB and AD:AW as VALUES to AD:AW. Do not copy the AC chooser list. Keep supplement-magnesium provenance and completeness fields. Never log both recipe and ingredients for the same consumption.
- Archive a day only when requested or part of an explicitly authorized routine. Copy `营养看板!J10:AC27` as VALUES into 18 appended rows of `每日归档!A:T`; extend the table and U validation formula. Do not paste formulas. Each date must contain exactly one row for each of the 18 nutrient names with valid metadata. Read back the frozen values.
- The snapshot includes goals, upper values, age/sex/stage/weight, standard/version, reference types, training metadata, completeness and expenditure. Do not change previous snapshots when updating the profile or standards. Main dashboard rows use archived values for a fully valid archive; the lower reference/training panels are labelled CURRENT parameters.
- This release changes live/unarchived references to CNS2023. Existing NIH-labelled archives keep their original values and scope. Do not relabel an NIH snapshot as Chinese data or retroactively fill a historic target from today's profile.

## Verification and reporting

- Verify edited rows, lookup resolution, counts, units, missing flags and dependent results. Test representative changes if modifying formulas. Report actual saved changes separately from a draft or unsupported action.
- Skill instructions do not provide an Excel connection or prove Excel-client compatibility. Only claim a save after an editing tool succeeds and affected cells are checked. Without an editor, give a ready-to-import draft and state it was not saved.
- Do not publish real user parameters, food/activity logs or medical details in a public template. Keep only explicitly labelled generic examples in public copies.

Copyright © 2026 AlphaBodyCode. CC BY-NC 4.0. Official numerical references remain attributed to the Chinese Nutrition Society.
