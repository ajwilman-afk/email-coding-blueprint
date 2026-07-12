Freemans HTML Email Development Framework

A comprehensive specification and production toolkit for building responsive, accessible, and client-compatible HTML marketing emails for Freemans.

Overview

This repository contains the official framework, coding standards, quality assurance checklists, and reusable HTML components required to build marketing emails for Freemans.

Unlike standard web development, email client HTML must support hundreds of legacy rendering engines (including Microsoft Outlook, Gmail, Apple Mail, Yahoo Mail, Samsung Mail, and others). This framework guarantees absolute visual consistency, accessibility, and high performance across all targeted configurations.

Core Objectives

Pixel-Perfect Rendering: Matching approved artwork exactly across modern and legacy clients.

Accessibility First: Native support for screen readers, legible contrasts, and logical hierarchies.

Responsive Frameworks: Clean fluid-to-breakpoint stacking logic for optimal mobile display.

Cross-Client Compatibility: Bulletproof nesting techniques designed to withstand Microsoft Word-based rendering engines.

High Performance: Optimized structures keeping absolute file sizes lightweight.

Golden Rules

ALWAYS

✔ Use nested, table-based layouts (<table role="presentation">) for structure.

✔ Inline every single CSS style directly onto the structural elements.

✔ Code using a responsive, mobile-first or fluid-hybrid outlook.

✔ Provide meaningful alternative (alt) text for all key images.

✔ Include a hidden preheader directly after the opening <body> tag.

✔ Optimise and compress every image before reference.

✔ Test builds thoroughly across MS Outlook, Gmail, and Apple Mail.

✔ Keep code block structures modular and reusable.

✔ Ensure calls-to-action (CTAs) are fully clickable over their entire visual surface.

✔ Prioritise live HTML text over embedded-image copy wherever layout permits.

✔ Maintain clean, human-readable structural code with clear logical indentations.

NEVER

✘ Use CSS Grid layouts.

✘ Use Flexbox logic (display: flex).

✘ Depend on absolute or relative positioning (position: absolute, position: relative).

✘ Include JavaScript.

✘ Reference external CSS style sheets.

✘ Use custom web fonts unless explicitly brand-approved and accompanied by safe fallbacks.

✘ Rely on CSS variables (var(--variable-name)).

✘ Use unsupported CSS selectors or properties.

✘ Build structural column or grid layouts using <div> elements.

✘ Bake primary copy or action calls directly inside image assets without a live alternative.

Supported Email Clients

Target support standards must be fully optimized for:

Outlook (Windows legacy and modern engines)

Outlook (Mac)

Outlook Mobile (iOS & Android)

Gmail (Desktop web app)

Gmail App (iOS & Android)

Apple Mail (macOS & iOS)

Yahoo Mail (Web & App)

Samsung Mail

AOL Mail

Email Structure

Every HTML build must strictly adhere to the following block layout order:

<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Meta tags for character sets, viewports, and client detection -->
  <!-- CSS Styles (Munging & baseline mobile overrides) -->
</head>
<body>
  <!-- Hidden Preheader Wrapper -->
  <!-- Outer Centered Wrapper Table (100% width) -->
    <!-- Main Email Container Table (640px max-width) -->
      <!-- Brand Header Section -->
      <!-- Category Navigation Block -->
      <!-- Main Content Modules (Heros, Banners, Grids) -->
      <!-- Footer / Legal Info / Unsubscribe Link -->
  <!-- Tracking Pixels -->
</body>
</html>


Layout and Sizing Standards

Desktop Standard Width: $640\text{px}$ maximum. (Acceptable variations range between $600\text{px}$ and $640\text{px}$ based on specific design requests).

Mobile Standard Width: $100\%$ fluid.

Margins and Padding Spacing System: Spacing increments must strictly align to the approved brand modular scale of $8, 16, 24, 32, 40, 48, 64\text{px}$. Avoid arbitrary margin or padding values.

HTML & CSS Layout Principles

