# FGH Promotional Email Build Guide

This README is a portable reference for building Freemans Grattan Holdings promotional email snippets in future AI or developer sessions.

It covers the working method, source-of-truth rules, Adobe Campaign requirements, Scene7 image conventions, brand handling, validation checks, and reusable content blocks needed to code Freemans, Grattan, Curvissa, Bonprix, Lookagain, Kaleidoscope, and related FGH campaign emails in the established FGH email style.

## Quick Start For A New Session

Before writing HTML, do these in order:

1. Read the high-resolution design PNG first.
2. Parse the XLSM brief completely once.
3. Locate and read the closest supplied template HTML.
4. Build only the first requested brand first.
5. Use the design for visible copy and layout.
6. Use the workbook for links, product data, promo code data, terms URLs, and brief-provided banner URLs.
7. Output a clean content snippet only.
8. Validate every link, image, spacer, width, CTA, and final 35px spacer before handing over.

Do not start from memory if project template HTML exists. Existing template code is the structural source of truth.

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
- Under-hero category CTA links.
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

Start with the first content `<table>` and end with the final closing table. Every email must end with a 35px spacer.

## Adobe Campaign Link And Image Rules

Every `<a>` tag must include:

```html
href="#"
target="_blank"
data-nl-type="externalLink"
data-nl-lnkep-perso-attr-href="[DESTINATION_URL]"
```

Common full link shape:

```html
<a href="#" id="LinkTrackingName" target="_blank" style="margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[DESTINATION_URL]">
```

Every `<img>` tag must include:

```html
alt=""
data-nl-imgep-perso-attr-alt="[ALT TEXT]"
height="auto"
```

Use meaningful alt text in `data-nl-imgep-perso-attr-alt`. The normal `alt` attribute may match the same copy if the supplied template does that.

Text-link CTAs styled black in light mode must include the relevant dark-mode class, usually `class="copy"`, so existing template CSS can turn them white in dark mode.

## Scene7 Asset Rules

Scene7 URL pattern:

```text
https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID]?&wid=[WIDTH]
```

Common image ID pattern:

```text
BAU_FY[YEAR]_[BRAND]_[DATE]_[CAMPAIGN]_[SECTION]
```

Example:

```text
BAU_FY26_FRE_190326_NEWSZN_20FD_HERO
```

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

Example accepted maths for 600x834 source assets:

```text
397 + 7 + 196 = 600
196 + 7 + 196 = 399
```

## Pricing Rules

TPR email pricing:

```html
<strong>£NOW </strong><s>£WAS</s>
```

Sale email pricing:

```html
<strong><span style="color:#ca0a00;">£NOW </span></strong><s>£WAS</s>
```

Price cells below images are always `text-align:left`.

## Promo Code And Offer Strip Rules

If the brief says `XXXX` for a promo code but the hero image shows a real code, use the code shown in the hero and mention the discrepancy.

When an offer code or terms strip sits directly below the hero, use the established wrapped hero offer-code pattern:

1. Outer `bgcolor="#000000"` table.
2. Hero image first.
3. 10px spacer.
4. Centered 500px `Use code <strong>CODE</strong>` row at 20px.
5. 10px spacer.
6. Centered 500px terms row at 10px/16px.

Do not invent a separate banner structure for this.

When a coded top offer banner is needed, use the supplied KAL/Freemans banner-with-code table pattern exactly and update only:

- Offer amount.
- Promo code.
- Terms wording.
- Date.

Do not add extra CTA text such as `Shop Now` unless it appears in the supplied pattern or design.

## Workbook Parsing Guidance

Parse the XLSM once per campaign unless the designer, requester, or campaign owner provides an updated workbook.

Use Python `zipfile` and XML to read:

- Workbook sheet names.
- Shared strings.
- Cell values.
- FRE sheet data.
- GRA sheet data.
- Any other brand sheet required for the campaign.

Extract all relevant data in one pass:

- Hero URL.
- Under-hero CTA labels and URLs.
- Product rows.
- Product order.
- `N` or grid-position values.
- Section CTA URLs.
- Banner image URLs.
- Promo code.
- Terms URL.

Suggested extraction approach:

