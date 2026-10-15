# WordPress SEO Audit Guide｜知识归位与开发范围 v0.1.0

> 基于 `coowinit/seo-research-playbook` main 分支 v2.2.1 的 README、目录和核心文档，并结合五站 2026-10-15 技术审计。此文件是新指南的规划文档，不代表现有网站已完成整改。

## 1. 项目职责

- **SEO Research Playbook**：SEO 方法论唯一维护入口；研究、架构、内容、页面优化、技术原理、数据、治理。
- **WordPress SEO Audit Guide**：WordPress 专项审查标准；操作路径、模板类型、字段与代码输出、通过条件、证据和复测。
- **WordPress Technical SEO Workbench**：未来计划负责网站级证据、审计任务、负责人、整改状态和历史快照；当前尚未建立。

**禁止重复维护：**新指南不复制 Playbook 的 SEO 原理长文，使用相对明确的引用链接与简短上下文。工作台不再成为第二份标准正文。

## 2. 知识归位矩阵

| 知识主题 | Playbook 原始文件 | 归位 | 新指南补充的实操 |
|---|---|---|---|
| 总体 SEO 方法 | `docs/01-foundation/seo-workflow.md` | 引用 | 审计场景和页面类型选择 |
| 术语 | `docs/01-foundation/terminology.md` | 引用 | WordPress 专用术语补充，不重复定义通用术语 |
| 关键词研究 | `docs/02-research/keyword-research.md` | 引用 | 查询词与 Post、Page、CPT、Taxonomy 映射验收 |
| 竞品与 SERP | `docs/02-research/competitor-site-research.md`、`serp-research.md` | 引用 | 仅建立检查入口 |
| 网站架构 | `docs/03-architecture/site-architecture.md` | 引用+专项 | Rewrite、固定链接、层级 Taxonomy、分页和可抓取链接 |
| 内容生产与 AI | `docs/04-content/content-production.md`、`ai-assisted-seo.md` | 引用 | 发布工作流、作者、修订、媒体字段、状态控制 |
| 页面 SEO | `docs/05-optimization/on-page-seo.md` | 引用+专项 | 按模板验证 Title/Description/H1/图片/内链的前台输出 |
| 技术 SEO | `docs/05-optimization/technical-seo.md` | 引用+重点专项 | robots、Sitemap、HTTP、Canonical、Schema、SEO 插件冲突的 WordPress 操作 |
| 月度分析 | `docs/06-measurement/seo-monthly-performance-tracking.md` | 引用 | 技术审计后复测与 GSC 关联，非重复数据仪表盘 |
| GSC 分析 | `docs/06-measurement/search-console-analysis.md` | 引用 | URL Inspection 验收记录字段 |
| 历史内容治理 | `docs/07-governance/content-governance.md` | 引用+专项 | 产品下架、归档、附件、重定向、Sitemap 同步 |
| 技术检查表 | `checklists/05-optimization/technical-seo.md` | 引用+结构化 | 形成稳定检查 ID 与 WordPress 操作和结果 |
| 技术审计模板 | `templates/05-optimization/technical-seo.md` | 引用 | 结果可记录于独立报告；未来再考虑与 Workbench 数据结构映射 |
| 内容审核清单 | `checklists/04-content/article-review.md` | 引用 | 文章后台发布前审核字段 |
| 页面 SEO 检查表 | `checklists/05-optimization/page-seo.md` | 引用 | 主题渲染验证 |

## 3. 六大 WordPress 专项与首轮检查点

### WP-01 基础设置与可索引性
- WP-01-01 设置 > 阅读：搜索引擎可见性设置与实际 robots/noindex 是否一致。
- WP-01-02 站点地址与 WordPress 地址；HTTP/HTTPS、www/裸域统一。
- WP-01-03 固定链接、Rewrite 与迁移后的 301/404。
- WP-01-04 robots.txt 的实际正文、来源、资源路径匹配。
- WP-01-05 XML Sitemap、子地图、CPT/Taxonomy 收录边界。
- WP-01-06 搜索、作者、标签、附件、feed、测试页的索引策略。

### WP-02 内容类型与模板矩阵
- WP-02-01 首页 front-page/home 的实际模板及 Title/H1。
- WP-02-02 Page 与 Post 详情：主标题、内容、作者、更新日期。
- WP-02-03 CPT 产品/案例/下载/FAQ：public、publicly_queryable、exclude_from_search、has_archive、rewrite 的实际影响。
- WP-02-04 分类法归档：taxonomy term 标题、meta、canonical、真实分页。
- WP-02-05 归档、第二页及更深分页：可访问、href、canonical。
- WP-02-06 404/410、已删除或迁移产品的状态与跳转。
- WP-02-07 重要站内链接在渲染 DOM 中可抓取。

### WP-03 SEO 标签与结构化数据唯一责任
- WP-03-01 Theme / SEO Plugin / 自研插件：Title 唯一输出责任。
- WP-03-02 Description、Canonical、OG/Twitter、robots、Sitemap 的责任划分。
- WP-03-03 wp_head()/wp_footer()、主题手写 Head 与重复输出风险。
- WP-03-04 Schema 的 Organization、Product、BlogPosting、BreadcrumbList 按页面类型绑定真实数据。
- WP-03-05 作者 display_name 与 schema author.name 一致；正确 JSON 序列化。
- WP-03-06 WooCommerce 或询盘业务的 Product 字段不可伪造 offers/review/rating。

