# Supplier catalogue preflight

I compared a simulated supplier update with a WooCommerce sample
catalogue so a store operator can review prices and problem rows.
This is a portfolio exercise, not paid client work.

## Data source

- Dataset: official WooCommerce sample product catalogue.
- Source: https://github.com/woocommerce/woocommerce/blob/trunk/plugins/woocommerce/sample-data/sample_products.csv
- Access date: 2026-10-10.
- Raw file: `data/sample_products.csv`, kept unchanged.

## Results

I included 19 physical products and variations from the 25 store rows.
The notebook records the 6 exclusions and the column meanings.

All 21 supplier rows appeared once:
- 17 exact matches: 2 price increases, 2 decreases and 13 unchanged prices.
- 2 duplicate supplier rows, 1 missing price and 1 unmatched SKU.

The four price changes need approval. The four problem rows need
investigation. Prices use sample price units, and no store was updated.

## Project files

- `project.ipynb`: inspection, simulated data, matching, QA and exports.
- `data/`: original catalogue, simulated supplier file and expected results.
- `outputs/`: Excel review workbook, review CSV and written summary.
- `PROJECT_BRIEF.md`: the agreed scope and rules.
- `CASE_STUDY.md`: a short explanation and example results.

Deliberate changes and their source store IDs are documented in
`data/expected_results.csv` and the M2 notebook cells.

## Run the notebook

Use Python with Pandas, NumPy, openpyxl and Jupyter support in VS Code.
Open the project folder, select the kernel, then restart and Run All.
Check the QA results before using the outputs.

M2 creates the simulated CSVs if they are missing. Existing copies
are kept. The notebook exports `review.csv` but keeps an existing
Excel workbook so its finished formatting is preserved. It does
not automatically refresh that existing workbook after data changes.

To recreate the data from scratch, use a separate project copy with
the original store CSV and no generated CSVs.

## Excel finishing steps

If the workbook is missing, the notebook creates the two initial sheets.
Finish that copy in Excel: make Review a table, freeze panes at C2,
show prices to two decimals, wrap explanations and adjust widths.
Use light red for exceptions and light yellow for proposed changes.

On Summary, count statuses from Review column J and price directions
from column I with COUNTIF. Count additional issues from column K.
For this 21-row sample, an exact-match formula is
`=COUNTIF(Review!J2:J22,"exact_match")`.
Add the written findings and verify all counts against Pandas before saving.
The written summary and case study are prepared manually from the results.

## AI assistance

I used AI (OpenAI Codex) to help generate the simulated data and
write parts of the code. I ran the code and checked the results.
