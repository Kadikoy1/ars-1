# ARS-1 Deployment-Pattern Profiles

ARS-1 v0.2 supports three named deployment-pattern profiles. Each is a published reference profile with declared purpose codes, conditionality predicates, onward-delivery channels, and licensing posture. An operator MAY claim conformance with one or more profiles. The standard does not endorse or name specific commercial operators; conformance is a matter of meeting the published criteria.

## Institutional Disbursement Profile

**Use case.** Multilateral institutions (IMF, World Bank, IFC, regional development banks), sovereign agencies, large NGOs disbursing aid programmes, conditional cash transfer programmes, parametric disaster response, scholarship and humanitarian programmes, agentic loan facility drawdown and repayment.

**Originator tier.** AIS-1 Sovereign tier. Multilateral or sovereign-issued sponsor card with government-attested Verifiable Credential.

**Recipient tier.** AIS-1 Verified, typically issued in the field by an authorised onboarding partner (community organisation, central authority designate, or sovereign registry).

**Conditionality.** Heavily used. Oracle-driven for parametric flows (NOAA, regional meteorological agencies, official price feeds). Attestation-driven for conditional programmes (vaccination registries, school enrolment, proof-of-life).

**Purpose codes typically used.**
- `DTCT` — Direct-to-Citizen Transfer
- `COND` — Conditional Cash Transfer
- `PRAM` — Parametric Disaster Response
- `SCHL` — Scholarship Disbursement (or ISO `STDY`)
- `HMRT` — Humanitarian Emergency Relief (or ISO `CHAR`)
- `CLIM` — Climate Resilience Payment
- `HLTH` — Health-Conditional Transfer
- `AGLN` / `AGRP` — Agentic Loan Drawdown / Repayment (or ISO `LOAN` / `LOAR`)
- `DIAS` — Diaspora Coordinated Remittance (where multilateral co-funding present)

**Onward delivery.** Typically mobile money or bank credit in the recipient jurisdiction. Hardship-adjustment policy mandatory for volatile-currency corridors.

**Licensing.** Operators licensed under a jurisdiction-appropriate digital-asset business framework. Sandbox licences acceptable for pilot deployment.

**Compliance posture.** Full Travel Rule compliance with selective disclosure. Three-checkpoint sanctions screening. AML risk-rating by programme type and corridor.

---

## Commercial Remittance Profile

**Use case.** Diaspora P2P remittance, employer payroll (including gig and contract workers), marketplace settlement, B2B cross-border supplier payment, treasury-to-treasury transfers with full agentic envelope.

**Originator tier.** AIS-1 Verified or Basic tier individuals and small-to-medium businesses. Sender app onboards via standard KYC at registration.

**Recipient tier.** AIS-1 Verified, typically issued via a partner network — mobile-money operators, diaspora associations, retail remittance agents, or directly via the operator's onboarding flow.

**Conditionality.** Light or absent. Most commercial remittance flows are unconditional. Where conditionality is present, it is typically time-based (scheduled payroll, recurring transfers) or attestation-based (delivery confirmation for B2B settlement).

**Purpose codes typically used.**
- `RMSP` — Sender-Pays Personal Remittance
- `RMBP` — Business-Pays Personal Remittance (payroll, gig payout, marketplace)
- `RMTB` — Treasury / B2B Remittance
- ISO `FAMI` — Family Maintenance
- ISO `SALA` — Salary Payment
- ISO `SUPP` — Supplier Payment
- ISO `INTC` — Intra-Company Payment
- ISO `GIFT` — Gift
- `DIAS` — Diaspora Coordinated Remittance (pooled flows)

**Onward delivery.** Mobile money, bank credit, retail cash, or in-network spend. Hardship-adjustment policy recommended for corridors with volatile local currency.

**Licensing.** Operators licensed as money transmitters, payment institutions, or digital-asset businesses in their home jurisdiction. Typically multiple jurisdictional licences for cross-border operation.

**Compliance posture.** Travel Rule compliance for cross-border transfers above declared threshold. Tier-appropriate sanctions screening at all three checkpoints. AML risk-rating by sender history and corridor pattern.

---

## State-to-Citizen Profile

**Use case.** Sovereign welfare and public-sector disbursement: social benefits, pensions, tax refunds, public-sector salaries, emergency state aid, universal basic income or universal basic agent allocations.

**Originator tier.** AIS-1 Sovereign tier. State entity with government-attested sponsor card.

**Recipient tier.** AIS-1 Sovereign tier. Recipient agents issued by the national registry of the originating state, bound to the citizen's national ID.

**Conditionality.** Eligibility predicates verified against government attestations. Common patterns include proof-of-life (pension), enrolment status (education), employment status (unemployment benefit), tax-filing status (refund). Recurring time-based release typical.

**Purpose codes typically used.**
- ISO `BENE` — Benefits
- ISO `PENS` — Pension Payment
- ISO `TAXS` — Tax Payment (refund direction)
- ISO `GOVT` — Government Payment
- ISO `SALA` — Salary Payment (public-sector employees)
- `UBAA` — Universal Basic Agent Allocation
- `HLTH` — Health-Conditional Transfer

**Onward delivery.** Bank credit to recipient's domestic account, or CBDC-rail in-wallet credit, or domestic mobile money. Hardship adjustment typically not required (domestic currency only).

**Settlement.** May be in CBDC, central-bank-issued stablecoin, or domestic fiat rail. State operators are often the issuer of their own settlement instrument.

**Licensing.** State-operated; subject to constitutional and statutory authority rather than commercial licensing.

**Compliance posture.** Domestic flows only — Travel Rule typically not engaged. State-operated sanctions screening. Privacy considerations elevated given state visibility into citizen flows; selective-disclosure recommended.

---

## Profile Interoperability

The three profiles share the protocol. A recipient agent provisioned under one profile can receive transfers under another. A citizen who first received institutional disbursement aid can subsequently receive commercial diaspora remittance, and welfare from her own government — all to the same AIS-1 recipient agent, all in the same protocol format.

The recipient agent is profile-agnostic. The operator is profile-specific.

This is the network effect ARS-1 unlocks.