Table Nesting Philosophy:

Wrapper Table (100% width, viewport background color)
↓
Container Table (640px fixed width, white background, centered)
↓
Section Table (100% width, modular wrapper)
↓
Module Table (Specific content layouts: grids, heros, banners)
↓
Individual Cell (Content: text, image, links with inline styling)


Inline CSS Styling Example:
Every structural text block, cell, and link must carry its styles inline. Global styles cannot be relied upon due to client scrubbing.

<td style="padding: 24px; font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 24px; color: #222222;">
  Live content goes here...
</td>


Typography Standards

Primary Font Stack: Arial, Helvetica, sans-serif. Use fallbacks gracefully.

Size Hierarchy:

Heading: $32\text{px}$ (Line-height: $38\text{px}$ - $120\%$)

Subheading: $24\text{px}$ (Line-height: $30\text{px}$ - $125\%$)

Body Copy: $16\text{px}$ (Line-height: $24\text{px}$ - $150\%$)

Small Copy: $14\text{px}$ (Line-height: $20\text{px}$ - $140\%$)

Legal / T&Cs: $12\text{px}$ (Line-height: $16\text{px}$ - $133\%$)

Colors

Never hardcode custom color values. Always maps elements strictly to the approved design system palette:

Primary / Core Text: #222222

Secondary / Editorial Copy: #444444

Brand Highlight Background: #f4f1ed

Primary CTA / Dark Backgrounds: #000000

Primary CTA Text / Spacing Backgrounds: #ffffff

Divider Lines / Borders: #dddddd

USP / Accent Backgrounds: #f2f2f2

Image Specifications & Export Rules

Inline Styles: Every image must explicitly carry these styles to prevent layout breakage across Outlook, Gmail, and Apple Mail:

style="display: block; width: 100%; max-width: {intended_width}px; height: auto; border: 0;"


Export Formats: PNG, JPG, or WebP.

Retina Resolution: Export assets at exactly $2\times$ their intended rendering display dimensions (e.g., $1280\text{px}$ width for a $640\text{px}$ hero banner display). Set the HTML physical width attribute to the $1\times$ desktop scale.

Compression Target: Every individual image asset should remain under $200\text{KB}$ where possible to minimize loading lag.

Accessibility Best Practices

Alternative Text: Provide detailed, readable alt text representing the context or call to action on the image. Avoid tags like "Hero Banner" or "Image 1".

Decorative Assets: Set empty alt="" and add role="presentation" to purely decorative separators, backgrounds, or spacers.

Semantic Markup: Ensure structural tags and reading orders run strictly logical.

Contrast Standards: Ensure text colors satisfy readable contrast limits against their target cell backgrounds.

Quality Assurance Checklist

Before finalizing or deploying any generated HTML email package, visually and structurally verify the following:

[ ] Asset Retrieval: All referenced image sources (src) route to live, verified URLs.

[ ] Accessibility Compliance: Descriptive alt text is explicitly provided on all descriptive images.

[ ] Destination Links: Every link redirects safely to its correct target destination with tracking metrics cleanly appended.

[ ] Responsive Flow: The email flows gracefully across standard mobile widths ($320\text{px}$ to $480\text{px}$) and columns stack properly.

[ ] Desktop Layout: Layout remains locked at a crisp, centered $640\text{px}$ scale.

[ ] Legacy Client Rendering: Verify outlook conditional wrappers (<!--[if mso]>) compile cleanly.

[ ] No Raw Placeholders: Ensure no trace of double brackets {{...}} or default example URLs remain.

[ ] Dark Mode Usability: Brand assets, logos, and separators preserve legibility across reversed interfaces.

[ ] File Size Constraint: The total structural HTML file size is kept under $100\text{KB}$ to prevent Gmail clipping.

AI Implementation Rules & Instructions

When compiling a new email campaign from a supplied brief, artwork, and design asset:

Strict Modular Design: Formulate the email layout using ONLY the approved reusable fragments documented below.

