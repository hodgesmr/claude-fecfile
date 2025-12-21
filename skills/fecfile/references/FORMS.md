# FEC Form Types

## F1 / F1A - Statement of Organization

**Purpose**: Committee registration/organization details (not financial)

**Key Fields**:
- `committee_name`
- `committee_type`
- `committee_designation`
- `fec_committee_id_number`
- `treasurer_name`
- `treasurer_email`
- `custodian_name`
- `custodian_email`
- `committee_email`
- `committee_url` / `committee_website`
- `street_1`, `street_2`, `city`, `state`, `zip_code`
- `filing_frequency`

**F1 vs F1A**:
- **F1**: Original Statement of Organization - filed when a committee first registers with the FEC
- **F1A**: Amended Statement of Organization - filed when committee details change (address, treasurer, etc.)

**Notes**:
- Must be filed before a committee can raise or spend money
- Amendments must be filed within 10 days of changes

---

## F2 / F2A - Statement of Candidacy

**Purpose**: Candidate declaration (not financial)

**Key Fields**:
- `candidate_name`
- `office` - Office sought (House, Senate, President)
- `state`
- `district` - Congressional district (N/A for Senate/President)
- `party`
- `election_year`
- `election_type`
- `candidate_email` / `email`
- `candidate_url` / `candidate_website` / `website`
- `street_1`, `street_2`, `city`, `candidate_state`, `zip_code`

**F2 vs F2A**:
- **F2**: Original Statement of Candidacy - declares intent to run for federal office
- **F2A**: Amended Statement of Candidacy - updates candidate information

**Notes**:
- Filed by individuals seeking House, Senate, or Presidential office
- Must be filed within 15 days of becoming a candidate
- Amendments must be filed within 15 days of changes

---

## F3 / F3P / F3X - Financial Reports

**Purpose**: Financial report showing money raised and spent

### Form Variants
- **F3**: Report of Receipts and Disbursements (House/Senate campaigns)
- **F3P**: Report of Receipts and Disbursements (Presidential campaigns)
- **F3X**: Report of Receipts and Disbursements (PACs, party committees)

### Column A vs Column B

Financial reports have two sets of summary fields:
- **col_a_*** - This reporting period only
- **col_b_*** - Year-to-date (or election cycle) totals

Use col_a for period-specific analysis; use col_b to gauge overall committee activity.

### Cash Flow

| Field | Description |
|-------|-------------|
| `col_a_cash_on_hand_beginning_period` | Cash at start of period |
| `col_a_total_receipts` | Total money received |
| `col_a_subtotal` | Beginning cash + receipts |
| `col_a_total_disbursements` | Total money spent |
| `col_a_cash_on_hand_close_of_period` | Ending cash balance |
| `col_b_cash_on_hand_jan_1` | Cash at start of year |
| `col_b_year` | The reporting year |

### Receipts - Contributions

| Field | Description |
|-------|-------------|
| `col_a_individuals_itemized` | Itemized individual contributions ($200+) |
| `col_a_individuals_unitemized` | Unitemized individual contributions (<$200) |
| `col_a_individual_contribution_total` | Total individual contributions |
| `col_a_political_party_committees` | Contributions from party committees |
| `col_a_other_political_committees_pacs` | Contributions from PACs |
| `col_a_total_contributions` | Total of all contributions |

### Receipts - Other

| Field | Description |
|-------|-------------|
| `col_a_transfers_from_aff_other_party_cmttees` | Transfers from affiliated/party committees |
| `col_a_total_loans` | Total loans received |
| `col_a_total_loan_repayments_received` | Loan repayments received |
| `col_a_offsets_to_expenditures` | Refunds/rebates offsetting expenditures |
| `col_a_federal_refunds` | Refunds of federal contributions |
| `col_a_other_federal_receipts` | Other federal receipts |
| `col_a_total_federal_receipts` | Total federal receipts |

### Receipts - Non-Federal (Party Committees)

| Field | Description |
|-------|-------------|
| `col_a_transfers_from_nonfederal_h3` | Transfers from non-federal accounts |
| `col_a_levin_funds` | Levin fund receipts |
| `col_a_total_nonfederal_transfers` | Total non-federal transfers |

### Disbursements - Operating

| Field | Description |
|-------|-------------|
| `col_a_shared_operating_expenditures_federal` | Federal share of shared operating costs |
| `col_a_shared_operating_expenditures_nonfederal` | Non-federal share of shared operating costs |
| `col_a_other_federal_operating_expenditures` | Other federal operating expenditures |
| `col_a_total_operating_expenditures` | Total operating expenditures |
| `col_a_total_federal_operating_expenditures` | Total federal operating expenditures |

### Disbursements - Political Activity

| Field | Description |
|-------|-------------|
| `col_a_transfers_to_affiliated` | Transfers to affiliated committees |
| `col_a_contributions_to_candidates` | Contributions to federal candidates |
| `col_a_independent_expenditures` | Independent expenditures |
| `col_a_coordinated_expenditures_by_party_committees` | Coordinated party expenditures |

### Disbursements - Other

| Field | Description |
|-------|-------------|
| `col_a_total_loan_repayments_made` | Loan repayments made |
| `col_a_loans_made` | Loans made to others |
| `col_a_refunds_to_individuals` | Refunds to individual contributors |
| `col_a_refunds_to_party_committees` | Refunds to party committees |
| `col_a_refunds_to_other_committees` | Refunds to other committees |
| `col_a_total_refunds` | Total contribution refunds |
| `col_a_other_disbursements` | Other disbursements |
| `col_a_total_federal_disbursements` | Total federal disbursements |

### Federal Election Activity (Party Committees)

| Field | Description |
|-------|-------------|
| `col_a_federal_election_activity_federal_share` | Federal share of FEA |
| `col_a_federal_election_activity_levin_share` | Levin share of FEA |
| `col_a_federal_election_activity_all_federal` | All-federal FEA |
| `col_a_federal_election_activity_total` | Total federal election activity |

### Net Calculations

| Field | Description |
|-------|-------------|
| `col_a_net_contributions` | Contributions minus refunds |
| `col_a_total_offsets_to_expenditures` | Total offsets to operating expenditures |
| `col_a_net_operating_expenditures` | Operating expenditures minus offsets |

### Debts

| Field | Description |
|-------|-------------|
| `col_a_debts_to` | Money owed to the committee |
| `col_a_debts_by` | Money the committee owes |

**Coverage Period Fields**:
- `coverage_from_date` - Start of reporting period
- `coverage_through_date` - End of reporting period

**Amendment Fields**:
- `amendment_indicator` - 'A' for amendment, 'T' for termination, empty for original
- `previous_report_amendment_indicator` - Original filing ID if this is an amendment

**Itemizations**:
Financial reports include detailed itemizations in schedules:
- Schedule A: Contributions received
- Schedule B: Disbursements made
- Schedule C: Loans
- Schedule D: Debts
- Schedule E: Independent expenditures

See [SCHEDULES.md](SCHEDULES.md) for field mappings.

---

## F99 - Miscellaneous Text

**Purpose**: Miscellaneous text communications to the FEC

**Key Fields**:
- `fec_committee_id_number`
- `committee_name`
- `date_signed`
- `text` - The substantive content of the filing

**Common Uses**:
- Debt settlement notifications
- Schedule change requests
- Explanations of discrepancies
- General correspondence with the FEC

**Notes**:
- The `text` field contains the important information
- No financial data - focus on the written explanation
- Text content may be a string or list of text blocks
