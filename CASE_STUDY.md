# Checking a Supplier Catalogue Update

## The problem

Before changing prices, a store operator needs to check that the
supplier’s product codes match the store’s products and that the
proposed prices are usable.

I built this project to practise making that comparison and giving
the operator a clear list of changes and problems to review.

This project uses WooCommerce official example catalogue data and
a simulated supplier update to demonstrate a supplier-catalogue
preflight workflow.

## The data

I used three files:

- sample_products.csv: the WooCommerce sample catalogue.
- supplier_update.csv: a simulated supplier file with 21 rows.
- expected_results.csv: the results each test case should produce.

The store file had 25 rows. I included 19 physical products and
variations. The other 6 rows was excluded because they were
outside the project’s scope.

## What I did

I used Pandas to check for missing and repeated SKUs, spaces around
SKUs and missing or invalid prices.

I matched the files using SKUs after trimming outer spaces.
I kept the original values and recorded the trimming in a note.

I gave each supplier row a status and only calculated price
differences where the match was unique and the prices were valid.
I checked the classifications against the expected results and
manually checked selected records against the source files.

## What I found

All 21 supplier rows appeared once in the review.

There were 17 exact matches: 2 proposed price increases,
2 decreases and 13 unchanged prices.

Four rows needed checking:
- Two sunglasses entries had the same SKU but different prices.
- The cap had no proposed price.
- The shoe-brush SKU was not in the included store catalogue.

A few examples from the review:

| SKU | Current price | Proposed price | Finding |
|---|---:|---:|---|
| woo-hoodie-with-logo | 45 | 45 | No change |
| woo-tshirt | 18 | 20 | Increase of 2 |
| woo-cap | 18 | Missing | Price needed |
| sim-new-shoe-brush | Not available | 12 | SKU not found |

## What the operator receives

The Excel workbook contain a summary and the full review.
It shows the proposed changes, problems and decisions needed.
The operator still needs to approve the four price changes
and resolve the four problem rows.

I also included a CSV of the review and a short written summary.

## Limits and AI use

The comparison uses case-sensitive SKUs. I did not use product
names to guess matches. Current prices came from Regular price,
and all prices use sample price units.

I used AI (OpenAI Codex) to help generate the simulated supplier
data and write parts of the code. I ran the code and checked
the results as I worked through the project.

This was a portfolio exercise, not paid client work.
No store prices were changed.