### WP-04 图片、资源、性能与缓存
- WP-04-01 重要图片的附件 ID、alt、数值宽高及布局预留。
- WP-04-02 响应式 srcset/sizes 或对应 picture/source 策略。
- WP-04-03 无图分支不输出错误 src=""；轮播装饰副本与主图区分。
- WP-04-04 wp_enqueue_script/style 与依赖 handle；检查 jQuery/Swiper 重叠引用。
- WP-04-05 Elementor 模板与普通模板的脚本、缓存和 head 输出差异。
- WP-04-06 WP Rocket、Cloudflare、CDN 缓存清理与首次访问回归。
- WP-04-07 真实用户 LCP/INP/CLS 与实验室诊断分开记录。

### WP-05 多语言与地区版本
- WP-05-01 URL、内容语言、html lang 及地区策略一致。
- WP-05-02 逐页等价映射，而非所有语言内页指向对应首页。
- WP-05-03 hreflang 自身与双向返回、Canonical 和状态码一致。
- WP-05-04 HTML/HTTP/Sitemap 申明渠道、x-default 与语言代码正确。
- WP-05-05 缺少真实译文的页面不制造不存在的版本链接。

### WP-06 发布验收、证据与回退
- WP-06-01 审计范围与样本：首页/分类/产品/归档/文章/分页/业务专项。
- WP-06-02 证据状态：已确认/风险或条件项/待验证/不适用/已通过。
- WP-06-03 区分证据状态和工作状态；不将未知计作故障。
- WP-06-04 改动前备份、测试站验证、发布、缓存清理、回退方案。
- WP-06-05 验收包含原始响应、渲染 DOM、GSC、日志、用户关键流程。
- WP-06-06 记录检查标准版本、执行日期、样本 URL、负责人、复测日期。

**注意：**上述检查点为首版规划 ID，不应直接覆盖历史审计的 C01—W04 编号；应另建映射表。

## 4. HTML 页面：建议两个，不重新建设四个阅读器

- `index.html`：与现有 Playbook 相似的 Markdown 阅读入口；专题导航、检索、相关标准及来源引用。正文唯一来源是 `docs/*.md`。
- `checklist.html`：从独立 JSON 标准字段生成检查清单；支持按首页、分类、产品、文章、上线、季度等场景筛选，以及打印/导出空白检查表。

方法论与操作规范作为 Markdown 文档由 index.html 阅读器打开，不再独立开发 `methodology.html` 和 `standards.html`，避免重复维护。当前网站的实际任务和状态应另外归档；Technical SEO Workbench 尚未建立。

## 5. 推荐数据与目录

```text
wordpress-seo-audit-guide/
├── README.md
├── index.html
├── checklist.html
├── assets/
│   ├── css/style.css
│   ├── js/app.js
│   ├── js/checklist.js
│   └── data/catalog.json
├── data/
│   ├── checks.json          # 稳定 ID、规则、适用模板和场景
│   ├── profiles.json        # 新站上线、常规巡检、季度、全面审查
│   └── legacy-map.json      # 旧 C01—W04 与新标准的关联
├── docs/
│   ├── 00-methodology.md
│   ├── 01-wordpress-basics.md
│   ├── 02-page-templates.md
│   ├── 03-seo-ownership.md
│   ├── 04-media-performance.md
│   ├── 05-international.md
│   └── 06-release-regression.md
└── .nojekyll
```

## 6. 第一版边界与验收

### V0.1.0 交付
1. 知识归位说明与仓库 README。
2. 六个 WordPress 专项首轮检查规则、适用页面、检查步骤和通过标准。
3. 检查数据 JSON、历史编号映射（对无法一一对应的情况保留多对多关联）。
4. 两个响应式 HTML 页面与统一的阅读入口。
5. 对 Playbook 的链接而非复制原文。

### 不纳入初版
- 爬虫/自动扫描、GSC API 直连、多人编辑、在线数据库、SEO 打分、五站具体问题复制到此仓库。

### 开发与验收要点
- Markdown 是知识正文唯一来源；JSON 是可执行检查规则来源。
- 相同标准在文档与 JSON 中只保留一处正式定义或清晰引用，避免互相矛盾。
- 新站审计记录暂用独立报告或任务表保存，不在指南中维护第二份状态。
- 每个技术结论写明官方要求、建议实践、适用条件和证据等级。
- 上线前检查 Markdown 链接、JSON ID 唯一、场景筛选、移动端和打印效果。

## 7. 整合顺序

1. 保持 `seo-research-playbook` v2.2.1 的七大结构和正文不动。
2. 基于五站审计的共性定义 WordPress 专项标准。
3. 优先建立 legacy-map.json，保证现有整改任务关联不会失效。
4. 开发 HTML 阅读与检查清单，不建设重复的 SEO 百科。
5. 使用 5 个真实网站做样本验证并完成版本发布。


> 实施注记：2026-10-15 最终决策将原计划的两个 HTML 精简为单个 index.html，CSS、JS 和检查数据均内嵌。以上双页面章节仅保留作历史规划参考。
