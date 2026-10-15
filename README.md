# WordPress SEO Audit Guide

**v1.0.0 · WordPress SEO 单页面检查标准**

针对 B2B WordPress 网站的新站上线、季度技术复查与日常巡检。直接双击 `index.html` 即可离线打开；内含 6 大模块、38 个稳定编号标准，无后端、数据库或依赖安装。

## 快速使用

- 使用关键词、专题或检查场景过滤。
- 展开标准，按“目标、位置、方法、合格条件、整改、验收”查看详细说明。
- 每项另标注检查范围（全站配置、页面类型抽样、按条件检查）和证据要求。
- 判定状态统一为通过、未通过、待验证、不适用；具体网站的状态和任务仅记录于 Workbench。
- 打印当前筛选标准；打印前自动展开，不保存页面中的审计结果。

## 技术边界

- robots.txt 控制抓取，不等同于 `noindex`。
- Canonical 是 Google 的强提示，而非保证采用的指令。
- 缺少 Meta Description、单页多个 H1、缺少可选 Schema 都不自动等于索引失败。
- 结构化数据校验通过不保证展示富媒体结果。
- Lighthouse 得分不是搜索排名分数；优先结合真实用户性能数据。
- WordPress `home` 与 `siteurl` 在特定独立目录部署中可以不同，勿机械判错。
- 禁止把未知和不适用直接统计为整改问题。

## 知识归位

- [SEO Research Playbook](https://github.com/coowinit/seo-research-playbook)：方法论、关键词、内容与竞争研究。
- **本仓库**：WordPress 专项标准与检查方法。
- [Technical SEO Workbench](https://github.com/coowinit/wordpress-technical-seo-workbench)：具体网站审计、证据、整改和归档。

## 版本

- v0.1.0：首次发布 38 项六模块的 HTML 检查手册。
- v1.0.0：综合四份独立 AI 评审，强化技术准确性、适用性、证据和复测流程；保持 38 项编号与单 HTML 架构。

原始知识规划在 `docs/knowledge-map.md`。本次整改细节在 `docs/REVIEW-AND-REMEDIATION-v1.0.0.md`。