```python
from pathlib import Path
from zipfile import ZipFile
import xml.etree.ElementTree as ET

XLSM = Path("Campaign Brief.xlsm")
NS = {
    "main": "http://schemas.openxmlformats.org/spreadsheetml/2006/main",
    "rel": "http://schemas.openxmlformats.org/officeDocument/2006/relationships",
}

def text_of(node):
    return "".join(t.text or "" for t in node.findall(".//main:t", NS))

with ZipFile(XLSM) as zf:
    shared = []
    if "xl/sharedStrings.xml" in zf.namelist():
        root = ET.fromstring(zf.read("xl/sharedStrings.xml"))
        shared = [text_of(si) for si in root.findall("main:si", NS)]

    workbook = ET.fromstring(zf.read("xl/workbook.xml"))
    rels = ET.fromstring(zf.read("xl/_rels/workbook.xml.rels"))
    rel_map = {rel.attrib["Id"]: rel.attrib["Target"] for rel in rels}

    for sheet in workbook.findall(".//main:sheet", NS):
        name = sheet.attrib["name"]
        rid = sheet.attrib["{http://schemas.openxmlformats.org/officeDocument/2006/relationships}id"]
        target = rel_map[rid]
        sheet_xml = "xl/" + target.lstrip("/")
        ws = ET.fromstring(zf.read(sheet_xml))
        # Walk rows/cells here and resolve shared-string cells via `shared`.
        print(name)
```

The exact parser can vary, but the important rule is: do the full extraction once, keep the data available, and do not repeatedly dip back into the workbook by hand.

## File Naming

Use the campaign naming pattern:

```text
BAU_FY[YEAR]_[FRE/GRA]_[DATE]_[CAMPAIGN].html
```

Examples:

```text
BAU_FY26_FRE_190326_NEWSZN.html
BAU_FY26_GRA_190326_NEWSZN.html
```

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
- Every `<a>` has Adobe Campaign external-link attributes.
- Every `<img>` has `alt`, `data-nl-imgep-perso-attr-alt`, and `height="auto"`.
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

## Content Blocks

Use project templates first. Use these blocks only when no supplied block exists, or to validate a generated section against the known pattern.

### 20px Spacer

```html
<table width="100%" height="20" class="full" border="0" cellpadding="0" cellspacing="0" style="line-height:20px;">
  <tbody><tr><td style="mso-line-height-rule:exactly;line-height:20px;">&nbsp;</td></tr></tbody>
</table>
```

### 35px Spacer

```html
<table width="100%" height="35" class="full" border="0" cellpadding="0" cellspacing="0" style="line-height:35px;">
  <tbody><tr><td style="mso-line-height-rule:exactly;line-height:35px;">&nbsp;</td></tr></tbody>
</table>
```

### Hero

```html
<!-- HERO -->
<table width="100%" style="min-width:100%;" class="full" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0">
  <tbody>
    <tr>
      <td width="100%" class="full" align="center" valign="top">
        <a href="#" id="HeroLink" target="_blank" style="margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[HERO_URL]">
          <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_HERO]?&wid=900" width="600" height="auto" class="full" border="0" style="display:block;text-align:center;font-size:25px;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" alt="[ALT]" data-nl-imgep-perso-attr-alt="[ALT]">
        </a>
      </td>
    </tr>
  </tbody>
</table>
<!-- /HERO -->
```

### Body Copy

```html
<!-- BODY COPY -->
<table width="100%" border="0" align="center" valign="top" cellpadding="0" cellspacing="0">
  <tbody>
    <tr>
      <td width="20" align="center" valign="top">&nbsp;</td>
      <td class="copy" width="560" align="left" valign="top" style="font-family:Arial,Helvetica,sans-serif;font-size:15px;line-height:20px;color:#000000;font-weight:normal;text-align:left;">[COPY]</td>
      <td width="20" align="center" valign="top">&nbsp;</td>
    </tr>
  </tbody>
</table>
<!-- /BODY COPY -->
```

### Standalone CTA Button

