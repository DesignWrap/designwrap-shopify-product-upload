# Upload and QA

Read this reference after schema confirmation and source mapping, before preparing an external Shopify write.

Use the working language selected in `SKILL.md` for the preflight, authorization request, QA findings, and completion report. In bilingual mode, present Chinese first with the English equivalent alongside it; keep product data and Shopify identifiers unchanged unless translation was separately requested.

## Preflight

Provide a batch summary containing:

- target store and product template;
- create vs update scope;
- products by READY / NEEDS REVIEW / BLOCKED;
- product and variant counts;
- inventory source values or the applied default of 1 per variant;
- mapped core fields and metafields, including a per-product source-to-metafield summary;
- proposed Shopify Category and existing Collection membership, with the evidence and confidence for each;
- proposed image-to-color-variant mapping, including images left gallery-only because they are not a single colorway;
- media actions and manual-review items;
- draft/active status and publication channels;
- existing data that would be overwritten;
- unresolved non-blocking decisions.

Exclude BLOCKED products from the proposed write unless the client resolves them. Obtain explicit authorization for the exact write scope.

## Prepare product records

Use the confirmed schema and preserve exact data types. Normalize presentation consistently without changing meaning:

- product and option naming;
- units and spacing while retaining source values;
- rich text structure;
- filenames and alt text;
- URL handles;
- tags and collections only within the store's existing taxonomy;
- category/metafield values only when compatible with their definitions.

For collections, add products only to client-confirmed existing collections. For categories, choose the existing taxonomy value only when the source evidence is sufficient. A blank category or collection is preferable to a guessed classification.

Do not create near-duplicate collections, metafields, metaobjects, or option names to work around an unclear mapping.

For updates, identify products using stable identifiers such as Shopify ID, SKU, barcode, or a client-confirmed handle. A similar title alone is not enough to overwrite or merge a product.

## Media handling

Classify each asset as READY, EDIT REQUIRED, or MANUAL REVIEW. Check resolution, orientation, crop, background, file size, duplicates, third-party branding, product accuracy, and variant association.

When editing is authorized:

- preserve physical product details and true color;
- use the format and dimensions appropriate to the theme, preferring efficient web delivery without visible quality loss;
- use descriptive filenames such as `rubber-treat-toy-pink-front.webp`;
- write literal, concise alt text without keyword stuffing;
- order galleries to explain the product: primary, alternate view, in-use, detail, scale/specification, packaging—adapting when another order is clearer.
- attach each high-confidence colorway image to the corresponding Color variant after media upload; leave an uncertain image gallery-only and report it for review.

## Write and verify

After the authorized write:

1. Confirm Shopify created or updated the expected records.
2. Re-read representative product and variant data from Shopify.
3. Open the actual PDP for every uploaded product when practical; for large batches, check every product programmatically and visually inspect a risk-based sample plus all exceptions.
4. Verify title, price, compare-at price, media order, variant selectors, variant price/image switching, availability, description, accordions/custom content, units, Category, collections, SEO, URL, and publication state as applicable.
5. When inventory is tracked, verify the available quantity at the selected location for every uploaded variant. Record whether the quantity came from the source or the default of 1.
6. Test responsive presentation when media or long content could affect layout.
7. Record failures by product and field. Correct only within the confirmed scope; ask before any materially different overwrite or structural change.

An import/API success does not prove that dynamic PDP fields render correctly.

## Completion report

Return:

- products created, updated, skipped, blocked, or failed;
- variants and images processed;
- PDPs checked and the sampling method, if any;
- resolved warnings;
- unresolved issues with exact client actions;
- whether products are draft or active and where they are published.

Do not say “Product Upload Complete” while required fields, failed writes, unresolved third-party branding, or broken PDP behavior remains. Use “Partially complete” and list the affected products instead.
