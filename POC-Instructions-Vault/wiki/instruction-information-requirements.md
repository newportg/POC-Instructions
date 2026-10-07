# Instruction Information Requirements

All the information an instruction needs to carry to describe the matter it relates to — and nothing else.

**Scope:** this is the information payload only. Authority and control are deliberately excluded: no authority to act, engagement/POA evidence, KYC/AML or conflict checks, no status or stage gates, no audit trail of variations. Those are listed under [Not covered here](#not-covered-here). Related entries: [[what-is-an-instruction]] (full concept, including authority and control), [[instruction-in-eu-crm-data-model]] (how the CRM stores each field).

Required markers reflect the CRM model where it flags fields as required.

## Instructing party

- Client name (person or organisation) — required
- Role — vendor, landlord, buyer, borrower, client (varies by instruction type)
- Party type — individual, company, trust (descriptive)
- Primary contact — name, phone, email
- Invoicing legal entity, where different from the client organisation — e.g. `kf_legalentityaccountid`
- Contact details of the client contact instructing (CRM: `kf_vendorcontactid`, `kf_landlordcontactid`, `kf_contactid` — required where present)

## Property

- Full address and title number — required
- Property register reference — `kf_propertyid` / `kf_respropertyid` — required
- Tenure — freehold or leasehold; for leasehold: term, ground rent, service charges
- Property type / sector — commercial class or residential attributes (bedrooms, bathrooms, furnishing, council tax)
- Known defects, restrictions, or planning issues

## Matter and transaction

- Service line the instruction belongs to — required (`kf_serviceline`)
- Transaction type — sale, purchase, letting (landlord/tenant rep), consultancy, development, debt/finance, property management, valuation
- Instruction type variant:
  - Sales — Sole Agency / Joint Sole Agency / Multi Agency / Private Treaty / Auction / Tender — required
  - Lettings — Sole Agency / Joint / Multi / Let Only / Let & Manage / Full Management — required
  - Valuation — purpose: Secured Lending / Fund Reporting / Acquisition / Disposal / Insurance / Tax / Financial Statements — required; basis: Market Value / Market Rent / Fair Value / DRC / Reinstatement — required
- Price or value — asking price (required for sales), guide price range, agreed asking rent (weekly required; monthly/annual calculated)
- Deposit and funding source — cash / mortgage / both
- Chain or dependencies on other transactions
- Currency of the transaction — required (`kf_currency`)

## Other parties

- Other side to the transaction and their representative (solicitor or agent)
- Broker, lender, and any third parties involved (tenant, applicant)

## Lender details (where applicable)

- Lender and relationship type (e.g. panel)
- Loan amount and product
- Conditions attached to the advance

## Scope of work

- What the professional is explicitly asked to do, and what is excluded
- Marketing scope for agency instructions — portals, photography, sole vs. multi-agency listing
- Report requirements for valuations — inspection needed, delivery deadline (see Dates)

## Commercial terms

- Fee basis — fixed fee or hourly rate, agreed fee (`kf_fee`)
- Commission percentage — required for sales and lettings (`kf_commissionpercent`), plus minimum commission where applicable
- Ongoing management fee percentage (Let & Manage / Full Management)
- Expected revenue (`kf_expectedrevenue`)
- Anticipated disbursements — searches, Land Registry fees
- Who is liable for the fees

## Dates

- Date instruction received — required (`kf_instructiondate`)
- Instruction term expiry (`kf_instructionexpiry`)
- Milestones relevant to the matter:
  - Sales — marketing launch, offer accepted, exchange, completion
  - Lettings — marketing launch, let agreed, tenancy start; minimum term and furnishing
  - Valuation — inspection date, report due (required), report issued

## Assignment and administration

- Assigned handler — negotiator or lead valuer — required (`kf_negotiator`, `kf_valuer`)
- Reviewer/second signatory where the service line uses one (`kf_reviewer`)
- Responsible office (`kf_owningoffice`, `kf_officebu`)
- Free-text notes and comments describing anything exceptional about the matter

## Outcomes recorded against the instruction

- Sales — achieved price, viewing count, offer count (rollups)
- Lettings — eventual tenant, agreed rent
- Valuation — assessed market value, market rent, yield applied, special assumptions
- Completion/termination facts — end date, and for withdrawals the reason (Client request / KF withdrawal / Completed / Other)

## Not covered here

Deliberately excluded — governance for acting on the instruction, not information about the matter:

- **Authority to act** — engagement letter, terms of business, POA or director authority, signed date
- **Compliance** — KYC/AML clearance, conflict checks, sanctions screening, source of funds
- **Process control** — status (Active/Completed/On Hold/Withdrawn), stage/BPF position, stage-gate rules
- **Audit** — instruction variations and their history

---

> **Note:** Field names follow the EU CRM model (`EU CRM Data Model.xlsx`); the groupings are domain-level, not a schema. Where the CRM and the general concept differ, the CRM required-flags are marked.
