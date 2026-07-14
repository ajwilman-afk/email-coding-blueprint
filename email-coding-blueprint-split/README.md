# FGH Promotional Email Build Guide

This README is the lightweight starting point for building Freemans Grattan Holdings promotional email snippets in future AI or developer sessions.

Read this file first. Then open only the supporting file needed for the specific campaign layout. This keeps sessions focused and avoids loading every reusable HTML block when a design only needs one or two section types.

## Quick Start For A New Session

Before writing HTML:

1. Read the high-resolution design PNG first.
2. Parse the XLSM brief completely once.
3. Locate and read the closest supplied template HTML.
4. Build only the first requested or primary brand first.
5. Use the design for visible copy and layout.
6. Use the workbook for links, product data, promo code data, terms URLs, and brief-provided banner URLs.
7. Output a clean Adobe Campaign content snippet only.
8. Validate every link, image, spacer, width, CTA, and final 35px spacer before handing over.

Do not start from memory if project template HTML exists. Existing template code is the structural source of truth.

## Resource-Conscious Use

For most sessions, read only these README sections first:

- Quick Start For A New Session
- Source Of Truth Rules
- Build Order
- Output Format
- Adobe Campaign Link And Image Rules
- Scene7 Asset Rules
- Spacer Rules
- Validation Checklist

Then read only the relevant supporting file:

| Need | File |
| --- | --- |
| Workbook extraction approach | [docs/workbook-parsing.md](docs/workbook-parsing.md) |
| Pricing, promo codes, offer strips | [docs/pricing-and-offers.md](docs/pricing-and-offers.md) |
| Spacers, hero, body copy, CTA, dividers | [blocks/core.md](blocks/core.md) |
| 2-up, 3-up, CTA grids, editorial banners, singles | [blocks/product-grids.md](blocks/product-grids.md) |
| Outfit builder layouts | [blocks/outfit-builder.md](blocks/outfit-builder.md) |
| Top offer banners | [blocks/top-offer-banners.md](blocks/top-offer-banners.md) |

Use project templates before snippets. The block files are fallbacks and validation references when a matching supplied template block is not available.

## Required Inputs

Campaign folders usually contain:

- A high-resolution design PNG, normally one folder above `Email Code/`.
- An XLSM brief, also normally one folder above `Email Code/`.
- One or more HTML template files in `HTML_Templates/`, a local template folder, or nearby dated FGH campaign folders.
- Product or banner asset naming instructions, sometimes visible in the workbook or the design.

If only an XD file exists, ask the designer or requester for a 2x PNG export before coding.

## Source Of Truth Rules

Use the design PNG for:

- Visible copy.
- Hero text.
- CTA labels.
- Section divider text.
- Promo code text visible in the creative.
- Section order.
- Whether CTAs sit above or below product blocks.
- Whether a product section uses 2-up, 3-up, mosaic, larger single, full-width, or outfit-builder layout.
- Whether per-item CTAs exist.

Use the XLSM workbook for:

- Destination URLs.
- Hero links.
- Under-hero CTA labels and links.
- Product rows.
- Product order and grid-position values such as `N`.
- Section CTA links.
- Banner image URLs.
- Promo code data.
- Terms and conditions URL.
- Brand-specific URLs.

Use template HTML for:

- Table nesting.
- Column widths.
- CTA structure.
- Typography.
- Classes.
- Spacers.
- Existing comments and naming patterns.
- Dark-mode class usage.

If the design and workbook disagree on brand, promo code, section order, or CTA placement, stop and report the mismatch.

## Build Order

For Freemans and Grattan pairings:

1. Build Freemans first.
2. Wait for the designer, requester, or reviewer to confirm.
3. Build Grattan after approval.

Grattan usually reuses Freemans product image IDs, but must use Grattan sheet destination URLs. Do not derive Grattan product URLs by editing Freemans URLs.

Grattan banner image URLs must come directly from the Grattan brief sheet. Do not derive them by changing the Freemans banner filename.

## Output Format

Return a clean Adobe Campaign content snippet only.

Do not include:

- `<!DOCTYPE>`
- `<html>`
- `<head>`
- `<body>`
- ACR wrappers
- `<script>`
- `<style>`

Start with the first content table and end with the final closing table. Every email must end with a 35px spacer.

## Adobe Campaign Link And Image Rules

Every link must use Adobe Campaign external-link attributes:

