# Supplier catalogue review

I compared 21 simulated supplier rows with 19 included store
products and variations.

## Results

- 17 exact matches: 2 price increases, 2 decreases and
  13 unchanged prices.
- 2 supplier rows share the same sunglasses SKU.
- 1 supplier row has a missing proposed price.
- 1 supplier SKU was not found in the included store catalogue.
- No additional issues were found beyond the primary statuses.

All 21 supplier rows appear once in the review.

## Decisions needed

The operator needs to approve or reject the four proposed price
changes, confirm which sunglasses entry to use, provide the
missing price and investigate the unmatched SKU.

## Notes

Matching used case-sensitive SKUs after removing outer spaces.
Original SKUs were preserved, and the whitespace change was recorded.

Current prices came from Regular price. Proposed prices are
replacement selling prices. All prices use sample price units.

This project uses official WooCommerce example data and a simulated
supplier update. It does not represent paid client work.
No store prices were updated.