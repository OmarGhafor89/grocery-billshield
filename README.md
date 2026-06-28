# grocery-billshield
Bill_Shield (Basket) — snap a grocery bill, and it reads, categorizes, and splits your spend by Bahrain VAT. No-code build: Web UI + n8n + Groq vision + Supabase.
# Bill_Shield — "Basket" 🧾
### Grocery bill spend tracker · 100xEngineers No-Code Hackathon (Track A)

Snap a photo of your grocery bill and instantly see where your money went —
items sorted into categories, with the Bahrain VAT split (0% staples vs 10% taxed).

**Live demo:** https://grocery-billshield.netlify.app/

## What it does
1. You upload a receipt photo on a simple web page.
2. The photo is sent to an n8n workflow (the engine).
3. Groq's vision model reads the bill into structured data (items, prices, VAT per line).
4. The workflow categorizes the items, computes the VAT-free vs taxed split, and
   runs a "needs review" check (flags the bill if the items don't add up to the total).
5. Everything is saved to Supabase, and the result is shown on a dashboard.

## The stack (all free tools)
- **Front end:** single HTML page (hosted on Netlify)
- **Engine:** n8n (no-code automation)
- **AI:** Groq vision model (reads the receipt)
- **Database:** Supabase (two tables: `bills` and `line_items`, linked by `bill_id`)

## Files in this repo
- `grocery_spend_tracker.html` — the front-end web page
- `n8n_workflow.json` — the full n8n workflow (import this into n8n to run the backend)

## The design idea
The tool only trusts what is printed on the bill (prices, the per-line VAT rate)
and is honest about what it guesses (item categories). It works best on grocery
bills that print VAT per line (e.g. Lulu). Restaurant bills that hide per-line VAT
are a known boundary.

## Built by
Omar Ghafor
