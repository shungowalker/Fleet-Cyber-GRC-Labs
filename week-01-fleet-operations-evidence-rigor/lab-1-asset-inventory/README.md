# Lab 1: Heartland Freight Asset Inventory

**Objective:** Build an asset inventory for 15 fleet systems covering the full freight lifecycle (booking → dispatch → transit → delivery → billing). Assign an owner, data classification, operational criticality and a PCI DSS scope-review status to each, with written reasoning.

📄 **Files:** [Excel workbook](Heartland_Freight_Asset_Inventory_SMW.xlsx) · [PDF preview](Heartland_Freight_Asset_Inventory_SMW.pdf)

## Approach
- **Owners are accountable business roles**, separate from the IT technical custodian.
- **Classification and criticality are rated separately.** HR and Payroll hold Highly Confidential data but are Medium criticality, because freight keeps moving if they are briefly down.
- **No system is labeled "PCI compliant."** Suspected payment-card touchpoints are marked *Scope review needed*. "Out of scope" ratings are provisional until confirmed with data-flow diagrams and segmentation testing.
- **The workbook includes a Method & Legend sheet** with classification and criticality definitions and documented assumptions.

## Results
**15 assets** · Criticality: 6 High / 7 Medium / 2 Low · PCI: 5 Scope review needed / 2 Unknown / 8 Out of scope (provisional)

| Asset ID | Asset | Business owner | Classification | Criticality | PCI scope review |
|---|---|---|---|---|---|
| HF-001 | Dispatch TMS | Director of Operations (Dispatch) | Confidential | High | Unknown |
| HF-002 | Driver Mobile App | Driver Operations Manager | Confidential | Medium | Unknown |
| HF-003 | Payroll System | Payroll Manager (Finance) | Highly Confidential | Medium | Out of scope |
| HF-004 | Fuel Card Portal | Fleet Fuel Program Manager | Highly Confidential | Medium | Scope review needed |
| HF-005 | Microsoft 365 Email | IT Director | Confidential | High | Scope review needed |
| HF-006 | Customer Portal | VP of Sales & Customer Service | Confidential | High | Scope review needed |
| HF-007 | ELD Platform | Safety & Compliance Director | Confidential | High | Out of scope |
| HF-008 | Maintenance Shop Laptop | Maintenance Manager | Internal | Medium | Out of scope |
| HF-009 | QuickBooks Accounting | Chief Financial Officer (Controller as delegate) | Highly Confidential | Medium | Scope review needed |
| HF-010 | Fleet GPS Tracking | Fleet Operations Manager | Confidential | High | Out of scope |
| HF-011 | HR Database | HR Director | Highly Confidential | Medium | Out of scope |
| HF-012 | Yard CCTV | Facilities & Physical Security Manager | Confidential | Low | Out of scope |
| HF-013 | Vendor Remote Access | IT Director (with Vendor Management) | Highly Confidential | High | Scope review needed |
| HF-014 | Company Intranet | Internal Communications Manager (HR) | Internal | Low | Out of scope |
| HF-015 | Executive Email/Calendar | Chief Executive Officer (Executive Office); custodian IT Director | Highly Confidential | Medium | Out of scope |

## Notable judgment calls
- **Fuel Card Portal is likely PCI-adjacent, not automatically in scope.** Heartland is the fleet-card program customer, not a merchant accepting cards. Scope depends on whether the cards are brand-network (Visa/Mastercard) or proprietary, and whether full card numbers are stored.
- **Microsoft 365 email is flagged** as a common uncontrolled path for card data (customers emailing card numbers to pay invoices).
- **Vendor Remote Access is flagged** as a connected, security-impacting system (cf. PCI DSS v4.0 Req. 8.2.7).
- **The Customer Portal is flagged** for payment-page script controls even if payment is outsourced (PCI DSS v4.0 Req. 6.4.3 / 11.6.1).