- `href="#"`
- `target="_blank"`
- `data-nl-type="externalLink"`
- `data-nl-lnkep-perso-attr-href="[DESTINATION_URL]"`

Every image must include:

- `alt=""` or the template's expected normal alt text.
- `data-nl-imgep-perso-attr-alt="[ALT TEXT]"`.
- `height="auto"`.

Use meaningful alt text in `data-nl-imgep-perso-attr-alt`. Text-link CTAs styled black in light mode must include the relevant dark-mode class, usually `class="copy"`, so existing template CSS can turn them white in dark mode.

## Scene7 Asset Rules

Scene7 URL pattern: `https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID]?&wid=[WIDTH]`

Common image ID pattern: `BAU_FY[YEAR]_[BRAND]_[DATE]_[CAMPAIGN]_[SECTION]`

Example: `BAU_FY26_FRE_190326_NEWSZN_20FD_HERO`

Conventions:

- Hero assets end `_HERO`.
- Product assets use `_1`, `_2`, `_3`, and so on.
- Brief-provided banners may have existing Scene7 IDs and URLs. Use the brief URL directly.
- Freemans uses FRE image IDs.
- Grattan product sections usually reuse FRE image IDs.
- Grattan URLs come from the Grattan workbook sheet.

Standard widths:

| Section | Scene7 `wid=` | Display width |
| --- | ---: | ---: |
| Hero | 900 | 600 |
| Full-width banner | 900 or 1200, depending on template | 600 |
| 2-up product | 445 | 297 |
| 3-up product | 294 | 196 |
| Larger single product | 780 | 544 |
| Outfit main image | 597 | 398 |
| Outfit small product | 294 | 196 |

## Spacer Rules

| Use | Spacer height |
| --- | ---: |
| Between sections | 35px |
| Between copy and images | 20px |
| Between section divider and following copy | 10px |
| Between top banner and hero | 10px |
| End of every email | 35px |

Product image gaps:

- 2-up row: `297 + 6 + 297 = 600`.
- 3-up row: `196 + 6 + 196 + 6 + 196 = 600`.
- Mixed mosaic rows may use a non-6px gap only when exact image maths requires it.

For mixed mosaic sections with one large image beside two stacked smaller images, calculate widths and vertical stack gap together so the large image height matches the two small image heights plus the gap. The total row must still equal 600px.

## File Naming

Use the campaign naming pattern: `BAU_FY[YEAR]_[FRE/GRA]_[DATE]_[CAMPAIGN].html`

Examples:

- `BAU_FY26_FRE_190326_NEWSZN.html`
- `BAU_FY26_GRA_190326_NEWSZN.html`

## Stop Conditions

Stop and ask the designer, requester, or campaign owner for clarification if:

- The high-resolution PNG is missing.
- Only an XD file exists and no 2x PNG export is available.
- The workbook lacks the expected brand sheets.
- The design and workbook disagree on a critical item.
- No local or nearby template can be found for the requested structure.
- A required URL is missing.
- A required banner URL is missing from the brand-specific sheet.

## Validation Checklist

Before delivery, check:

- Output is a snippet only.
- No `html`, `head`, `body`, `script`, or `style` wrappers.
- First element is the first content table.
- Final element is followed by a 35px spacer.
- Every link has Adobe Campaign external-link attributes.
- Every image has `alt`, `data-nl-imgep-perso-attr-alt`, and `height="auto"`.
- All image URLs use the right Scene7 ID and width.
- Freemans links are from FRE data.
- Grattan links are from GRA data.
- Grattan product image IDs still use the shared FRE product assets where expected.
- CTA labels match the design.
- Section divider copy matches the design.
- Promo code matches the design when the brief uses a placeholder.
- Product order follows the design and workbook grid positions.
- No per-item CTAs were added unless the design shows them.
- 2-up widths total 600.
- 3-up widths total 600.
- Spacers match the house spacing rules.
- Pricing format matches TPR or Sale mode.
- Black text-link CTAs include dark-mode class handling where needed.

## Final Handoff Format

When handing over coded email work:

- State which brand was built.
- State the output filename.
- Mention any design vs workbook discrepancies.
- Mention whether tests or validation were run.
- For Freemans and Grattan paired work, wait for confirmation after Freemans before producing Grattan.

Keep the final message concise, but include blockers or risks clearly.
