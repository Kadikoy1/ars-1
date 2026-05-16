# ARS-1 ↔ ISO 20022 Mapping — pain.001.001.10

This document specifies how ARS-1 Class I fields populate ISO 20022 pain.001.001.10 (CustomerCreditTransferInitiation). The mapping is normative for v0.2.

ARS-1 supplementary data is carried under the namespace `urn:ars-1:v0_2` inside the `<SplmtryData>` element. Implementations that strip supplementary data when crossing into non-agentic infrastructure MUST preserve the AIS-1 originator and beneficiary identifiers in the canonical ISO 20022 fields, maintaining FATF Travel Rule compliance.

## Field mapping

| ARS-1 Class I field | ISO 20022 pain.001.001.10 location | Notes |
|---|---|---|
| `messageId` | `<GrpHdr><MsgId>` | Direct mapping. |
| `timestamp` | `<GrpHdr><CreDtTm>` | Direct mapping. |
| `originatorRef` | `<Dbtr><Id><OrgId><Othr><Id>` with `<SchmeNm><Prtry>AIS-1</Prtry></SchmeNm>` | AIS-1 DID as proprietary identifier. |
| `originatorAgentRef` | `<DbtrAgt><FinInstnId><Othr><Id>` | Originator agent as proprietary FI. |
| `recipientAgentRef` | `<CdtrAgt><FinInstnId><Othr><Id>` | Recipient agent as proprietary FI. |
| `beneficiaryRef` | `<Cdtr><Id><PrvtId><Othr><Id>` or `<OrgId>` | Natural person (PrvtId) or entity (OrgId). |
| `amount.value` + `amount.currency` | `<PmtInf><CdtTrfTxInf><Amt><InstdAmt Ccy="">` | Direct mapping. |
| `amount.issuer` | `<SplmtryData>` under `urn:ars-1:v0_2` | Stablecoin issuer reference not natively expressible. |
| `purposeCode` | `<PmtInf><CdtTrfTxInf><Purp><Cd>` or `<Prtry>` | ISO codes in `<Cd>`; ARS-1 supplementary codes in `<Prtry>`. |
| `conditionality` | `<SplmtryData>` under `urn:ars-1:v0_2` | Inline or referenced Class C block. |
| `compliance` | `<SplmtryData>` under `urn:ars-1:v0_2`; Travel Rule core fields also in `<UltmtDbtr>` / `<UltmtCdtr>` | Dual carriage for non-agentic infrastructure interoperability. |
| `onwardDelivery` | `<SplmtryData>` under `urn:ars-1:v0_2` | Agentic semantics; not natively expressible in pain.001. |
| `valueDate` | `<PmtInf><ReqdExctnDt><Dt>` | Direct mapping. |
| `signature` | `<SplmtryData>` carrying full ARS-1 signature object | The ISO 20022 envelope is signed separately under the originating institution's standard signature regime. |
| `aas1RecordRef` | `<SplmtryData>` under `urn:ars-1:v0_2` | Cross-reference to AAS-1 audit record. |

## Namespace and conformance

ARS-1 supplementary data MUST be carried under the namespace `urn:ars-1:v0_2`. Implementations claiming ARS-1 conformance with ISO 20022 interop MUST:

1. Populate the canonical ISO 20022 fields with the mapped data.
2. Carry the full ARS-1 payload in `<SplmtryData>` under `urn:ars-1:v0_2`.
3. Preserve `<SplmtryData>` end-to-end when routing through non-agentic infrastructure.

## Other message-class mappings

The mapping above is for Class I → pain.001. Equivalent mappings for the other classes:

| ARS-1 Class | ISO 20022 Message |
|---|---|
| T — Transfer | pacs.008.001.10 |
| R — Receipt | camt.054.001.10 |
| V — Reversal (post-settlement) | pacs.004.001.10 |
| V — Reversal (pre-settlement) | camt.056.001.10 |

Detailed mapping tables for each will be published in v0.3 alongside the formal mapping annex agreed with the ISO 20022 Registration Authority.

## Open process

This mapping is proposed, not yet ratified by the ISO 20022 Registration Authority. The ARS-1 team intends to submit through the formal ISO 20022 maintenance process during the Phase 1.0 standardisation track (Q2 2027).
