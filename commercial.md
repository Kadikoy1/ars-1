# Profile: Commercial Remittance

**ARS-1 deployment-pattern profile · v0.2 reference**

## Use case

Private-sector value transfer:

- Diaspora P2P remittance (sender pays family / personal connections home)
- Employer payroll (cross-border salary, gig payouts)
- Marketplace settlement (vendor payments, platform payouts)
- B2B cross-border (supplier payments with agentic envelope)
- SME treasury operations

## Identity tiers

| Party | AIS-1 tier |
|---|---|
| Originator (individual) | Basic or Verified |
| Originator (business) | Verified |
| Originator agent | Verified |
| Operator | Verified |
| Recipient agent | Verified |
| Beneficiary | Verified |

## Purpose codes used

| Code | Description |
|---|---|
| RMSP | Sender-Pays Personal Remittance |
| RMBP | Business-Pays Personal Remittance |
| RMTB | Treasury / B2B Remittance |
| DIAS | Diaspora Coordinated Remittance |

Existing ISO 20022 codes used frequently: `FAMI` (family maintenance), `SALA` (salary), `SUPP` (supplier), `INTC` (intra-company), `GIFT`.

## Conditionality

Light or absent. Where used:

- **Time**: scheduled payroll, recurring transfers
- **Balance**: minimum-balance conditional spend
- **Attestation**: delivery confirmation for marketplace settlement (release on shipment confirmation)

## Onward delivery channels

- Mobile money (high-volume corridors)
- Bank credit (where the recipient is banked)
- Retail cash agent (last-mile)
- In-network spend (recipient agent holds and spends within the operator's merchant network)
- Hold-in-rail (recipient holds value in stablecoin for later use)

## Licensing posture

Operator is licensed as a money transmitter, payment institution, or digital-asset business in its home jurisdiction. Common patterns:

- US: state money-transmitter licences + FinCEN MSB registration
- UK: FCA EMI or API
- EU: PSD2 PI or EMI; MiCA for stablecoin handling
- Singapore: PSA Major Payment Institution
- UAE: VARA
- Bermuda: DABA Class F (or Class M for sandbox)

## Compliance posture

- Travel Rule mandatory for cross-border flows above declared threshold (typically USD/EUR 1,000)
- AML risk-scoring at originator and beneficiary tier
- Three-checkpoint sanctions screening per §11.3
- Higher transaction volumes mean automated batch screening with human review for matches

## Hardship-adjustment policy

This profile typically operates in corridors where local-currency volatility is meaningful. Operators SHOULD publish a hardship policy (per §12.2) and apply it consistently. The policy MUST run to the citizen's benefit, not the operator's spread.

## Pricing posture

Operators in this profile typically generate revenue from:

- Sender-paid fixed fee per transfer
- FX spread on conversion
- Per-active-agent annual fee paid by partner businesses (employers, marketplaces) for B2P flows
- API/SaaS fees for partner integrations

Pricing competition is on **transparency** and **net amount the beneficiary receives**, not on hidden spread.

## Audit posture

AAS-1 Class A records emitted per message. Operators conforming to this profile SHOULD publish AAS-1 Class C continuous-stream attestations for regulatory visibility, with selective disclosure to home and host regulators.

## Example deployments

Operators conforming to this profile typically serve:

- Diaspora corridors (US→Mexico, UK→Nigeria, UAE→South Asia, GCC→Philippines, EU→West Africa)
- Cross-border employers paying remote workers
- Marketplaces with sellers in multiple jurisdictions
- B2B platforms requiring conditional release on delivery

---

*This is a deployment-pattern reference. ARS-1 v0.2 does not endorse specific commercial operators. Conformance to this profile is by published criteria.*
