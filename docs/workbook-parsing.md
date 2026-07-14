# Workbook Parsing Guidance


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
