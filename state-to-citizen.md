# Profile: State-to-Citizen

**ARS-1 deployment-pattern profile · v0.2 reference**

## Use case

Sovereign welfare and public-sector disbursement:

- Social benefits (unemployment, disability, housing assistance)
- State pensions
- Tax refunds
- Public-sector salaries
- Universal Basic Agent (UBA) allocations
- Disaster relief from sovereign emergency funds
- Education grants and bursaries
- Child benefit and family allowances

## Identity tiers

| Party | AIS-1 tier |
|---|---|
| Originator (state entity) | Sovereign |
| Originator agent | Sovereign |
| Operator | Sovereign or Verified (may be the central bank, treasury, or designated public utility) |
| Recipient agent | Sovereign (issued by national registry) |
| Beneficiary | Verified by the national identity system |

## Purpose codes used

| Code | Description |
|---|---|
| UBAA | Universal Basic Agent Allocation |
| BENE | (ISO 20022 standard code for social benefits) |
| PENS | (ISO 20022 standard code for pension) |
| GOVT | (ISO 20022 standard code for general government payment) |
| TAXS | (ISO 20022 standard code for tax-related payment / refund) |
| SALA | (ISO 20022 standard code for salary) |

## Conditionality

Eligibility predicates verified against government attestations. Common patterns:

- **Attestation**: confirmation from the relevant ministry that the beneficiary meets programme criteria (unemployment status, disability status, residency, etc.)
- **Time**: scheduled recurring disbursement against the programme calendar
- **Composite**: combine multiple eligibility predicates (employment status AND residency AND age)

Fallback actions typically `null_and_audit` — if eligibility cannot be confirmed, no disbursement occurs and the case is escalated for human review.

## Settlement

May use:

- **CBDC** where the issuing state has deployed one
- **Central-bank-issued stablecoin** (state-backed payment token)
- **Domestic fiat rail** (RTGS or national payment system; the ARS-1 envelope rides on top of standard ISO 20022 pacs.008)
- **Stablecoin** (where state policy permits)

## Onward delivery channels

- Bank credit (most common — citizens have national bank account)
- Mobile money (in countries with high mobile-money penetration)
- In-network spend (where the state's recipient agent network includes accepting merchants — e.g. supermarkets accepting welfare disbursement directly)

## Licensing posture

Operator is typically either:

- A central bank (issuing state-backed digital money directly)
- A treasury-designated public utility
- A licensed digital-asset business under the state's regulatory framework

## Compliance posture

- Travel Rule typically not applicable (domestic flows) but envelope MAY be populated for audit completeness
- AML risk-scoring at state-system level rather than per-transaction
- Sanctions screening against state's own list set (which may include domestic adverse-actor lists in addition to international lists)
- Capital-flow tags MUST be populated for state's own balance-of-payments reporting

## Privacy posture

Highest among the three profiles. Beneficiary information is necessarily known to the state but MUST NOT be exposed unnecessarily to merchants, settlement-rail operators, or downstream parties. The selective-disclosure envelope (§11.2) is critical.

## Audit posture

AAS-1 records MUST be emitted but MAY be held by the state's audit authority rather than published. State audit offices use AAS-1 records as the basis for programme effectiveness and integrity audits.

## Example deployments

States adopting ARS-1 under this profile typically use it for:

- Disbursing universal basic income or universal basic agent allocations
- Pandemic-era stimulus and emergency support
- Targeted welfare programmes with eligibility predicates
- Diaspora-to-citizen state pension delivery
- Tax refund delivery

---

*This is a deployment-pattern reference. ARS-1 v0.2 does not endorse specific state operators. Conformance to this profile is by published criteria.*
