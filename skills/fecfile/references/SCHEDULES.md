# FEC Schedule Field Mappings

## Schedule A - Individual Contributions

Itemized contributions received ($200+ threshold for itemization).

### Contributor Identity

| Field | Description |
|-------|-------------|
| `entity_type` | Entity type: IND (individual), ORG (organization), COM (committee) |
| `contributor_organization_name` | Organization name (if applicable) |
| `contributor_prefix` | Name prefix (Mr., Ms., Dr., etc.) |
| `contributor_last_name` | Individual's last name |
| `contributor_first_name` | Individual's first name |
| `contributor_middle_name` | Individual's middle name |
| `contributor_suffix` | Name suffix (Jr., Sr., etc.) |
| `contributor_employer` | Employer name |
| `contributor_occupation` | Occupation |

### Contributor Address

| Field | Description |
|-------|-------------|
| `contributor_street_1` | Street address line 1 |
| `contributor_street_2` | Street address line 2 |
| `contributor_city` | City |
| `contributor_state` | Two-letter state code |
| `contributor_zip_code` | ZIP code |

### Contribution Details

| Field | Description |
|-------|-------------|
| `contribution_amount` | Dollar amount of contribution |
| `contribution_date` | Date of contribution |
| `contribution_aggregate` | Year-to-date aggregate from this contributor |
| `contribution_purpose_descrip` | Purpose description |
| `election_code` | Election code |
| `memo_code` | Memo indicator |
| `memo_text_description` | Memo text |
| `transaction_id` | Unique transaction identifier |

### Conduit/Intermediary (Earmarked Contributions)

For contributions passed through intermediaries like ActBlue or WinRed:

| Field | Description |
|-------|-------------|
| `conduit_name` | Intermediary organization name |
| `conduit_street1` | Intermediary street address |
| `conduit_city` | Intermediary city |
| `conduit_state` | Intermediary state |
| `conduit_zip_code` | Intermediary ZIP code |

### Name Resolution

To get contributor name:
1. First check `contributor_organization_name`
2. If empty, construct from `contributor_last_name, contributor_first_name`

### Common Queries

- **Top contributors**: Sort by `contribution_amount` descending
- **State filtering**: Use exact match on `contributor_state`
- **Large contributions**: Filter where `contribution_amount` > threshold

---

## Schedule B - Disbursements/Expenditures

Itemized expenditures made ($200+ threshold for itemization).

### Payee Identity

| Field | Description |
|-------|-------------|
| `entity_type` | Entity type: IND (individual), ORG (organization), COM (committee) |
| `payee_organization_name` | Organization/vendor name |
| `payee_prefix` | Name prefix (Mr., Ms., Dr., etc.) |
| `payee_last_name` | Individual payee's last name |
| `payee_first_name` | Individual payee's first name |
| `payee_middle_name` | Individual payee's middle name |
| `payee_suffix` | Name suffix (Jr., Sr., etc.) |

### Payee Address

| Field | Description |
|-------|-------------|
| `payee_street_1` | Street address line 1 |
| `payee_street_2` | Street address line 2 |
| `payee_city` | City |
| `payee_state` | Two-letter state code |
| `payee_zip_code` | ZIP code |

### Expenditure Details

| Field | Description |
|-------|-------------|
| `expenditure_amount` | Dollar amount spent |
| `expenditure_date` | Date of expenditure |
| `expenditure_purpose_descrip` | Purpose/category of spending |
| `category_code` | FEC category code |
| `election_code` | Election code |
| `memo_code` | Memo indicator |
| `memo_text_description` | Memo text |
| `transaction_id_number` | Unique transaction identifier |

### Beneficiary (Contributions to Candidates/Committees)

For expenditures that benefit a specific candidate or committee:

| Field | Description |
|-------|-------------|
| `beneficiary_committee_fec_id` | Beneficiary committee FEC ID |
| `beneficiary_committee_name` | Beneficiary committee name |
| `beneficiary_candidate_fec_id` | Beneficiary candidate FEC ID |
| `beneficiary_candidate_last_name` | Beneficiary candidate last name |
| `beneficiary_candidate_first_name` | Beneficiary candidate first name |
| `beneficiary_candidate_office` | Office sought by candidate |
| `beneficiary_candidate_state` | Candidate's state |
| `beneficiary_candidate_district` | Candidate's district |

### Name Resolution

To get payee/recipient name:
1. First check `payee_organization_name`
2. If empty, construct from `payee_last_name, payee_first_name`

### Common Queries

- **Largest expenditures**: Sort by `expenditure_amount` descending
- **Spending by category**: Group by `expenditure_purpose_descrip`
- **Vendor analysis**: Group by `payee_organization_name`

---

## Schedule C - Loans

Loans received by the committee.

### Key Fields

| Field | Description |
|-------|-------------|
| `lender_organization_name` | Lending organization |
| `lender_last_name` | Individual lender's last name |
| `lender_first_name` | Individual lender's first name |
| `loan_amount` | Original loan amount |
| `loan_balance` | Outstanding balance |
| `loan_incurred_date` | Date loan was received |
| `loan_due_date` | Repayment due date |
| `loan_interest_rate` | Interest rate |

---

## Schedule D - Debts and Obligations

Debts owed by or to the committee.

### Key Fields

| Field | Description |
|-------|-------------|
| `creditor_organization_name` | Creditor organization |
| `creditor_last_name` | Individual creditor's last name |
| `creditor_first_name` | Individual creditor's first name |
| `debt_amount` | Amount of debt |
| `debt_incurred_date` | Date debt was incurred |
| `debt_purpose` | Purpose of debt |
| `outstanding_balance_beginning` | Balance at start of period |
| `outstanding_balance_close` | Balance at end of period |

---

## Schedule E - Independent Expenditures

Independent expenditures (not coordinated with campaigns).

### Key Fields

| Field | Description |
|-------|-------------|
| `payee_organization_name` | Payee organization |
| `payee_last_name` | Individual payee's last name |
| `payee_first_name` | Individual payee's first name |
| `expenditure_amount` | Amount spent |
| `expenditure_date` | Date of expenditure |
| `expenditure_purpose_descrip` | Purpose of expenditure |
| `support_oppose_code` | 'S' for support, 'O' for oppose |
| `candidate_name` | Candidate supported/opposed |
| `candidate_office` | Office sought by candidate |
| `candidate_state` | Candidate's state |
| `candidate_district` | Candidate's district |

---

## Data Quality Notes

- **Itemization Threshold**: Only contributions/expenditures of $200+ are required to be itemized
- **Smaller Amounts**: May appear in summary totals but not in schedule itemizations
- **Missing Fields**: Some fields may be empty - handle gracefully
- **Date Formats**: Usually YYYY-MM-DD, may include timezone info (ignore time portion)
- **Amount Formats**: Numeric values, may need formatting for display
