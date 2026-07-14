# Pricing And Offer Rules

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
