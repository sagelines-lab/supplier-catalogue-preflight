# Supplier Catalogue Preflight

## Aim

Compare a supplier update with a store catalogue before the operator
decides whether to change selling prices. Show which products match,
which prices change and which rows needs checking.

This is a portfolio simulation using official WooCommerce example
data and a simulated supplier update. It is not paid client work.

## Inputs and scope

Use the unchanged `sample_products.csv`, the simulated
`supplier_update.csv` and the independently planned `expected_results.csv`.
Keep the generation code and the notes about deliberate changes.

Include physical simple products and variations. Exclude parent,
grouped, external and virtual/downloadable rows.

The simulated supplier file contain ordinary matches, price changes,
a duplicate SKU, an unmatched SKU, a missing price and outer spaces
around one SKU. Keep these cases separate and give every supplier
row a unique identifier.

## Rules

- Keep original identifiers as text and retain traceability to source rows.
- Match exact, case-sensitive SKUs after trimming outer spaces in working fields.
- Record SKU trimming separately. Do not guess matches from names or choose a duplicate arbitrarily.
- Check blank and duplicate SKUs, invalid prices and excluded store rows before matching.
- Use Regular price as the current selling price, not Sale price or an inherited parent price.
- Treat proposed prices as replacement selling prices, not supplier costs.
- Prices must be present, numeric and greater than zero after consistent two-decimal rounding.
- Calculate proposed price minus current price only for valid, unique exact matches.

Assign one primary status in this order:
1. missing_or_invalid_sku
2. duplicate_supplier_sku
3. duplicate_store_sku
4. missing_store_sku
5. missing_or_invalid_price
6. exact_match

Record other detectable problems in `other_issues`.
An exact match does not approve a price change.

## Deliverables and checks

Deliver `supplier_catalogue_review.xlsx`, `review.csv` and `summary.md`
in `outputs/`. The workbook needs Summary and Review sheets with
clear reasons, actions, filters, frozen headers and simple formatting.

Every supplier row must appear once. Check classifications against
expected results, verify prices and secondary issues, and run the
duplicate-store and overlapping-issue examples. Manually check the
deliberate cases, whitespace case and five ordinary matches.

Excel formulas must calculate and agree with Pandas. Keep the original
inputs unchanged. Include a README with reproduction instructions
and a short case study with example inputs, results and limitations.

Use Python, Pandas and Excel. Prices use sample price units.
Do not connect to a live store, update prices or add extra technologies.
Disclose AI assistance.
