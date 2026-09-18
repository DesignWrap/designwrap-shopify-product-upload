# DesignWrap Shopify Product Upload

[中文](#中文说明) · [English](#english)

An open-source AI skill by [DesignWrap](https://designwrap.co) that turns product spreadsheets and media into structured, checked Shopify product listings.

## 中文说明

### 这是什么？

**DesignWrap Shopify Product Upload** 是一个用于 ChatGPT / Codex 的 Shopify 商品上架 Skill。

你可以把现有的 Excel、产品图片、供应商资料和备注交给它。它会先查看你的 Shopify 产品详情页需要哪些内容，再整理和匹配数据，经过你确认后创建或更新商品，并检查实际页面是否正常显示。

它的目标不是让 AI 随意生成商品资料，而是减少重复、低价值的手动录入，同时保留必要的人工确认。

### 它可以做什么？

- 根据现有产品详情页，识别需要填写的 Shopify 字段和 Metafields
- 从 Excel、文档、链接、图片和备注中提取并整理相关资料
- 忽略详情页不需要的表格列，同时保留原始文件不变
- 整理标题、描述、SEO、Variant、图片、Category 和 Collection
- 在资料允许时，把不同颜色的产品图片匹配到对应 Variant
- 发现缺失或矛盾的数据，只询问真正影响上架的问题
- 上传前提供清晰的检查摘要，得到确认后才写入 Shopify
- 支持创建草稿或更新现有商品
- 上传后检查商品记录、库存、图片、Variant 和产品详情页显示
- 支持中文、英文或中英双语工作流程

如果表格没有提供库存数量，默认会为每个新建 Variant 开启库存追踪，并把库存设为 `1`。表格中明确填写的库存（包括 `0`）会被保留。

### 它不会做什么？

- 不会编造价格、SKU、尺寸、材质、认证、安全声明或其他产品事实
- 不会未经确认直接发布商品
- 不会自动修改主题代码、产品详情页设计或 Metafield 定义
- 不会为了完成匹配而创建重复的 Category、Collection 或 Tag
- 不会仅因为导入成功就判断任务完成；还需要检查实际产品页面

### 适合谁？

- 需要批量上架 Shopify 商品的品牌和商家
- 已有供应商 Excel，但表格结构与 Shopify 不一致的团队
- 希望减少商品录入时间，同时保留人工审核的店主
- 为客户管理 Shopify 商品资料的设计师、开发者和电商团队

### 安装方式

1. 下载或克隆这个仓库。
2. 将 `designwrap-shopify-product-upload` 文件夹添加到支持 Skills 的 ChatGPT / Codex 环境。
3. 上传你的产品表格和图片，然后调用 `@DesignWrap Shopify Product Upload`。

不同版本的 ChatGPT / Codex 安装入口可能不同，请以你当前产品界面为准。

### 示例指令

```text
@DesignWrap Shopify Product Upload 请读取我上传的 Excel，
为第 9–12 行创建 Shopify 商品草稿。
使用产品模板“Default product”。
请先给我检查摘要，不要发布，待我确认后再上传。
```

### 工作流程

1. 选择中文、英文或中英双语。
2. 确认目标店铺、商品范围、产品模板和草稿/发布状态。
3. 识别产品详情页所需字段及其 Shopify 数据来源。
4. 将原始资料映射到正确字段，并标记缺失或不确定内容。
5. 展示上传前检查摘要，请用户确认。
6. 使用已连接并获得授权的 Shopify 工具执行上传。
7. 检查商品记录和实际产品详情页，并返回完成报告。

### 关于 DesignWrap

[DesignWrap](https://designwrap.co) 是一家位于澳大利亚墨尔本的独立数字设计工作室，专注于 Shopify、Webflow、Framer 网站设计与开发。这个 Skill 来自真实的 Shopify 客户项目流程，用来减少重复录入，让品牌和设计团队把时间放在更重要的产品、内容和客户体验上。

如果你需要定制 Shopify 网站、产品详情页规划或商品数据结构设计，可以联系 DesignWrap。

---

## English

### What is it?

**DesignWrap Shopify Product Upload** is a Shopify product-upload skill for ChatGPT / Codex.

Give it your existing spreadsheets, product images, supplier documents, links, and notes. It first checks what your current Shopify product page needs, maps the relevant data, asks for approval, creates or updates products, and verifies the resulting product pages.

The goal is not to let AI invent product information. It is to reduce repetitive manual entry while keeping important decisions under human control.

### What can it do?

- Detect the Shopify fields and metafields used by an existing product page
- Extract and organize relevant information from spreadsheets, documents, links, images, and notes
- Ignore spreadsheet columns the product page does not use, without changing the original file
- Prepare titles, descriptions, SEO, variants, images, categories, and collection assignments
- Match product images to color variants when the evidence is clear
- Find missing or conflicting data and ask only the questions that block the upload
- Show a clear preflight summary before writing anything to Shopify
- Create draft products or update existing products after approval
- Check product records, inventory, media, variants, and the rendered product page after upload
- Work in Chinese, English, or bilingual mode

If inventory is missing, the skill enables inventory tracking and sets each newly created variant to `1` by default. Any explicit source quantity, including `0`, is preserved.

### What will it not do?

- It will not invent prices, SKUs, measurements, materials, certifications, safety claims, or other product facts
- It will not publish products without approval
- It will not change theme code, PDP design, or metafield definitions unless the scope is explicitly expanded
- It will not create duplicate categories, collections, or tags just to complete a mapping
- It will not treat a successful import as proof that the storefront works; the actual PDP still needs verification

### Who is it for?

- Brands and merchants uploading many Shopify products
- Teams whose supplier spreadsheets do not match their Shopify setup
- Store owners who want less manual entry without losing control of product data
- Designers, developers, and ecommerce teams managing Shopify catalogues for clients

### Installation

1. Download or clone this repository.
2. Add the `designwrap-shopify-product-upload` folder to a ChatGPT / Codex environment that supports Skills.
3. Upload your product spreadsheet and media, then invoke `@DesignWrap Shopify Product Upload`.

The exact installation entry point may differ between ChatGPT / Codex versions. Follow the interface available in your product.

### Example prompt

```text
@DesignWrap Shopify Product Upload, read the spreadsheet I uploaded
and create draft Shopify products for rows 9–12.
Use the product template “Default product”.
Show me the preflight summary first. Do not publish until I approve.
```

### How it works

1. Choose Chinese, English, or bilingual mode.
2. Confirm the store, product scope, template, and draft/publishing state.
3. Identify the fields required by the product page and their Shopify data sources.
4. Map the source files to the correct fields and flag missing or uncertain information.
5. Show a preflight summary and request approval.
6. Upload through an authenticated Shopify connection.
7. Verify the Shopify records and rendered PDPs, then return a completion report.

### About DesignWrap

[DesignWrap](https://designwrap.co) is an independent digital design studio based in Melbourne, Australia, specializing in Shopify, Webflow, and Framer design and development. This skill comes from a real client delivery workflow. It was created to reduce repetitive product-entry work so brands and design teams can focus on product, content, and customer experience.

For custom Shopify design, PDP planning, or product-data architecture, contact DesignWrap.

## Repository structure

```text
designwrap-shopify-product-upload/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── pdp-schema-and-mapping.md
    └── upload-and-qa.md
```

## License

MIT License. See [LICENSE](LICENSE).

## Disclaimer

This is an independent open-source project by DesignWrap. It is not affiliated with or endorsed by Shopify or OpenAI. Shopify, ChatGPT, and Codex are trademarks of their respective owners.
