# Invoice Reconciliation: verification record

Review date: **10 November 2026**.

## Current mode

English/Arabic synthetic document packets. Fixture extraction and real text-layer parsing are distinct modes; image-only OCR remains unverified.

## Observed checks

- Nine database regressions and six browser checks passed in the current verification pass.
- A synthetic 25-set corpus includes price, quantity, unit, currency, duplication and hostile-file cases.
- Text-layer evaluation on the generated corpus recorded 517/542 header fields and 1,786/1,798 line cells matching after normalization.

These are scoped development checks, not an external audit or a claim of production adoption. Test fixtures are fictional. The private implementation workspace retains detailed test logs and provider receipts; this package carries the presentation evidence only.

## Explicit limits

Those extraction figures apply only to the generated corpus. Real supplier layouts, scanned OCR and human Arabic review are not established by these results.

## Package integrity

[Media manifest](../media-manifest.json) records the included filenames, byte sizes and SHA-256 digests. It identifies the exact presentation assets; a hash does not by itself prove the assertions above.