```html
<!-- CTA - [LABEL] -->
<table width="600" class="full" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="160" class="displaynone-small" align="center" valign="middle">&nbsp;</td>
      <td width="280" class="full-small" align="center" valign="middle" bgcolor="#ffffff" style="padding:0px;color:#000000;border:#000000 solid 1px;border-radius:5px;">
        <a href="#" id="[LINK_ID]" class="sbs-cta" style="font-family:Arial,sans-serif;display:block;font-weight:bold;font-size:14px;line-height:14px;text-decoration:none;color:#000000;mso-line-height-rule:exactly;text-transform:none;margin-top:0px;margin-bottom:0px;padding:1px 0;width:100%;" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL]">&nbsp;<br>[LABEL]<br>&nbsp;</a>
      </td>
      <td width="160" class="displaynone-small" align="center" valign="middle">&nbsp;</td>
    </tr>
  </tbody>
</table>
<!-- /CTA - [LABEL] -->
```

### Section Divider

```html
<!-- SECTION DIVIDER -->
<table width="100%" class="full" border="0" align="left" valign="top" cellpadding="0" cellspacing="0">
  <tbody>
    <tr>
      <td width="20" align="left" valign="top">&nbsp;</td>
      <td class="divider" width="560" align="left" valign="middle" style="font-family:Arial,Helvetica,sans-serif;font-size:20px;line-height:23px;color:#000000;font-weight:normal;text-align:left;"><strong>[DIVIDER TEXT]</strong></td>
      <td width="20" align="left" valign="top">&nbsp;</td>
    </tr>
  </tbody>
</table>
<!-- /SECTION DIVIDER -->
```

### 2-Up Product Images

`<a>` goes directly inside `<td width="297">`. Do not add an inner table per image unless a project template already uses one.

```html
<!-- 2-UP: [LABEL] -->
<table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="100%" class="full" align="center" valign="middle">
        <table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
          <tbody>
            <tr>
              <td width="297" align="center" valign="middle">
                <a href="#" id="[LINK_ID_1]" style="display:block;color:rgb(0, 0, 0);" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL_1]">
                  <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_1]?&wid=445" width="297" height="auto" class="full" border="0" alt="[ALT_1]" style="display:block;text-align:center;font-size:25px;font-weight:normal;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" data-nl-imgep-perso-attr-alt="[ALT_1]">
                </a>
              </td>
              <td width="6" align="center" valign="middle">&nbsp;</td>
              <td width="297" align="center" valign="middle">
                <a href="#" id="[LINK_ID_2]" style="display:block;color:rgb(0, 0, 0);" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL_2]">
                  <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_2]?&wid=445" width="297" height="auto" class="full" border="0" alt="[ALT_2]" style="display:block;text-align:center;font-size:25px;font-weight:normal;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" data-nl-imgep-perso-attr-alt="[ALT_2]">
                </a>
              </td>
            </tr>
          </tbody>
        </table>
      </td>
    </tr>
  </tbody>
</table>
<!-- /2-UP: [LABEL] -->
```

### 3-Up Product Images

`<a>` goes directly inside `<td width="196">`. Do not add an inner table per image unless a project template already uses one.

```html
<!-- 3-UP: [LABEL] -->
<table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="100%" class="full" align="center" valign="middle">
        <table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
          <tbody>
            <tr>
              <td width="196" align="center" valign="middle">
                <a href="#" id="[LINK_ID_1]" style="display:block;color:rgb(0, 0, 0);" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL_1]">
                  <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_1]?&wid=294" width="196" height="auto" class="full" border="0" alt="[ALT_1]" style="display:block;text-align:center;font-size:25px;font-weight:normal;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" data-nl-imgep-perso-attr-alt="[ALT_1]">
                </a>
              </td>
              <td width="6" align="center" valign="middle">&nbsp;</td>
              <td width="196" align="center" valign="middle">
                <a href="#" id="[LINK_ID_2]" style="display:block;color:rgb(0, 0, 0);" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL_2]">
                  <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_2]?&wid=294" width="196" height="auto" class="full" border="0" alt="[ALT_2]" style="display:block;text-align:center;font-size:25px;font-weight:normal;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" data-nl-imgep-perso-attr-alt="[ALT_2]">
                </a>
              </td>
              <td width="6" align="center" valign="middle">&nbsp;</td>
              <td width="196" align="center" valign="middle">
                <a href="#" id="[LINK_ID_3]" style="display:block;color:rgb(0, 0, 0);" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL_3]">
                  <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_3]?&wid=294" width="196" height="auto" class="full" border="0" alt="[ALT_3]" style="display:block;text-align:center;font-size:25px;font-weight:normal;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" data-nl-imgep-perso-attr-alt="[ALT_3]">
                </a>
              </td>
            </tr>
          </tbody>
        </table>
      </td>
    </tr>
  </tbody>
</table>
<!-- /3-UP: [LABEL] -->
```

