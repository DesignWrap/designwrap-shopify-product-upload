# PDP Schema and Source Mapping

Read this reference when starting work for a store, when the product template changes, or when source columns need mapping.

Use the working language selected in `SKILL.md` for all client-facing explanations, schema questions, and confirmation requests. Keep Shopify field names, source values, and technical identifiers in their original form unless translation is explicitly requested.

## Derive the schema

Identify both visible PDP content and the Shopify data that powers it. Depending on available access, inspect:

- the live PDP and the intended product template;
- theme section/block settings and dynamic-source connections;
- product and variant options;
- product, variant, category, or metaobject metafield definitions;
- taxonomy/category requirements;
- relevant theme code only when needed to disambiguate a data source.

Do not infer a reliable backend destination from visible text alone. For example, a Care accordion might use the product description, a product metafield, a metaobject reference, or static theme copy.

If store access is unavailable, ask for the minimum viable evidence: storefront URL plus an example product, or screenshots/export of the product template settings, dynamic-source bindings, and metafield definitions. Mark unverified destinations as uncertain.

## Schema record

Build one record per field:

| Item | Meaning |
|---|---|
| PDP label/control | What the shopper sees, such as Material or Color selector |
| Shopify destination | Core field, option/variant, metafield namespace/key, metaobject, taxonomy, or static content |
| Data type | Text, rich text, number, measurement, file, reference, list, etc. |
| Applicability | Required, conditional, optional, or generated |
| Condition | Product type/template/option rule that makes it applicable |
| Source candidates | Likely spreadsheet columns or supplied materials |
| Transformation | Safe formatting, unit normalization, copy editing, or none |
| Confidence | Confirmed, probable, or uncertain |

Distinguish:

- **Required:** needed for the applicable PDP or Shopify behavior.
- **Conditional:** required only for a defined product type, template, or variant setup.
- **Optional:** useful but does not block upload.
- **Generated:** may be produced from verified facts, such as alt text or SEO copy.

Include operational Shopify inputs that may not be visibly rendered, such as status, publication scope, category, inventory behavior, shipping weight, tax status, or fulfillment data—but only when the store workflow actually requires them.

### Inventory default

Map a supplied inventory quantity to the matching variant. When a product or variant has no inventory value in the source and the client has not provided a different rule, enable inventory tracking and set its available quantity to `1` at the store's selected location. Apply this default to every created variant, rather than summing or splitting stock across them. An explicit `0` remains `0`; do not replace it with the default.

## Metafields, Category, and Collection mapping

For every product row, identify the fields that power the selected PDP template before writing. Make the mapping visible in the preflight. A common apparel mapping is:

| Source information | Shopify destination |
|---|---|
| Product introduction / The Details | `custom.product_introduction` or the confirmed introduction field |
| Highlights | `custom.product_details` or the confirmed details field |
| Materials & Care | `custom.materials_care` |
| Size Guide | `custom.size_specifications` |
| Product images attached to the same spreadsheet row | Product media, in their source order |

Use the store's actual metafield definitions and template bindings over this example. If a source cell contains long-form copy, extract only a faithful introduction when the mapped field calls for a short introduction; retain the complete supplied description in its confirmed destination. Do not invent product claims, specifications, or sizing.

Read the store's existing Collections and Shopify Category taxonomy before assigning either. Select an existing Category and Collection only when the product title, type, materials, intended use, and supplied content support the match. Prefer the store's established naming and hierarchy. State the evidence for each proposed assignment in the preflight.

If more than one established collection or category could apply, or no confident match exists, mark the mapping **NEEDS REVIEW** and ask the client to choose. Do not create a new collection, category, tag, or taxonomy value unless that is separately authorized.

## Confirm and reuse

Present the detected schema as a short table and call out uncertain or static fields. Ask the client to confirm it once before processing the batch. Reuse the confirmed mapping for the same store and template; revalidate if the theme, template, metafield definitions, or variant model changes.

Do not silently apply one product template's schema to another template.

## Map source data

Inspect every supplied source, then map values into the confirmed schema. Normalize harmless naming differences such as `Colour` → `Color` or `RRP` → `Price` only when the meaning is clear.

For every source field classify it as:

- **Mapped** — used for a confirmed Shopify destination.
- **Preserved / not uploaded** — retained in the original source but not required.
- **Optional suggestion** — potentially valuable customer-facing content that is outside the current PDP; never blocks the batch.
- **Unclear** — meaning or destination needs confirmation.

Ignoring a column never means deleting it. Do not overwrite the client's original files unless explicitly asked.

## Gap analysis

Compare applicable schema fields against mapped values product by product and variant by variant. Ask only about required missing or contradictory values.

Good question: “Please confirm the retail price for Blue / Large.”

Bad question: “Please complete the spreadsheet.”

When several products share the same missing rule, request the information in a compact table. Keep optional suggestions separate from blockers.

## Variant integrity

Confirm:

- option names are consistent across related products;
- every intended combination is explicit;
- price, SKU, barcode, weight, inventory, and image assignments are matched to the correct variant when used;
- unavailable combinations are intentionally omitted rather than guessed;
- option ordering matches the storefront experience;
- variant-specific PDP content has a verified storage destination.

Never create a Cartesian product of options unless the source or client confirms every combination should exist.

## Variant image mapping

When the product has a Color (or Colour) option and the supplied images show specific colorways, create a variant-media mapping before upload. Use the strongest available evidence in this order:

1. An explicit source label, filename, caption, or URL that names the colorway.
2. The image's position or association within the same spreadsheet row when the source clearly pairs it with a color value.
3. A visual match between the visible product color and an existing option value.

Bind high-confidence images to the matching Color variant after the product media is uploaded. Retain every usable image in the product gallery, but do not attach lifestyle images, detail shots, multi-color group shots, or uncertain images to a specific variant. Do not infer a color solely from gallery order or force one image onto every variant.

Show the proposed image-to-variant mapping in the preflight. If an image could match more than one color, the color is not visible, or variant names do not correspond to the image, mark it **NEEDS REVIEW** and ask the client to choose. Never change the actual product color to make an image fit a variant.