No Custom Frameworks: Never introduce custom structural code, nested CSS frameworks, external classes, or responsive hacks outside this framework.

Strict HTML Standard: Maintain nesting patterns (Table ➔ TD ➔ Content) and enforce inline styling on every single content node.

Outlook & Gmail Prioritized: Always guarantee formatting stability under Outlook (using VML for buttons where applicable) and Gmail (relying strictly on inlined, clean styling classes).

Live Content Preservation: Use live HTML copy blocks wherever possible. Never drop live headings or copy fields into raw static image exports.

AI Code Review Checklist

Ensure the final produced HTML successfully answers:

[ ] Are all elements formatted strictly using nested tables?

[ ] Is every single style attribute declared directly inline?

[ ] Are structural responsive classes (class="stack-column") preserved?

[ ] Are Outlook specific VML structures correctly matched to their parent anchors?

[ ] Is there absolute zero use of CSS Grid, Flexbox, or absolute positions?

[ ] Are image width properties written cleanly in physical HTML attributes?

[ ] Are responsive viewport configurations declared clearly?

Brief and Asset Matching Process

Use this process to convert the supplied brief, artwork, copy, images and links into the reusable HTML email fragments in this repository.

1. Read the Full Brief

Before selecting a fragment or writing HTML, identify:

Required module order

Supplied heading and body copy

CTA wording

Destination URLs

Image filenames

Desktop and mobile variants

Background colours

Text alignment

Legal or offer wording

Required spacing

Do not invent missing copy, links, prices, discount codes, expiry dates or legal wording. Use clear placeholders where information has not been supplied:
{{HERO_IMAGE}}, {{HERO_URL}}, {{HERO_HEADING}}, {{HERO_COPY}}, {{HERO_CTA}}, {{OFFER_CODE}}, {{LEGAL_COPY}}

2. Create a Module Map

Match each section of the brief to one of the existing reusable fragments.
Example:

Hidden Preheader

Category Navigation

Full-Width Hero Image

Hero with Live Copy and CTA

Two-Column Image Layout

Editorial Copy Block

Offer Banner

USP Strip

Divider

Footer

Only use modules required by the brief. Do not add extra sections unless instructed.

3. Select the Correct Fragment

Use the fragment that best matches the supplied design:

One full-width linked image $\rightarrow$ Full-Width Hero Image

Image followed by heading, copy and CTA $\rightarrow$ Hero with Live Copy and CTA

Two equal images beside each other $\rightarrow$ Two-Column Image Layout

Image beside live text $\rightarrow$ Two-Column Image and Copy Layout

Two products beside each other $\rightarrow$ Two-Column Product Grid

Three products beside each other $\rightarrow$ Three-Column Product Grid

Centered heading, paragraph and text link $\rightarrow$ Full-Width Editorial Copy Block

Short promotional message on a solid background $\rightarrow$ Offer Banner

Horizontal category links $\rightarrow$ Category Navigation

Three service messages $\rightarrow$ USP Strip

Horizontal separating line $\rightarrow$ Divider

Controlled empty vertical space $\rightarrow$ Vertical Spacer

Do not recreate a module with custom HTML when an existing fragment already provides the required structure.

4. Match Images to the Correct Module

Match each supplied image to the section described in the brief. Check:

Visible image content

Filename

Dimensions

Position in the approved design

Associated copy

Associated URL

The approved design and brief take priority over unclear filenames. Every image must retain its original aspect ratio. Always apply standard dynamic baseline styling:

style="display:block; width:100%; max-width:640px; height:auto; border:0;"


Do not stretch an image by setting conflicting width and height values.

5. Match Image Width to the Fragment

Use image dimensions that suit the selected module:

Full-width module $\rightarrow$ Maximum displayed width: 640px

Two-column module $\rightarrow$ Maximum displayed width: approximately 320px per image

Three-column module $\rightarrow$ Maximum displayed width: approximately 201px per image

