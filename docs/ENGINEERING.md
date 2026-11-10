# Invoice Reconciliation: engineering notes

An invoice total can look plausible while individual lines disagree with the purchase order or delivery. This review desk makes the evidence and the exception visible before approval.

## System path

~~~mermaid
flowchart LR
  POAndInvoiceAndReceipt --> Extraction
  Extraction --> EvidenceLinkedFields
  EvidenceLinkedFields --> ThreeWayMatch
  ThreeWayMatch --> Exceptions
  Exceptions --> Reviewer
  Reviewer --> ApprovalAndReport
~~~

This diagram describes the demonstrated system boundary, not a production deployment topology.

## Decisions and tradeoffs

### Link values back to the document

Extracted fields and line items carry page-region references so a reviewer can inspect where a number came from.

### Make ambiguity explicit

Short delivery, changed price, unit mismatch and ambiguous dates become exceptions with reviewer dispositions instead of silent normalization.

### Keep review and approval separate

Corrections, document versions and final approval form an auditable case before report export.

## Review questions

- What evidence demonstrates **link values back to the document**, and what would fail without it?
- What evidence demonstrates **make ambiguity explicit**, and what would fail without it?
- What evidence demonstrates **keep review and approval separate**, and what would fail without it?

## Verification boundary

Nine database regressions and six browser checks passed in the current verification pass. A synthetic 25-set corpus includes price, quantity, unit, currency, duplication and hostile-file cases. Text-layer evaluation on the generated corpus recorded 517/542 header fields and 1,786/1,798 line cells matching after normalization.

Those extraction figures apply only to the generated corpus. Real supplier layouts, scanned OCR and human Arabic review are not established by these results.
