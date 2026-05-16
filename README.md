# ARS-1 — Agentic Remittance Standard

The open standard for agent-mediated value transfer.

**Working Paper v0.2 · May 2026 · CC0 · Draft for public comment**

🌐 [ars-1.org](https://ars-1.org)  
📄 [Read the specification (PDF)](https://ars-1.org/ARS-1_Specification_v0_2.pdf)  
🔗 Companions: [AIS-1](https://ais-1.org) · [AAS-1](https://aas-1.org)

---

## What is ARS-1?

ARS-1 defines a portable, signed, structured message protocol for moving value through AI agents. Where AIS-1 outputs a verifiable identity card and AAS-1 outputs signed action records, **ARS-1 outputs messages** — five classes (Instruction, Transfer, Receipt, Conditionality, Reversal) that together carry a full remittance lifecycle across operators, jurisdictions, and rails.

The standard addresses the **Stranded Agent Problem**: agents are now executing value transfer at scale, yet every operator implements its own message format, conditionality grammar, compliance overlay, and addressing scheme. Agents and the value they carry are stranded on whichever rail they were issued on. ARS-1 collapses this with three primitives:

1. **Messages** — the structured signed JSON artefacts that one party hands to another.
2. **AIS-1 DIDs** as the universal address — N² operator-to-operator integration becomes N.
3. **The ISO 20022 envelope** — ARS-1 rides inside pain.001 / pacs.008 via the standard's `<SplmtryData>` extension. Existing banking infrastructure routes the message without modification.

## Key properties

- **Dual-readable** — a Class I instruction is simultaneously a valid pain.001 message and a valid ARS-1 instruction.
- **Settlement-rail agnostic** — same message works whether settlement is in USDC on Base, EURC on Avalanche, CBDC on a private rail, or MT103 over correspondent banking.
- **FATF Travel Rule native** — Recommendation 16 data is a first-class field, with selective-disclosure support.
- **Conditionality built-in** — six predicate types (oracle, attestation, time, balance, manual, composite) with declared fallbacks.
- **Audit automatic** — every ARS-1 message emits an AAS-1 Class A record at issuance.
- **Three operator profiles** — institutional disbursement, commercial remittance, state-to-citizen. All share the protocol.

## Repository structure

```
ars-1/
├── README.md                          ← this file
├── LICENSE                            ← CC0
├── docs/
│   ├── ARS-1_Specification_v0_2.pdf   ← the specification (PDF)
│   └── ARS-1_Specification_v0_2.md    ← markdown source
├── schemas/
│   └── ars-1-class-i.schema.json      ← Class I JSON Schema (normative)
├── examples/
│   └── class-i-institutional.json     ← worked example
├── profiles/
│   ├── institutional.md
│   ├── commercial.md
│   └── state-to-citizen.md
└── .github/
    └── ISSUE_TEMPLATE/
        ├── feedback.md
        └── proposal.md
```

## Status

ARS-1 v0.2 is a **draft for public comment**. The comment period closes **31 August 2026**. A revised v0.3 will incorporate substantive feedback.

## How to contribute

- **File feedback or report an issue** → [open an issue](https://github.com/Kadikoy1/ars-1/issues/new?template=feedback.md)
- **Propose a change** → [open a proposal](https://github.com/Kadikoy1/ars-1/issues/new?template=proposal.md)
- **Email** → info@aiagentsservices.net

We are looking for:

- Review of the ISO 20022 envelope mechanic from ISO 20022 registration authorities
- Feedback on the Class I schema and conditionality grammar from operators and audit firms
- Proposed regulatory profile mappings (DABA, MiCA, GENIUS, FATF)
- Input on selective-disclosure cryptography
- Proposed supplementary purpose codes through the ISO 20022 RFP process
- Real-world deployment use cases and edge cases
- Support for formal standardisation through ISO TC 68 / SC 8

## License

This work is released under [CC0 1.0 Universal](LICENSE). No rights reserved. Free to implement without restriction.

## Companion standards

- **AIS-1** — Agent Identity Standard ([ais-1.org](https://ais-1.org)) — the identity layer ARS-1 binds to.
- **AAS-1** — Agent Auditability Standard ([aas-1.org](https://aas-1.org)) — the audit layer ARS-1 emits to.

Together, the three standards form an open identity-action-audit substrate for the agent economy.

## Published by

**BDA AI Agent Services** · Kadikoy Limited, Bermuda (Reg. 202302362)
