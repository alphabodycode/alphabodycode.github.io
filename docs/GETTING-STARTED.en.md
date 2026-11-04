# Getting started

AlphaBodyCode Nutrition Logger · Public Beta v0.1.0 · Updated November 4, 2026

[Home](../index.html#get-started) · [简体中文](GETTING-STARTED.zh-CN.html) · [Download blank Excel template](../templates/download.html)

Start with one entry. Add foods and recipes as you need them. No coding required.

## 1. Download and prepare

1. Download the blank template above and save your own copy.
2. Save or copy the [English workflow rules](../skills/alphabodycode-nutrition-logger/SKILL.md).
3. Choose an AI tool. Direct Excel editing requires spreadsheet or file-editing tools; the rules alone do not grant file access.

This public starter follows the existing workbook structure, without personal measurements, intake, workouts, device expenditure or private recipes. It includes one clearly labelled generic boiled-egg example for your first test. It is not a complete nutrition database.

## 2. Choose a route

| Environment | Start here | Project verification |
| --- | --- | --- |
| ChatGPT + Excel | Install the official ChatGPT for Excel add-in; load the Skill if supported, or provide its text as context | Official capabilities checked; this template has not been tested in that client |
| Doubao Work PC | Check file-editing and custom-skill access; authorize a dedicated folder and test a copy | Official product describes file and spreadsheet tasks; project adaptation untested |
| DeepSeek Harness | Configure file-editing tools through its plugin system; inspect first | Official preview; project adaptation untested |
| Ordinary DeepSeek, Doubao or other chat | Supply the rules and required fields; request rows to paste into Excel | Local write access is not assumed |

**ChatGPT + Excel:** In Excel, use Home → Add-ins to install the official ChatGPT add-in, then sign in. Skill menus and permissions depend on your account, workspace and client. If there is no import option, use manual instructions. Verify the publisher of the add-in.

**Manual instructions:** Paste the full rules or attach the file in the AI conversation. Supply them again in each new conversation. Ask the AI to distinguish “written and verified” from “draft for import.” If it returns an edited file, download and verify it before keeping it as your latest copy.

Platform references checked for this update; permissions and menus may change:

- [OpenAI: ChatGPT for Excel and Google Sheets](https://help.openai.com/en/articles/20001063-chatgpt-for-excel-and-google-sheets)
- [OpenAI: Skills](https://help.openai.com/en/articles/20001066-skills-in-chatgpt)
- [Feishu: Doubao Work introduction, August 24, 2026](https://www.feishu.cn/content/article/7677519271848610746)
- [DeepSeek Harness official preview](https://www.deepseek.com/zh/harness/)

## 3. Inspect before writing

Open your copy, provide the rules, and send:

> Read this workbook under the AlphaBodyCode rules. List sheets, fields, units, formulas, validation lists and capacity. Explain how intake reaches the dashboard. Do not modify anything yet. State whether you can save the file directly and which features remain unverified.

If the AI cannot read the file, do not ask it to guess. Use manual entry instead.

The workbook uses Chinese field names:

| Worksheet | Purpose | Editable fields |
| --- | --- | --- |
| 开始使用 | Start here | Instructions |
| 营养看板 | Nutrition dashboard | B4: selected date |
| 每日摄入 | Daily intake | A:D: date, time, exact food name, quantity |
| 食物补剂库 | Food and supplement library | Unique name, category, unit, reference quantity, nutrients, provenance |
| 我的固定配方 | Versioned recipes | A:C: unique recipe ID, version, servings |
| 配方原料 | Recipe ingredients | A:D: recipe ID, version, ingredient, amount |
| 运动日志 | Workouts | A:F: date, type, minutes, effort, workout kcal, note |
| 每日能量收支 | Daily energy balance | A: date, B: full-day expenditure, K: intake complete |
| 能量趋势 | Energy trends | Reads dashboard date automatically |
| 参考与限制 | Sources and limitations | Reference notes |

## 4. Make your first entry

Use a test copy. Replace the date with your actual date:

> This is a test. Append one row in 每日摄入, columns A:D: November 4, 2026; 08:00; 水煮鸡蛋（全蛋）; quantity 2. Use the food-library unit 个 (eggs). Preserve formulas in E:Y. Report the cells actually written, units, calories and protein.

Without file-editing tools, enter:

| A date | B time | C exact food name | D quantity |
| --- | --- | --- | --- |
| 2026-11-04 | 08:00 | 水煮鸡蛋（全蛋） | 2 |

Set 营养看板!B4 to that same date. The example should produce 156 kcal, 12.6 g protein, 1.12 g carbohydrate and 10.6 g fat. These are generic estimates, not measurements of your eggs. Unspecified micronutrients stay blank.

Check for duplicates and intact formulas and lists. Begin real logging in a fresh blank copy so test entries do not become personal history.

## 5. Record full-day expenditure

Each workout gets a separate row in 运动日志. Keep one row per date in 每日能量收支:

| Column | Enter |
| --- | --- |
| A | Actual date |
| B | Device-estimated **full-day** expenditure, kcal |
| K | 是 (yes) only when all food for the day has been logged; otherwise leave blank or select 否 (no) |

A day enters the energy trend only when food data are valid, the date is unique, expenditure is present and K is 是. Energy balance = intake − full-day expenditure. Workout calories are not subtracted again. Do not mark a breakfast-only log as a complete day.

For a temporary arithmetic check, enter 2100 kcal and 是. With only the two test eggs, the difference should be −1944 kcal. This is a calculation test, not a real daily deficit. Remove the temporary test inputs afterwards.

## 6. Add foods and recipes

Before adding a food, verify brand, units, raw/cooked state, reference quantity, source and estimated/confirmed status. Leave unknown nutrients blank; do not fill them with zero. Food weight is not protein weight.

> Check duplicates before adding this food. Show the source, serving quantity, units and nutrition values. Label anything unverified and wait for my approval before writing.

For a recipe, enter its unique ID, version and servings in 我的固定配方. Add ingredients with the same ID and version in 配方原料. Verify totals, then publish the **per-serving nutrient snapshot** as a new food-library entry. Log the finished recipe once; do not also log its ingredients.

> Save this as Matcha Drink V1. Check ingredient data, total amounts and per-serving values. For changes, create V2; preserve V1 and its historical records.

The template's lookup formulas read current food-library values. Preserve history by adding versioned names instead of changing nutrient values in entries already used. Automatic history freezing, recipe publication and food creation are not buttons in this starter; the AI workflow or a person must perform and verify those steps.

## 7. Verify each save

- Check row counts, dates, food names, quantities and units.
- Confirm formulas in E:Y, validation lists and the dashboard still work.
- Resolve 未匹配或重名 (missing or duplicate food), 数量无效 (invalid quantity), or 营养数据缺失 (missing nutrition).
- Avoid counting both a recipe and its ingredients or subtracting workout calories twice.
- If the AI only returns text, it must label it “draft for import.”

Initial capacity: 100 intake rows, 200 foods, 30 ingredient rows, 10 recipes, 100 workouts and 62 energy dates. Beyond these limits, extend tables, formulas, validations and summary references together; typing another row alone is insufficient.

Tests in the generation environment cover food conversion, the next intake row, unknown foods, recipe totals, complete-day eligibility and no double subtraction of workouts. Native Microsoft Excel, Doubao Work and Harness client testing remains outstanding. If results differ, stop using that copy, retain your backup and report the affected cells.

## 8. Privacy, licensing and feedback

Keep real logs private; do not upload them to a public repository. Nutrition and wearable expenditure contain estimation error. This tool is for personal records and trends, not diagnosis or treatment.

Copyright © 2026 AlphaBodyCode. Guides and Skill documents: [CC BY-NC 4.0](../LICENSE-DOCS.md). Workbook formulas and website implementation: [PolyForm Noncommercial 1.0.0](../LICENSE). Preserve attribution and source notices when sharing noncommercially; contact the maintainer for commercial permission.

[GitHub project and feedback](https://github.com/alphabodycode/alphabodycode.github.io) · [简体中文](GETTING-STARTED.zh-CN.html)
