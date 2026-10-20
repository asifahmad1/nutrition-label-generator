# Nutrition Facts Label Generator

By **Dr. Asif Ahmad** — Asif SaaS Studio

Category **Health** · Version **1.0** · MIT License

Build a recipe from ingredients and get a professional US FDA-style Nutrition Facts label — entirely in your browser.

## Run it

Open `index.html` in any modern browser, or serve this folder with any static host. No build step, no dependencies, no server, no account — everything works offline.

## What it does

- **Recipe builder with a 38-ingredient reference database** — dairy, oils, eggs, meats, grains, fruits, vegetables, legumes, nuts and sweeteners, each with 15 nutrient values stated per 100 g (USDA-style reference values).
- **Custom ingredients** — add your own from a data sheet (milk powder, protein powder, your flour blend…) using the same per-100 g convention; they join the recipe and the dropdown for reuse.
- **Serving size + servings per container** — printed on the label exactly as you type them, with an optional "about".
- **Official FDA Daily Values and rounding applied to the classic label** — Daily Values per 21 CFR 101.9 (fat 78 g, sodium 2300 mg, carbs 275 g…) and the FDA label rounding rules (calories to the nearest 5/10, fat in 0.5 g steps, sodium tiers, vitamin/mineral % tiers), rendered in the standard black-and-white vertical format.
- **Exact detail table** — unrounded values per serving *and* per 100 g beside the label, so you always see what the rounding did.
- **Exports** — high-resolution PNG (3× canvas), SVG with real text, and a printable standalone HTML label page — all generated from one shared label model, so they can never disagree.

## An honest note

The ingredient values are **standard reference values for drafting, teaching and product development**. A label used on a commercial product must be based on **laboratory analysis or a verified database for your exact ingredients**. The label format is the **US format**; other countries use different layouts (the per-100 g column helps there). **Protein %DV is omitted** from the label, as on standard FDA labels when no protein claim is made. A future verified-database lookup (e.g. USDA FoodData Central) would need an API key held by a small backend proxy — that is a possible v2, never faked in the page.

## Files

- `index.html` — the complete app, self-contained: all CSS and JavaScript inline, 32,441 bytes. No localStorage, no service workers, no browser permissions, no parent-window access — safe in a sandboxed iframe.
- `nutrition-label-generator-test-report.md` — the full test report with the Wix listing fields and the post-upload testing checklist.
- Documentation (PDF) → `docs/nutrition-label-generator-docs.pdf` — user guide & technical documentation (13 pages).

## Testing

50 automated checks run against the shipped PURE CORE — **all passed**: every FDA rounding rule at its boundaries (calories 4→0, 37→35, 137→140; fat 0.4→0, 7.6→8; sodium 147→150 mg; vitamin tiers 23%→25%, 67%→70%), %DV maths, invalid-row handling, label-model completeness (21 rows in FDA order), SVG generation, database integrity (38 ingredients × 15 values) — and **two full recipes hand-verified end-to-end**: milk + sugar prints Calories 130 with Added Sugars 25 g · 50%; the trail-mix sample prints Calories 220 with Total Fat 11 g · 14%.

## Documentation

Full documentation: `docs/nutrition-label-generator-docs.pdf` — the workflow, the ingredient database, the recipe maths, the FDA Daily Values and rounding tables, both worked examples, label anatomy, exports, accuracy & legal notes, validation rules, and the tested core verbatim in the appendix.

Created by Dr. Asif Ahmad · Asif SaaS Studio · v1.0
