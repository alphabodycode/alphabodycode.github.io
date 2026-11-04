# AlphaBodyCode Nutrition Logger

**用自然语言记录饮食，用长期数据理解自己。**

AlphaBodyCode Nutrition Logger 是一份面向主动健康管理者的开放式 AI 工作流程（Public Beta），用于协助维护个人营养 Excel 工作簿：食物/补剂检索、饮食记录、临时饮品配方、固定配方版本、运动日志、可穿戴设备估算热量与能量收支。

> 它是一个 Skill 说明文件，不是独立的 App，也不自带 Excel 写入权限、自动 WHOOP 同步或完整营养数据库。实际运行需要能读写工作簿的 AI 环境以及用户自己的工作簿。

## 适合谁

- 规律运动，想观察饮食和训练恢复关系的人
- 使用 WHOOP、Garmin、Apple Watch 等设备，并愿意手动补充每日总消耗的人
- 希望减少每日食物和自制饮品记录负担的人

## 开始使用 / Get started

- [中文上手指南](docs/GETTING-STARTED.zh-CN.md) · [English guide](docs/GETTING-STARTED.en.md)
- [下载公开空白 Excel 模板](templates/download.html)
- [中文规则](skills/alphabodycode-nutrition-logger/SKILL.ch.md) · [English rules](skills/alphabodycode-nutrition-logger/SKILL.md)

模板仅含一条通用食物示例，没有个人记录。请先在副本中完成指南里的首次测试。工作表字段为中文，英文指南提供字段对照。平台官方能力与本项目兼容性不是同一件事：各客户端的端到端测试仍待完成。

## 文件

- [`skills/alphabodycode-nutrition-logger/SKILL.md`](skills/alphabodycode-nutrition-logger/SKILL.md) — 可移植的 Skill 工作流程规则
- [`CHANGELOG.md`](CHANGELOG.md) — 版本更新记录
- [`index.html`](index.html) — GitHub Pages 静态介绍页

## 使用方式

1. 打开你拥有并已备份的营养工作簿。
2. 使用支持读取/编辑该工作簿的 AI 工具，按照 `SKILL.md` 的规则工作；具体导入Skill的界面取决于所使用的平台。
3. 先在副本中测试食物匹配、公式、下拉列表和日期汇总，再操作正式工作簿。
4. 不要上传含真实饮食、补剂、个人健康记录的工作簿到公开仓库。

## 示例

> 今天11点喝了一杯饮品：250ml牛奶、10g蛋白粉、5g胶原蛋白、3g抹茶。请按一次性临时配方合并记录，避免原料重复计入；营养数值以已有数据库和可核对的来源为准。

## 使用限制

- 能量消耗与营养摄入为估算，不能诊断营养缺乏或推断精确减脂进展。
- 本仓库没有提供官方 WHOOP API 接口，亦非 WHOOP 或 OpenAI 官方项目。
- `SKILL.md` 是否能被自动调用、是否能修改 Excel，取决于使用者的平台、账户权限和工具配置。

## 版本

首个公开预览版：**v0.1.0-beta**。见 [CHANGELOG](CHANGELOG.md)。

## 版权与授权

Copyright © 2026 AlphaBodyCode。软件与工作簿公式采用 PolyForm Noncommercial 1.0.0；Skill 与说明文档采用 CC BY-NC 4.0。具体范围及正式条款见下文和许可证文件。
---

## License & Usage

AlphaBodyCode is an independent project created and maintained by AlphaBodyCode.

The project adopts a dual-license structure to distinguish software implementation from documentation and educational materials.

### 1. Software & Workbook Implementation

The website source code, software implementation, spreadsheet formulas, workbook logic, and related technical components are licensed under the **PolyForm Noncommercial License 1.0.0**.

You may:
- Use the project for personal purposes.
- Study and modify the source code.
- Share original or modified versions for noncommercial purposes.

You may not:
- Sell this project or its modified versions.
- Redistribute it as part of a paid product or commercial service without permission.
- Use it commercially without obtaining a separate written license from AlphaBodyCode.

Full license: https://polyformproject.org/licenses/noncommercial/1.0.0

### 2. Skills & Documentation

The original Skill instructions, README documentation, tutorials, and educational materials are licensed under **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**.

You may share and adapt these materials for noncommercial purposes, provided that you:
- Give appropriate credit to AlphaBodyCode.
- Include a link to the original project and license.
- Indicate whether changes have been made.
- Do not imply endorsement by the original author.

Commercial use requires separate written permission.

Full license: https://creativecommons.org/licenses/by-nc/4.0/

### 3. Attribution

Original Project: AlphaBodyCode

Website: https://alphabodycode.github.io/

GitHub: https://github.com/alphabodycode/alphabodycode.github.io

Copyright © 2026 AlphaBodyCode. All rights reserved except as expressly permitted by the applicable licenses.

### 4. Commercial Licensing

For commercial licensing, enterprise deployment, paid distribution, or partnership opportunities, please contact the project owner for separate authorization.

### 5. Disclaimer

This project is an independent personal nutrition and energy-balance tracking tool. It is provided for informational and educational purposes only.

It is not a medical device and does not provide medical diagnosis or treatment recommendations.

---