### 2x2 CTA Grid

Use percentage widths for this block. Do not convert to fixed pixel columns.

```html
<!-- 2x2 CTA GRID -->
<table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="1%" align="center" valign="middle">&nbsp;</td>
      <td width="47%" align="center" valign="middle">
        <table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
          <tbody><tr>
            <td class="cta" width="100%" align="center" valign="middle" bgcolor="#ffffff" style="padding:0px;color:#000000;border:#000000 solid 1px;border-radius:5px;">
              <a href="#" id="[LINK_ID_1]" class="sbs-cta" style="font-family:Arial,sans-serif;display:block;font-weight:bold;font-size:14px;line-height:14px;text-decoration:none;color:#000000;mso-line-height-rule:exactly;text-transform:none;margin-top:0px;margin-bottom:0px;padding:1px 0;width:100%;" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL_1]">&nbsp;<br>[LABEL_1]<br>&nbsp;</a>
            </td>
          </tr></tbody>
        </table>
      </td>
      <td width="2%" align="center" valign="middle">&nbsp;</td>
      <td width="47%" align="center" valign="middle">
        <table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
          <tbody><tr>
            <td class="cta" width="100%" align="center" valign="middle" bgcolor="#ffffff" style="padding:0px;color:#000000;border:#000000 solid 1px;border-radius:5px;">
              <a href="#" id="[LINK_ID_2]" class="sbs-cta" style="font-family:Arial,sans-serif;display:block;font-weight:bold;font-size:14px;line-height:14px;text-decoration:none;color:#000000;mso-line-height-rule:exactly;text-transform:none;margin-top:0px;margin-bottom:0px;padding:1px 0;width:100%;" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL_2]">&nbsp;<br>[LABEL_2]<br>&nbsp;</a>
            </td>
          </tr></tbody>
        </table>
      </td>
      <td width="1%" align="center" valign="middle">&nbsp;</td>
    </tr>
  </tbody>
</table>
<table width="100%" height="10" class="full" border="0" cellpadding="0" cellspacing="0" style="line-height:10px;">
  <tbody><tr><td style="mso-line-height-rule:exactly;line-height:10px;">&nbsp;</td></tr></tbody>
</table>
<table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="1%" align="center" valign="middle">&nbsp;</td>
      <td width="47%" align="center" valign="middle">[CTA 3 TABLE]</td>
      <td width="2%" align="center" valign="middle">&nbsp;</td>
      <td width="47%" align="center" valign="middle">[CTA 4 TABLE]</td>
      <td width="1%" align="center" valign="middle">&nbsp;</td>
    </tr>
  </tbody>
</table>
<!-- /2x2 CTA GRID -->
```

For CTA 3 and CTA 4, repeat the same inner CTA table shape used for CTA 1 and CTA 2, replacing the link IDs, labels, and URLs.

### Full-Width Editorial Banner

Use for brief-provided Scene7 URLs.

```html
<!-- [BANNER NAME] EDITORIAL BANNER -->
<table width="100%" style="min-width:100%;" class="full" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0">
  <tbody>
    <tr>
      <td width="100%" class="full" align="center" valign="top">
        <a href="#" id="[LINK_ID]" target="_blank" style="margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL]">
          <img src="[SCENE7_URL_FROM_BRIEF]?wid=900" width="600" height="auto" class="full" border="0" style="display:block;text-align:center;font-size:25px;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" alt="[ALT]" data-nl-imgep-perso-attr-alt="[ALT]">
        </a>
      </td>
    </tr>
  </tbody>
</table>
<!-- /[BANNER NAME] EDITORIAL BANNER -->
```

### Larger Single Product

Use for 85% width centered Template 3 style.

