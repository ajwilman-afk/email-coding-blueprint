# Product Grid And Image Blocks

Use project templates first. Use these blocks only when no supplied block exists, or to validate a generated section against the known pattern.

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
