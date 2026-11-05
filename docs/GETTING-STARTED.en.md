# Getting started

AlphaBodyCode Nutrition Logger · Public Beta v0.3.0 · Updated November 5, 2026

[Home](../index.html#get-started) · [简体中文](GETTING-STARTED.zh-CN.html) · [Download blank Excel template](../templates/download.html)

Start with one entry. Add foods and recipes as you need them. No coding required.

## 1. Download and prepare

1. Download the blank template above and save your own copy.
2. Save or copy the [English workflow rules](https://github.com/alphabodycode/alphabodycode.github.io/blob/main/skills/alphabodycode-nutrition-logger/SKILL.md).
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
| 营养看板 | Nutrition dashboard | B3: selected date |
| 个人参数 | Personal profile | Actual red input cells; separate fictional examples |
| 配方快照 | Published recipes | Values-only copies; preserve old version IDs |
| 每日归档 | Archived days | 18 values-only nutrient rows per date |
| 营养参考规则 | Adult reference rules | Fixed sources and version |
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

> This is a test. Append one row in 每日摄入, columns A:D: November 5, 2026; 08:00; 示例_水煮鸡蛋（全蛋）; quantity 2. Use the food-library unit 个 (eggs). Preserve formulas in E:AD. Report the cells actually written, units, calories and protein.

Without file-editing tools, enter:

| A date | B time | C exact food name | D quantity |
| --- | --- | --- | --- |
| 2026-11-04 | 08:00 | 示例_水煮鸡蛋（全蛋） | 2 |

First enter that date in 每日能量收支!A4, leaving expenditure and completion blank; then select it in 营养看板!B3. The example should produce 156 kcal, 12.6 g protein, 1.12 g carbohydrate and 10.6 g fat. These are generic estimates, not measurements of your eggs. Unknown source nutrients stay blank; intake cells show 未知 (unknown), and the dashboard reports known subtotals with missing-data status.

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

For a recipe, enter ID, version and batch servings in 我的固定配方; add its ingredients in 配方原料. Verify totals, then copy that recipe row **A:AB as values into the same columns in 配方快照; also copy AD:AW as values into AD:AW**. Do not copy the AC selection list. Nutrients are known subtotals for the whole batch; C stores batch servings. AD:AW preserves missing-data status. Unknown values must not be invented as zero.

In 每日摄入, select the published recipe ID directly in C and enter consumed servings in D. Do not republish it as a food or also log its ingredients. The generic 示例_双鸡蛋_v1 recipe gives 156 kcal and 12.6g protein per serving. Create a new version for ingredient or serving changes; preserve the previous published ID.

**Personal references:** Enter age, physiological sex and life stage to match Chinese CNS DRIs2023 core references. Height/weight are separate inputs for metabolism and training. Women aged 50–64 must state menstrual status for iron RNI; do not infer it from age. Select low/middle/high PAL, then explicitly adopt the population EER or enter a confirmed positive energy target before macro gram ranges appear. Protein RNI, AMDR and UL remain distinct. Training goals are shown separately below the dashboard. Coverage is adults18+, pregnancy by trimester/lactation18–49; children are not yet supported. Existing archives retain their original standards and targets.

**Preserve history:** After checking a day, copy **营养看板!J10:AC27, 18 rows by 20 columns, as values only** into 每日归档!A:T. Start at A4; for later days add 18 rows within the DailyArchive Excel table and extend its U validation formulas. Each date needs exactly one row for each of the 18 nutrients. Archived totals, missing-data status, personal parameters, targets and rule version remain static when current food/profile data change.

Pasting formulas does not freeze history. U validates fields and cannot replace the values-only paste operation. Unarchived dates continue to read current food data. AI connection, publication and archiving require your AI tool or manual action; they are not automatic buttons.

## 7. Verify each save

- Check row counts, dates, food names, quantities and units.
- Confirm formulas in E:AD, validation lists and the dashboard still work.
- Resolve 未匹配或重名 (missing or duplicate food), 数量无效 (invalid quantity), or 营养数据缺失 (missing nutrition).
- Avoid counting both a recipe and its ingredients or subtracting workout calories twice.
- If the AI only returns text, it must label it “draft for import.”

Initial capacity: 999 intake rows, 199 foods, 100 ingredient rows, 200 recipe versions, 199 workouts and 431 energy dates. The archive is an expandable Excel table: add 18 rows per day and extend validation formulas. Beyond other limits, extend tables, formulas, lists and summary references together.

Generation-environment checks cover direct recipe servings, demographic rules, missing data, complete-day eligibility, historical snapshots and trend dates beyond the old row 104 limit. Native Microsoft Excel, Doubao Work and Harness client testing remains outstanding. If results differ, stop using that copy, retain your backup and report the affected cells.

## 8. Privacy, licensing and feedback

Keep real logs private; do not upload them to a public repository. Nutrition and wearable expenditure contain estimation error. This tool is for personal records and trends, not diagnosis or treatment.

Copyright © 2026 AlphaBodyCode. Guides and Skill documents: [CC BY-NC 4.0](../LICENSE-DOCS.md). Workbook formulas and website implementation: [PolyForm Noncommercial 1.0.0](../LICENSE). Preserve attribution and source notices when sharing noncommercially; contact the maintainer for commercial permission.

[GitHub project and feedback](https://github.com/alphabodycode/alphabodycode.github.io) · [简体中文](GETTING-STARTED.zh-CN.html)