```html
<!-- LARGER IMAGE: [LABEL] -->
<table width="100%" style="max-width:85%;" class="full" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0">
  <tbody>
    <tr>
      <td width="100%" class="full" align="center" valign="top">
        <a href="#" id="[LINK_ID]" target="_blank" style="margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL]">
          <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID]?&wid=780" width="544" height="auto" class="full" border="0" style="display:block;text-align:center;font-size:25px;letter-spacing:1px;line-height:28px;font-family:helvetica,arial,sans-serif;color:#000000;" alt="[ALT]" data-nl-imgep-perso-attr-alt="[ALT]">
        </a>
      </td>
    </tr>
  </tbody>
</table>
<!-- /LARGER IMAGE: [LABEL] -->
```

### Full-Width Single Image

Use for H&G style full-width image sections.

```html
<!-- FULL-WIDTH IMAGE: [LABEL] -->
<table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="100%" class="full" align="center" valign="middle">
        <table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
          <tbody>
            <tr>
              <td width="600" align="center" valign="middle">
                <a href="#" id="[LINK_ID]" style="display:block;" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[URL]">
                  <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID]?&wid=1200" width="600" height="auto" class="full" border="0" alt="[ALT]" style="display:block;" data-nl-imgep-perso-attr-alt="[ALT]">
                </a>
              </td>
            </tr>
          </tbody>
        </table>
      </td>
    </tr>
  </tbody>
</table>
<!-- /FULL-WIDTH IMAGE: [LABEL] -->
```

### Outfit Builder

Odd-numbered outfits usually use main image left. Even-numbered outfits usually use main image right.

Main image left:

```html
<!-- OUTFIT [N] -->
<table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="401" align="center" valign="middle" rowspan="3">
        <table class="full" width="401" align="center" border="0" cellspacing="0" cellpadding="0">
          <tbody><tr><td width="100%" class="full" align="center" valign="middle">
            <a href="#" id="Outfit[N]MainLink" style="display:block;" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[MAIN_URL]">
              <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_MAIN]?&wid=597" width="398" height="auto" class="full" border="0" alt="[MAIN_ALT]" style="margin:0;padding:0;border:none;display:block;" data-nl-imgep-perso-attr-alt="[MAIN_ALT]" title="[MAIN_ALT]">
            </a>
          </td></tr></tbody>
        </table>
      </td>
      <td width="6" align="center" valign="middle" style="width:6px;border-collapse:collapse;">&nbsp;</td>
      <td width="196" align="center" valign="middle">[SMALL PRODUCT 1]</td>
    </tr>
    <tr>
      <td height="6" style="font-size:6px;line-height:6px;">&nbsp;</td>
    </tr>
    <tr>
      <td width="6" align="center" valign="middle" style="width:6px;">&nbsp;</td>
      <td width="196" align="center" valign="middle">[SMALL PRODUCT 2]</td>
    </tr>
    <tr>
      <td height="6" style="font-size:6px;line-height:6px;">&nbsp;</td>
    </tr>
  </tbody>
</table>
<!-- /OUTFIT [N] -->
```

Main image right:

```html
<!-- OUTFIT [N] -->
<table class="full" width="100%" align="center" border="0" cellspacing="0" cellpadding="0">
  <tbody>
    <tr>
      <td width="196" align="center" valign="middle">[SMALL PRODUCT 1]</td>
      <td width="6" align="center" valign="middle" style="width:6px;border-collapse:collapse;">&nbsp;</td>
      <td width="402" align="center" valign="middle" rowspan="3">
        <table class="full" width="402" align="center" border="0" cellspacing="0" cellpadding="0">
          <tbody><tr><td width="100%" class="full" align="center" valign="middle">
            <a href="#" id="Outfit[N]MainLink" style="display:block;" target="_blank" data-nl-type="externalLink" data-nl-lnkep-perso-attr-href="[MAIN_URL]">
              <img src="https://s7ondemand4.scene7.com/is/image/OttoUK/[IMAGE_ID_MAIN]?&wid=597" width="398" height="auto" class="full" border="0" alt="[MAIN_ALT]" style="margin:0;padding:0;border:none;display:block;" data-nl-imgep-perso-attr-alt="[MAIN_ALT]" title="[MAIN_ALT]">
            </a>
          </td></tr></tbody>
        </table>
      </td>
    </tr>
    <tr>
      <td height="6" style="font-size:6px;line-height:6px;">&nbsp;</td>
    </tr>
    <tr>
      <td width="196" align="center" valign="middle">[SMALL PRODUCT 2]</td>
      <td width="6" align="center" valign="middle" style="width:6px;">&nbsp;</td>
    </tr>
  </tbody>
</table>
<!-- /OUTFIT [N] -->
```

