# ARANYA Digital Herbarium — tree QR pages

Project ARANYA · LIVE Foundation · West Singhbhum, Jharkhand

Har tagged ped par ek QR hota hai. Scan karne par `t.html?id=<Tree ID>` khulta hai,
jo Google Sheet (Tree Register) se us ped ka record padh kar dikhata hai.

## Files

| File | Kaam |
|---|---|
| `index.html` | Browse / search page — saare ped |
| `t.html` | Ek ped ka record. URL: `t.html?id=ARN-TNT-0001` |

## Setup — 2 cheez badalni hain

Dono files ke `<script>` ke shuru mein:

```js
const SHEET_CSV_URL = "";   // <- Sheet ka published CSV link
```

Sheet se CSV link lene ka tareeka:
**File → Share → Publish to web → "Tree Register" tab chuno → CSV → Publish**

`t.html` mein ek aur:

```js
const ENQUIRY_PHONE = "+91 ";   // tag par chhapa number
```

## Live URL

```
https://aranya.livefoundation.in/t.html?id=ARN-TNT-0001
```

Yahi URL har QR ke andar encode hota hai. **Agar yeh URL badla, to saare QR
dobara banane padenge** — isliye tag print karne se pehle URL final kar lena.

## DNS (GoDaddy)

| Type | Name | Value |
|---|---|---|
| CNAME | `aranya` | `<github-username>.github.io` |

Main site (livefoundation.in) GoDaddy Website Builder par hi rahegi — yeh
sirf ek subdomain hai, usse koi chhed-chhaad nahi.

## QR aur tag banane ke liye

Repo ke bahar `generate_tags.py` hai — Sheet ka CSV deke chalao:

```
pip install qrcode pillow reportlab
python3 generate_tags.py tree_register.csv
```

Output: `qr_codes/` (har ped ka PNG) aur `aranya_tree_tags.pdf` (print-ready,
85×55 mm, 8 tag per A4). QR error-correction level **H** par hain — 30% tak
kharab hone par bhi scan hote hain, jungle ke liye zaruri.
