# Profile: Institutional Disbursement

**ARS-1 deployment-pattern profile · v0.2 reference**

## Use case

Multilateral and sovereign value transfer:

- IMF, World Bank, IFC and regional development bank disbursements
- Sovereign-to-citizen aid programmes
- Parametric disaster response (oracle-triggered)
- Conditional cash transfer programmes (vaccination, school attendance, training enrolment)
- Agentic loan facility drawdown and repayment
- Scholarship disbursement
- Humanitarian emergency relief

## Identity tiers

| Party | AIS-1 tier |
|---|---|
| Originator | Sovereign |
| Originator agent | Verified |
| Operator | Verified |
| Recipient agent | Verified |
| Beneficiary | Verified (typically issued in-field by an authorised onboarding partner) |

## Purpose codes used

| Code | Description |
|---|---|
| DTCT | Direct-to-Citizen Transfer |
| COND | Conditional Cash Transfer |
| PRAM | Parametric Disaster Response |
| SCHL | Scholarship Disbursement |
| HMRT | Humanitarian Emergency Relief |
| CLIM | Climate Resilience Payment |
| HLTH | Health-Conditional Transfer |
| DIAS | Diaspora Coordinated Remittance (with multilateral co-funding) |
| AGLN | Agentic Loan Drawdown |
| AGRP | Agentic Loan Repayment |

Existing ISO 20022 codes (`CHAR`, `STDY`, `BENE`, `LOAN`, `LOAR`) MAY also be used where they fit.

## Conditionality

Heavy use. Common predicate patterns:

- **Oracle**: NOAA cyclone category, drought index, price feed, government attestation feed
- **Attestation**: health authority certification of vaccination, education ministry confirmation of enrolment
- **Composite**: combine eligibility predicate (manual) with delivery-condition predicate (oracle)
- **Time**: scheduled disbursement against a programme calendar

Fallback actions are typically `return_to_originator` (humanitarian programmes) or `escrow_extend` (programme-aligned conditional flows).

## Onward delivery channels

- Mobile money (most common in development corridors)
- Bank credit (where the citizen is banked)
- Retail cash agent (last-mile cash-out for unbanked recipients)

## Licensing posture

Operator is licensed under a jurisdiction-appropriate digital-asset framework. Common patterns:

- Bermuda DABA (Class M sandbox to Class F full)
- EU MiCA (CASP authorisation)
- US GENIUS Act framework (where applicable to stablecoin settlement)
- Singapore PSA
- Switzerland FinSA / DLT Act

## Compliance posture

- Travel Rule data carried in clear OR under selective-disclosure envelope
- AML risk assessment at Sovereign-tier originator level
- Three-checkpoint sanctions screening per §11.3
- Capital-flow tags populated for regulator reporting

## Audit posture

Every ARS-1 message emits an AAS-1 Class A record. Operators conforming to this profile SHOULD publish AAS-1 Class B Merkle-root batches at agreed cadence (typically daily) for regulator and audit-firm consumption.

## Example deployments

Pilot deployments under this profile typically involve:

- A multilateral originator (signs Class I)
- A regional licensed operator (routes Class T)
- An in-field onboarding partner (issues AIS-1 Verified recipient agents)
- A mobile-money or retail-cash partner (signs Class R proof of delivery)

---

*This is a deployment-pattern reference. ARS-1 v0.2 does not endorse specific commercial operators. Conformance to this profile is by published criteria.*