Use the same 196px small product inner table shape as the full snippet or local template expects. Keep the odd/even width differences: `401` on main-left, `402` on main-right.

### Top Offer Banners

Place a top banner as the first element before the hero. Add a 10px spacer between banner and hero.

Hurry, offer ends midnight:

```html
<table width="100%" class="offerbanner" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0" bgcolor="#000000" style="line-height:34px;">
  <tbody><tr>
    <td width="45" align="center" valign="top">&nbsp;</td>
    <td width="510" class="offertext" align="center" valign="middle" bgcolor="#000000" style="font-family:Arial, Helvetica, sans-serif;font-size:13px;line-height:20px;color:#ffffff;font-weight:bold;text-align:center;text-transform:uppercase;">Hurry! <span class="offertext" style="font-weight:normal;">offer ends midni‌ght</span></td>
    <td width="45" align="center" valign="top">&nbsp;</td>
  </tr></tbody>
</table>
```

VIP Preview:

```html
<table width="100%" class="offerbanner" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0" bgcolor="#000000" style="line-height:34px;">
  <tbody><tr>
    <td width="45" align="center" valign="top">&nbsp;</td>
    <td width="510" class="offertext" align="center" valign="middle" bgcolor="#000000" style="font-family:Arial, Helvetica, sans-serif;font-size:13px;line-height:20px;color:#ffffff;font-weight:bold;text-align:center;text-transform:uppercase;">VIP Preview <span class="offertext" style="font-weight:normal;">| Be the first to shop!</span></td>
    <td width="45" align="center" valign="top">&nbsp;</td>
  </tr></tbody>
</table>
```

Flash Offer, 24hrs only:

```html
<table width="100%" class="offerbanner" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0" bgcolor="#000000" style="line-height:34px;">
  <tbody><tr>
    <td width="45" align="center" valign="top">&nbsp;</td>
    <td width="510" class="offertext" align="center" valign="middle" bgcolor="#000000" style="font-family:Arial, Helvetica, sans-serif;font-size:13px;line-height:20px;color:#ffffff;font-weight:bold;text-align:center;text-transform:uppercase;"><span class="offertext" style="font-weight:normal;">Flash Offer |</span> 2‌4hrs only</td>
    <td width="45" align="center" valign="top">&nbsp;</td>
  </tr></tbody>
</table>
```

Flash Offer, 48hrs only:

```html
<table width="100%" class="offerbanner" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0" bgcolor="#000000" style="line-height:34px;">
  <tbody><tr>
    <td width="45" align="center" valign="top">&nbsp;</td>
    <td width="510" class="offertext" align="center" valign="middle" bgcolor="#000000" style="font-family:Arial, Helvetica, sans-serif;font-size:13px;line-height:20px;color:#ffffff;font-weight:bold;text-align:center;text-transform:uppercase;"><span class="offertext" style="font-weight:normal;">Flash Offer | </span>4‌8hrs only</td>
    <td width="45" align="center" valign="top">&nbsp;</td>
  </tr></tbody>
</table>
```

VIP Email Exclusive:

```html
<table width="100%" class="offerbanner" border="0" align="center" valign="middle" cellpadding="0" cellspacing="0" bgcolor="#000000" style="line-height:34px;">
  <tbody><tr>
    <td width="45" align="center" valign="top">&nbsp;</td>
    <td width="510" class="offertext" align="center" valign="middle" bgcolor="#000000" style="font-family:Arial, Helvetica, sans-serif;font-size:13px;line-height:20px;color:#ffffff;font-weight:normal;text-align:center;text-transform:uppercase;">Vip email exclusive</td>
    <td width="45" align="center" valign="top">&nbsp;</td>
  </tr></tbody>
</table>
```

## Final Handoff Format

When handing over coded email work:

- State which brand was built.
- State the output filename.
- Mention any design vs workbook discrepancies.
- Mention whether tests or validation were run.
- For Freemans and Grattan paired work, wait for confirmation after Freemans before producing Grattan.

Keep the final message concise, but include blockers or risks clearly.
