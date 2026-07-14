# Outfit Builder Blocks

Use project templates first. Use these blocks only when no supplied block exists, or to validate a generated section against the known pattern.

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
