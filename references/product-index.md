# Product Rule Index

Use one product rule per product direction. Do not merge unrelated product logic into one rule.

## Current Product Directions

- `digital_signage`: small indoor digital signage hardware. Customer must bring CMS/content publishing/screen management/project delivery. See `digital-signage-rules.md`.
- `scanner`: plug-and-play barcode scanner / barcode reader / Auto-ID hardware. Customer does not need self-developed software. See `scanner-rules.md`.
- `pos`: Windows POS all-in-one / cashier hardware / customized self-ordering kiosk direction. Use `pos-rules.md`; `pos-rules-template.md` is only the old blank intake template.

## Adding A New Product

Create `references/<product>-rules.md` with:

1. Product boundary: what the company sells and does not sell.
2. High-score customer types.
3. Medium/low-score customer types.
4. Exclusion rules.
5. Apollo first-layer recall keywords and industries.
6. Agent judgement examples.
7. Field writing style for product direction, fit reason, cut-in angle, and unsuitable reason.

Update this index after adding the rule.

Keep the generic scripts unchanged unless the workbook schema changes.
