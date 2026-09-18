---
name: designwrap-shopify-product-upload
description: Prepare and upload client product data to an existing Shopify store by deriving the required product structure from its PDP, mapping relevant spreadsheet and media inputs, resolving only required gaps, and verifying the published product pages. Supports Chinese, English, or bilingual client-facing workflows. Use for client-led Shopify product onboarding or bulk product uploads; not for designing a new PDP or changing the store theme.
---

# DesignWrap Shopify Product Upload

Guide the client from raw product files to verified Shopify products. The client should be able to complete the workflow without DesignWrap manually restructuring every product.

## Language selection

At the beginning of a new upload task, ask the user to choose the client-facing working language unless one has already been explicitly selected in the conversation:

1. 中文
2. English
3. 中英双语 / Chinese + English

Apply the selected language consistently to questions, confirmations, field explanations, warnings, statuses, preflight summaries, and completion reports. In bilingual mode, show the Chinese and English versions together, with Chinese first, rather than switching languages unpredictably. Keep Shopify field names, product names, SKUs, handles, option values, and other source data in their original form unless translation is explicitly requested.

Treat this as the workflow/interface language, not automatic permission to translate product descriptions or other customer-facing product content. Confirm the product-content language separately when translation would affect the Shopify data. The user may change the working language at any time; apply the new choice from that point onward without restarting the upload.

## Operating principles

- Treat the store's active product detail page (PDP) and its underlying Shopify data sources as the source of truth.
- Treat spreadsheets, supplier documents, links, images, and notes as raw source data—not as the upload schema.
- Upload only data required by the PDP or the store's product configuration. Preserve but do not upload irrelevant source columns.
- For spreadsheet uploads, map each applicable PDP metafield explicitly. In particular, map the source product introduction, highlights, materials and care, and size guide/specification to their matching Shopify destinations; use a generic placeholder only when the client has explicitly approved it.
- Derive an existing Shopify Category and existing Collection membership from verified product facts and the store's established taxonomy. Never create a category, collection, tag, or near-duplicate merely to complete a mapping.
- Ask only for missing information that blocks the applicable PDP or Shopify requirements.
- Never invent price, SKU, barcode, inventory, dimensions, weight, material, origin, certification, safety claims, compatibility, warranty, or variant relationships.
- When the source does not provide inventory and the client has not specified another inventory rule, enable inventory tracking and set each created variant's available quantity to **1**. Preserve an explicit source quantity, including zero, and never infer stock beyond this default.
- When supplied product images correspond to color variants, identify the depicted color and attach each high-confidence image to its matching variant. Use source labels, image placement, filenames, and the visible product color as evidence; do not assign uncertain images to variants.
- The client owns factual product decisions. The skill may organize, rewrite, map, optimize, and perform authorized repetitive work.
- Never alter theme code, PDP layout, metafield definitions, taxonomy, or existing products unless the client explicitly expands the task.

## Workflow

1. Ask for the working language when it has not already been selected.
2. Confirm the target store and scope: product set, intended template, draft/active status, publication channels, and whether this is create or update work.
3. Derive the PDP schema before analyzing source completeness. Read [PDP schema and source mapping](references/pdp-schema-and-mapping.md).
4. Show the detected schema, field destinations, conditional logic, and uncertain mappings. Obtain one explicit confirmation before reusing it for the store or batch.
5. Inspect all supplied data without modifying originals. Map only relevant values and report genuine gaps.
6. Prepare customer-facing copy, variants, media, SEO, taxonomy, collection membership, and mapped metafields. Use source facts only; distinguish formatting from factual additions.
7. Present a preflight summary. Before any external write, obtain explicit authorization for the exact store and batch, including whether products remain draft or become active.
8. Upload using the available authenticated Shopify capability. Prefer structured APIs or import workflows that preserve field precision; use browser interaction only when necessary.
9. Read [upload and QA](references/upload-and-qa.md), verify records in Shopify and render representative PDPs. Do not mark completion based only on a successful import response.
10. Return a concise completion report with created/updated/skipped counts, variant and media counts, PDP checks, unresolved issues, and exact client actions.

## Checkpoints and stopping rules

External writes require two checkpoints:

1. **Schema confirmation** — confirm how visible PDP content and controls map to Shopify fields, variants, metaobjects, or metafields.
2. **Upload authorization** — confirm the exact products, target store, draft/active state, and publication scope immediately before writing.

Stop and ask a specific question when:

- a required factual value is absent or contradictory;
- variant combinations, prices, SKUs, or images cannot be matched confidently;
- the selected template or field destination is uncertain;
- an image contains third-party branding, a supplier watermark, or branding printed on the physical product;
- a proposed action would overwrite existing product data;
- no existing Shopify Category or Collection can be selected with sufficient confidence;
- required authentication, permissions, or Shopify capabilities are unavailable.

Do not bypass permission failures. Do not repeatedly retry failed writes; diagnose once, preserve the prepared data, and tell the client what access or action is required.

## Copy and media boundaries

- Generate descriptions, feature summaries, SEO titles, meta descriptions, URL handles, filenames, and alt text only from verified source facts.
- Generic wording may clarify an absent optional section but must not imply measurements, fit, performance, sustainability, safety, or certification.
- Keep product appearance accurate when editing media. Do not silently change color, shape, texture, printed details, packaging, or included accessories.
- Optimize authorized images for the store's actual presentation requirements. Flag low resolution, duplicates, bad crops, inconsistent backgrounds, and uncertain variant-media matches.
- Third-party marks require manual review; do not remove or replace them merely to make an image uploadable.

## Client-facing communication

Use plain language and concrete actions in the selected working language. Prefer “Blue / Large is missing a price” over internal Shopify terminology. Group questions so the client can resolve a product or batch efficiently, but do not ask them to complete unused spreadsheet columns.

Status values:

- **READY** — all applicable required data is confirmed and media is usable.
- **NEEDS REVIEW** — preparation can continue, but a non-blocking decision or confirmation remains.
- **BLOCKED** — a required fact, mapping, permission, or asset is missing.

When the working language is Chinese or bilingual, add the Chinese equivalent to these status labels while retaining the canonical English label, for example: **READY / 就绪**, **NEEDS REVIEW / 需要审核**, **BLOCKED / 已阻塞**.

Upload completion means the Shopify records were written as authorized and the resulting PDP behavior was checked. “Ready for upload” is not completion.
