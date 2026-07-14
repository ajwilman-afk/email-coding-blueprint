# Core Content Blocks

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
