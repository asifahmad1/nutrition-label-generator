# Nutrition Facts Label Generator v1.0 — Test Report & Wix Listing

**File:** `~/workspace/your_files/nutrition-label-generator/index.html` (32,441 bytes — well under the 150 KB limit)
**Version:** 1.0 · **Built:** 20 Oct 2026 · **Creator:** Dr. Asif Ahmad (Asif SaaS Studio)

## Short description
Build a recipe from ingredients and get a professional US FDA-style Nutrition Facts label. A built-in reference database of 38 common ingredients (values per 100 g) covers dairy, oils, eggs, meats, grains, fruits, vegetables, legumes, nuts and sweeteners — and you can add your own ingredients from a data sheet (milk powder, protein powder, your own flour blend…). Set the serving size text and servings per container; the app totals the recipe, divides per serving, applies the official FDA Daily Values and the FDA label rounding rules, and renders the classic black-and-white label. Export as a high-resolution PNG (3×), an SVG with real text, or a printable standalone HTML file. A detail table also shows exact unrounded values per serving and per 100 g.

## Wix SaasProducts listing (ready to paste)
- **Title:** Nutrition Facts Label Generator
- **Category:** Health
- **Slug:** `nutrition-label-generator`
- **Summary:** Turn recipes into FDA-style Nutrition Facts labels — 38-ingredient reference database, custom ingredients, official Daily Values & FDA rounding, PNG/SVG/printable exports.
- **Version:** 1.0 · **Demo:** No

## Accuracy & honesty notes (also shown in the app)
- Ingredient values are **standard reference values (USDA-style)** for drafting, teaching and product development. A label used on a commercial product must be based on **laboratory analysis or a verified database for your exact ingredients** — the app says this on the preview card.
- The label format, Daily Values (21 CFR 101.9) and rounding conventions follow the current US FDA rules as simplified in the documentation (e.g. calories to the nearest 5/10, fat to 0.5 g steps, %DV tiers for vitamins/minerals). **Protein %DV is omitted**, as on standard FDA labels when no protein claim is made.
- "Added sugars" follows the FDA idea: sugars from added sweeteners count; sugars naturally in whole fruit (e.g. dates, banana) do not.
- Other countries use different formats (EU per-100 g tables, Pakistani/PSQCA rules) — the detail table's per-100 g column helps there, but this generator's label itself is the US format. No backend or API key is needed for anything in v1; a future verified-database lookup (e.g. USDA FoodData Central) would need an API key held by a small backend proxy — that is a possible v2, never faked in the page.

## What was tested (automated, against the shipped core)
**50 checks — all passed.**
- Every FDA rounding rule: calories (4→0, 37→35, 137→140), fat (0.4→0, 3.24→3, 7.6→8), grams (0.7→1), cholesterol (13→15 mg), sodium (147→150 mg), vitamin/mineral % tiers (23%→25%, 67%→70%)
- %DV maths (39 g fat = 50%, 1150 mg sodium = 50%)
- Two full recipes computed end-to-end: milk + sugar (label shows Calories 130, Total Fat 1.5 g / 2%, Carbs 27 g / 10%, Added Sugars 25 g / 50%, Sodium 20 mg, Protein 2 g — all hand-verified) and the trail-mix sample (Calories 220, Fat 11 g / 14%)
- Invalid rows (0 g / negative grams) are skipped safely; per-100 g figures verified (trail mix 431.4 kcal/100 g)
- Label model completeness (21 rows in FDA order) and SVG generation; database integrity (38 ingredients × 15 nutrient values, none negative)

## Testing checklist (after you upload it to the site)
1. Open the live page — the sample trail-mix recipe is loaded and the label shows **Calories 220**, servings line "4 servings per container / 1 pack (50 g)".
2. Change servings per container to 2 — calories double to 430 and every value rescales; change it back to 4.
3. Add "Granulated sugar" at 100 g from the dropdown, then remove it with ✕ — the label follows each step.
4. Set an ingredient's grams to 0 — a red warning appears (amounts must be above 0 g).
5. Add a custom ingredient (name + a few per-100 g values) — it joins the recipe and the dropdown for reuse.
6. Compare the label against the detail table — label values are the FDA-rounded versions of the exact figures.
7. Download all three exports: PNG (crisp 3× label), SVG (opens in a browser), printable HTML (a clean label page you can print or save as PDF from the browser).
8. Check on your phone — the label sits below the builder and stays fully readable.

## Upload steps (Wix CMS — same as the other tools)
1. Wix dashboard → CMS → **SaasProducts** → Add Item.
2. Fill the listing fields above; paste the full contents of `index.html` into **appHtml**.
3. Set **published** on, save, then open the live app page and run the checklist above.