6. Use Live Text Where the Fragment Provides It

When the selected fragment contains HTML headings, paragraphs, prices or CTAs, use the approved copy as live text.
Do not replace live text with an image unless the supplied artwork already contains the approved typography as part of the image. Do not duplicate the same wording in both the image and the live HTML unless the approved design requires it.

7. Match Links to the Correct Elements

Every linked image and CTA must use the URL supplied for that section. The following elements should normally share the same destination:

Hero image $\rightarrow$ Hero landing-page URL

Hero CTA $\rightarrow$ Hero landing-page URL

Category image $\rightarrow$ Relevant category URL

Category CTA $\rightarrow$ Relevant category URL

Product image $\rightarrow$ Product detail URL

Product name or product CTA $\rightarrow$ Product detail URL

Do not use one generic URL for every section unless instructed.

8. Match Copy to the Correct Image

The copy must correspond with the visual content. For example, a bedding image must map strictly to bedding headers and URLs. Do not attach copy to an image based only on file order; verify the image content before assigning parameters.

9. Set Meaningful Alt Text

Use alt text that describes the destination or purpose of the image.

Good: alt="Shop new-season dresses at Freemans"

Avoid: alt="Hero image" or alt="Banner 01"

For decorative images: alt="" role="presentation"

Do not repeat a nearby heading word-for-word unless the image itself is also the main linked message.

10. Apply the Supplied Styling

Match the approved design by updating only the relevant inline values within the fragment (e.g., background-color, padding, text-align). Do not replace the core table structure, inline CSS conventions, or responsive classes.

11. Preserve Responsive Classes

Fragments using columns must retain the supplied responsive classes (class="stack-column"). The structural mobile layout styles depend directly on them. Use utility classes like mobile-padding, mobile-center, mobile-hide, or mobile-heading safely when the responsive layout dictates it.

12. Confirm Mobile Order

Columns stack in natural layout source HTML order (Left Column $\rightarrow$ Right Column). Arrange the HTML in the strict linear hierarchy you want them to stack on mobile devices. Do not rely on Flexbox, CSS Grid, or absolute positioning to fix order layout shifts.

13. Use the Correct Button Fragment

Use the standard table button for normal CTA requirements. Use the Outlook-compatible bulletproof button when a fixed button appearance is required in desktop Outlook. Keep the VML fallback URL and standard anchor href URLs perfectly synchronized.

14. Use Spacers and Dividers Deliberately

Use the Vertical Spacer fragment only when the approved design requires fixed vertical spacing between modules. Always change all three vertical metrics synchronously (height="32" style="height:32px; line-height:32px;"). Update line color or structural weights cleanly on Dividers.

15. Handle Missing Information

Use named placeholders instead of guessing. Do not publish the final email while placeholders remain unresolved. Search the final HTML output for any trace of raw {{ brackets or standard base setup data like example.com or £39.99 before finalizing.

16. Verify Every Fragment

Before completing the email, systematically check each module against the brief's parameters for correct structural alignment, responsive styling preservation, and data integrity.

Reusable Fragments

Base Responsive Mobile CSS

Include this in the <head> of the master layout template.

<style>
  body,
  table,
  td,
  a {
    -webkit-text-size-adjust: 100%;
    -ms-text-size-adjust: 100%;
  }

  table,
  td {
    mso-table-lspace: 0pt;
    mso-table-rspace: 0pt;
  }

  img {
    -ms-interpolation-mode: bicubic;
  }

  table {
    border-collapse: collapse !important;
  }

  body {
    margin: 0 !important;
    padding: 0 !important;
    width: 100% !important;
  }

  @media only screen and (max-width: 640px) {
    .email-container {
      width: 100% !important;
      max-width: 100% !important;
    }

    .stack-column {
      display: block !important;
      width: 100% !important;
      max-width: 100% !important;
    }

    .stack-column img {
      width: 100% !important;
      max-width: 100% !important;
      height: auto !important;
    }

    .mobile-padding {
      padding-left: 20px !important;
      padding-right: 20px !important;
    }

    .mobile-center {
      text-align: center !important;
    }

    .mobile-full-width {
      width: 100% !important;
    }

    .mobile-hide {
      display: none !important;
      width: 0 !important;
      height: 0 !important;
      overflow: hidden !important;
    }

    .mobile-heading {
      font-size: 26px !important;
      line-height: 32px !important;
    }

    .mobile-body {
      font-size: 16px !important;
      line-height: 24px !important;
    }
  }
</style>


Hidden Preheader

<!-- PREHEADER -->
<div style="display: none; max-height: 0; max-width: 0; overflow: hidden; opacity: 0; color: transparent; font-size: 1px; line-height: 1px; mso-hide: all;">
  Discover the latest styles, offers and home updates from Freemans.
</div>

<div style="display: none; max-height: 0; overflow: hidden; mso-hide: all;">
  &nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;
</div>
<!-- /PREHEADER -->


Category Navigation

<!-- CATEGORY NAVIGATION -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0" style="background-color: #ffffff;">
  <tr>
    <td align="center" style="padding: 14px 8px; font-family: Arial, Helvetica, sans-serif; font-size: 14px; line-height: 20px;">
      <a href="[https://www.freemans.com/womens](https://www.freemans.com/womens)" target="_blank" style="display: inline-block; padding: 6px 10px; color: #222222; font-weight: bold; text-decoration: none;">Womenswear</a>
      <a href="[https://www.freemans.com/mens](https://www.freemans.com/mens)" target="_blank" style="display: inline-block; padding: 6px 10px; color: #222222; font-weight: bold; text-decoration: none;">Menswear</a>
      <a href="[https://www.freemans.com/home](https://www.freemans.com/home)" target="_blank" style="display: inline-block; padding: 6px 10px; color: #222222; font-weight: bold; text-decoration: none;">Home</a>
      <a href="[https://www.freemans.com/electricals](https://www.freemans.com/electricals)" target="_blank" style="display: inline-block; padding: 6px 10px; color: #222222; font-weight: bold; text-decoration: none;">Electricals</a>
    </td>
  </tr>
</table>
<!-- /CATEGORY NAVIGATION -->


Full-Width Hero Image

<!-- HERO IMAGE -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
  <tr>
    <td align="center">
      <a href="[https://www.freemans.com/](https://www.freemans.com/)" target="_blank" style="text-decoration: none;">
        <img src="[https://example.com/images/hero.jpg](https://example.com/images/hero.jpg)" width="640" alt="Discover the latest Freemans collection" style="display: block; width: 100%; max-width: 640px; height: auto; border: 0;">
      </a>
    </td>
  </tr>
</table>
<!-- /HERO IMAGE -->


Hero with Live Copy and CTA

<!-- HERO COPY -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0" style="background-color: #f4f1ed;">
  <tr>
    <td align="center" style="padding: 32px 24px 40px; font-family: Arial, Helvetica, sans-serif;">
      <h1 style="margin: 0 0 16px; font-family: Arial, Helvetica, sans-serif; font-size: 32px; line-height: 38px; font-weight: bold; color: #222222;">New season, new favourites</h1>
      <p style="margin: 0 0 24px; font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 24px; color: #444444;">Refresh your wardrobe with the latest styles from Freemans.</p>
      <table role="presentation" cellspacing="0" cellpadding="0" border="0">
        <tr>
          <td align="center" bgcolor="#000000" style="border-radius: 0;">
            <a href="[https://www.freemans.com/](https://www.freemans.com/)" target="_blank" style="display: inline-block; padding: 14px 28px; font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 20px; font-weight: bold; color: #ffffff; text-decoration: none;">Shop now</a>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>
<!-- /HERO COPY -->


Offer Banner

<!-- OFFER BANNER -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0" style="background-color: #222222;">
  <tr>
    <td align="center" style="padding: 20px 24px; font-family: Arial, Helvetica, sans-serif;">
      <p style="margin: 0; font-family: Arial, Helvetica, sans-serif; font-size: 18px; line-height: 24px; font-weight: bold; color: #ffffff;">
        20% off selected styles with code <span style="white-space: nowrap;">STYLE20</span>
      </p>
    </td>
  </tr>
</table>
<!-- /OFFER BANNER -->


Outlook-Compatible Bulletproof Button

<!-- BULLETPROOF CTA -->
<table role="presentation" cellspacing="0" cellpadding="0" border="0" align="center">
  <tr>
    <td align="center">
      <!--[if mso]>
      <v:roundrect xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" href="[https://www.freemans.com/](https://www.freemans.com/)" style="height: 48px; v-text-anchor: middle; width: 180px;" arcsize="0%" strokecolor="#000000" fillcolor="#000000">
        <w:anchorlock/>
        <center style="color: #ffffff; font-family: Arial, Helvetica, sans-serif; font-size: 16px; font-weight: bold;">Shop now</center>
      </v:roundrect>
      <![endif]-->
      <!--[if !mso]><!-->
      <a href="[https://www.freemans.com/](https://www.freemans.com/)" target="_blank" style="display: inline-block; min-width: 132px; padding: 14px 24px; background-color: #000000; border: 1px solid #000000; font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 18px; font-weight: bold; color: #ffffff; text-align: center; text-decoration: none;">Shop now</a>
      <!--<![endif]-->
    </td>
  </tr>
</table>
<!-- /BULLETPROOF CTA -->


Two-Column Image Layout

<!-- TWO-COLUMN IMAGE LAYOUT -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
  <tr>
    <td class="stack-column" width="50%" valign="top" style="width: 50%;">
      <a href="[https://www.freemans.com/category-one](https://www.freemans.com/category-one)" target="_blank" style="text-decoration: none;">
        <img src="[https://example.com/images/category-one.jpg](https://example.com/images/category-one.jpg)" width="320" alt="Shop category one" style="display: block; width: 100%; max-width: 320px; height: auto; border: 0;">
      </a>
    </td>
    <td class="stack-column" width="50%" valign="top" style="width: 50%;">
      <a href="[https://www.freemans.com/category-two](https://www.freemans.com/category-two)" target="_blank" style="text-decoration: none;">
        <img src="[https://example.com/images/category-two.jpg](https://example.com/images/category-two.jpg)" width="320" alt="Shop category two" style="display: block; width: 100%; max-width: 320px; height: auto; border: 0;">
      </a>
    </td>
  </tr>
</table>
<!-- /TWO-COLUMN IMAGE LAYOUT -->


Two-Column Image and Copy Layout

<!-- IMAGE AND COPY SPLIT -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
  <tr>
    <td class="stack-column" width="50%" valign="middle" style="width: 50%;">
      <img src="[https://example.com/images/editorial.jpg](https://example.com/images/editorial.jpg)" width="320" alt="Seasonal fashion from Freemans" style="display: block; width: 100%; max-width: 320px; height: auto; border: 0;">
    </td>
    <td class="stack-column" width="50%" valign="middle" style="width: 50%; padding: 32px; font-family: Arial, Helvetica, sans-serif; background-color: #f4f1ed;">
      <h2 style="margin: 0 0 12px; font-family: Arial, Helvetica, sans-serif; font-size: 24px; line-height: 30px; font-weight: bold; color: #222222;">Style for every day</h2>
      <p style="margin: 0 0 20px; font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 24px; color: #444444;">Easy-to-wear pieces designed to fit effortlessly into your wardrobe.</p>
      <a href="[https://www.freemans.com/](https://www.freemans.com/)" target="_blank" style="font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 20px; font-weight: bold; color: #222222; text-decoration: underline;">Shop the collection</a>
    </td>
  </tr>
</table>
<!-- /IMAGE AND COPY SPLIT -->


Two-Column Product Grid

<!-- TWO-COLUMN PRODUCT GRID -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
  <tr>
    <td class="stack-column" width="50%" valign="top" style="width: 50%; padding: 0 8px 24px 0;">
      <table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
        <tr>
          <td align="center">
            <a href="[https://www.freemans.com/product-one](https://www.freemans.com/product-one)" target="_blank" style="text-decoration: none;">
              <img src="[https://example.com/images/product-one.jpg](https://example.com/images/product-one.jpg)" width="304" alt="Product one" style="display: block; width: 100%; max-width: 304px; height: auto; border: 0;">
            </a>
          </td>
        </tr>
        <tr>
          <td align="center" style="padding: 16px 12px 0; font-family: Arial, Helvetica, sans-serif;">
            <p style="margin: 0 0 6px; font-size: 16px; line-height: 22px; font-weight: bold; color: #222222;">Product name</p>
            <p style="margin: 0 0 14px; font-size: 16px; line-height: 22px; color: #222222;">£39.99</p>
            <a href="[https://www.freemans.com/product-one](https://www.freemans.com/product-one)" target="_blank" style="font-size: 15px; line-height: 20px; font-weight: bold; color: #222222; text-decoration: underline;">Shop now</a>
          </td>
        </tr>
      </table>
    </td>
    <td class="stack-column" width="50%" valign="top" style="width: 50%; padding: 0 0 24px 8px;">
      <table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
        <tr>
          <td align="center">
            <a href="[https://www.freemans.com/product-two](https://www.freemans.com/product-two)" target="_blank" style="text-decoration: none;">
              <img src="[https://example.com/images/product-two.jpg](https://example.com/images/product-two.jpg)" width="304" alt="Product two" style="display: block; width: 100%; max-width: 304px; height: auto; border: 0;">
            </a>
          </td>
        </tr>
        <tr>
          <td align="center" style="padding: 16px 12px 0; font-family: Arial, Helvetica, sans-serif;">
            <p style="margin: 0 0 6px; font-size: 16px; line-height: 22px; font-weight: bold; color: #222222;">Product name</p>
            <p style="margin: 0 0 14px; font-size: 16px; line-height: 22px; color: #222222;">£49.99</p>
            <a href="[https://www.freemans.com/product-two](https://www.freemans.com/product-two)" target="_blank" style="font-size: 15px; line-height: 20px; font-weight: bold; color: #222222; text-decoration: underline;">Shop now</a>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>
<!-- /TWO-COLUMN PRODUCT GRID -->


Three-Column Product Grid

<!-- THREE-COLUMN PRODUCT GRID -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
  <tr>
    <td class="stack-column" width="33.33%" valign="top" style="width: 33.33%; padding: 0 6px;">
      <a href="[https://www.freemans.com/product-one](https://www.freemans.com/product-one)" target="_blank" style="text-decoration: none;">
        <img src="[https://example.com/images/product-one.jpg](https://example.com/images/product-one.jpg)" width="201" alt="Product one" style="display: block; width: 100%; max-width: 201px; height: auto; border: 0;">
      </a>
      <p style="margin: 12px 0 4px; font-family: Arial, Helvetica, sans-serif; font-size: 15px; line-height: 21px; font-weight: bold; color: #222222; text-align: center;">Product one</p>
      <p style="margin: 0; font-family: Arial, Helvetica, sans-serif; font-size: 15px; line-height: 21px; color: #222222; text-align: center;">£29.99</p>
    </td>
    <td class="stack-column" width="33.33%" valign="top" style="width: 33.33%; padding: 0 6px;">
      <a href="[https://www.freemans.com/product-two](https://www.freemans.com/product-two)" target="_blank" style="text-decoration: none;">
        <img src="[https://example.com/images/product-two.jpg](https://example.com/images/product-two.jpg)" width="201" alt="Product two" style="display: block; width: 100%; max-width: 201px; height: auto; border: 0;">
      </a>
      <p style="margin: 12px 0 4px; font-family: Arial, Helvetica, sans-serif; font-size: 15px; line-height: 21px; font-weight: bold; color: #222222; text-align: center;">Product two</p>
      <p style="margin: 0; font-family: Arial, Helvetica, sans-serif; font-size: 15px; line-height: 21px; color: #222222; text-align: center;">£34.99</p>
    </td>
    <td class="stack-column" width="33.33%" valign="top" style="width: 33.33%; padding: 0 6px;">
      <a href="[https://www.freemans.com/product-three](https://www.freemans.com/product-three)" target="_blank" style="text-decoration: none;">
        <img src="[https://example.com/images/product-three.jpg](https://example.com/images/product-three.jpg)" width="201" alt="Product three" style="display: block; width: 100%; max-width: 201px; height: auto; border: 0;">
      </a>
      <p style="margin: 12px 0 4px; font-family: Arial, Helvetica, sans-serif; font-size: 15px; line-height: 21px; font-weight: bold; color: #222222; text-align: center;">Product three</p>
      <p style="margin: 0; font-family: Arial, Helvetica, sans-serif; font-size: 15px; line-height: 21px; color: #222222; text-align: center;">£44.99</p>
    </td>
  </tr>
</table>
<!-- /THREE-COLUMN PRODUCT GRID -->


Full-Width Editorial Copy Block

<!-- EDITORIAL COPY BLOCK -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0" style="background-color: #ffffff;">
  <tr>
    <td align="center" style="padding: 40px 32px; font-family: Arial, Helvetica, sans-serif;">
      <h2 style="margin: 0 0 16px; font-family: Arial, Helvetica, sans-serif; font-size: 28px; line-height: 34px; font-weight: bold; color: #222222;">Find your new-season look</h2>
      <p style="margin: 0 auto 24px; max-width: 520px; font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 24px; color: #444444;">Explore easy layers, standout prints and everyday favourites designed to make getting dressed feel effortless.</p>
      <a href="[https://www.freemans.com/](https://www.freemans.com/)" target="_blank" style="font-family: Arial, Helvetica, sans-serif; font-size: 16px; line-height: 20px; font-weight: bold; color: #222222; text-decoration: underline;">Discover more</a>
    </td>
  </tr>
</table>
<!-- /EDITORIAL COPY BLOCK -->


USP Strip

<!-- USP STRIP -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0" style="background-color: #f2f2f2;">
  <tr>
    <td class="stack-column" width="33.33%" align="center" valign="top" style="width: 33.33%; padding: 20px 12px; font-family: Arial, Helvetica, sans-serif;">
      <p style="margin: 0; font-size: 14px; line-height: 20px; font-weight: bold; color: #222222;">Flexible ways to pay</p>
    </td>
    <td class="stack-column" width="33.33%" align="center" valign="top" style="width: 33.33%; padding: 20px 12px; font-family: Arial, Helvetica, sans-serif;">
      <p style="margin: 0; font-size: 14px; line-height: 20px; font-weight: bold; color: #222222;">Easy returns</p>
    </td>
    <td class="stack-column" width="33.33%" align="center" valign="top" style="width: 33.33%; padding: 20px 12px; font-family: Arial, Helvetica, sans-serif;">
      <p style="margin: 0; font-size: 14px; line-height: 20px; font-weight: bold; color: #222222;">Shop trusted brands</p>
    </td>
  </tr>
</table>
<!-- /USP STRIP -->


Divider

<!-- DIVIDER -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
  <tr>
    <td style="height: 1px; font-size: 1px; line-height: 1px; background-color: #dddddd;">&nbsp;</td>
  </tr>
</table>
<!-- /DIVIDER -->


Vertical Spacer

<!-- SPACER -->
<table role="presentation" width="100%" cellspacing="0" cellpadding="0" border="0">
  <tr>
    <td height="24" style="height: 24px; font-size: 1px; line-height: 24px;">&nbsp;</td>
  </tr>
</table>
<!-- /SPACER -->
