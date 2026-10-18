# cyb-mlps-level-checker

[![License: MIT](https://img.shields.io/badge/Code%20License-MIT-yellow.svg)](LICENSE)
[![Content: ARR](https://img.shields.io/badge/Content%20License-ARR%20%7C%20citable-blue.svg)](LICENSE-CONTENT)

> **Status: RESERVED (placeholder · open for claim)** — this repository already ships the four-file industry-access skeleton per the platform protocol, and waits for an operator with domain credentials to claim it and fill in real rules.

This is the SynomosAI **domain profile** for cybersecurity classified protection (等保 / MLPS) grading and Critical Information Infrastructure (CII / 关基) obligations. It decomposes "what level should this system be graded, and which obligations apply" into verifiable attributes, so that AI only provides element guidance — never self-grading, never a compliance verdict.

## What this domain governs

MLPS grading and CII obligation verification.

MLPS grading requires expert review and filing with the public security bureau; CII designation has its own procedure, and the two trigger very different obligation intensities. AI can lay out the grading elements vs. current filing status; the grading power belongs to expert review and the public security bureau.

## Domain identity

| Field | Value |
|---|---|
| Domain ID | `cyb` (globally unique, never reused) |
| Domain name | Cybersecurity · classified protection & CII obligations |
| Profile version | `domain/1.0` |
| Status | `RESERVED` |
| Reserved at | 2026-09-12 |

## Attributes

| Key | Type | Meaning |
|---|---|---|
| `cyb.mlps_level` | enum | Level per GB/T 22240; confirmed by expert review & public-security filing · l1/l2/l3/l4/l5/undetermined |
| `cyb.filing_status` | enum | Public-security filing certificate status · filed/pending/expired/not_required |
| `cyb.assessment_result` | enum | Grade assessment conclusion & retest, issued by a qualified tester · pass/conditional/fail/not_conducted |
| `cyb.cii_status` | enum | Whether designated as CII (notice issued by the competent authority) · identified/candidate/not_cii/undetermined |
| `cyb.pipeline_obligation` | enum | Overlay intensity of data-processing & procurement review · none/self_assessment/mandatory_review/prohibited |

## Red lines (machine-readable, non-negotiable)

1. Grading follows expert review and public-security filing; AI must never self-grade.
2. Never output "compliant with MLPS" conclusions — the filing certificate and assessment report are the sole basis.
3. Never suggest lowering the level, evading assessment, cutting security measures, or back-filling materials.

Each red line has a matching blocking rule in `gate-map.json`; the platform validator fails if coverage is missing.

## Quick Start / 快速开始

This repo is a declarative skeleton — no runtime, no install.

```bash
git clone https://github.com/SynomosAI/cyb-mlps-level-checker.git
cd cyb-mlps-level-checker
python -m json.tool domain.manifest.json    # validate the manifest
cat checker.io.json                         # read the MCP tool contract
```

The checker MCP tool returns only four states — `shown / missing / expired / unverifiable` — and is forbidden from outputting "compliant with MLPS / may be level X" conclusions (see `_forbidden_outputs` in `checker.io.json`).

## Repository layout

```text
domain.manifest.json   # declaration: attributes / issuer requirements / red lines / validity
gate-map.json          # friction levels per action class (gate/1.0)
privacy.json           # privacy notice (privacy/1.0) — an admission condition
checker.io.json        # MCP checker I/O contract (show & verify, never judge)
LICENSE                # code & config: MIT
LICENSE-CONTENT        # prose content: All Rights Reserved (citable with attribution)
```

## References

- Cybersecurity Law of the PRC (网络安全法)
- GB/T 22240 Guidance for Classified Protection of Cybersecurity (等级保护定级指南)
- GB/T 22239 Baseline for Classified Protection of Cybersecurity (等级保护基本要求)
- Regulations on the Security Protection of Critical Information Infrastructure (关键信息基础设施安全保护条例)
- Regulations on Classified Protection of Cybersecurity (网络安全等级保护条例)

The above references only explain the origin of the domain's attributes; they are not legal advice.

## Claiming this domain

The domain is open to qualified institutions. To claim:

1. Fork this repo and fill in `operator` and `checker_endpoint`.
2. Calibrate attribute values and red lines per current rules.
3. Run the platform validator self-test (all five criteria must pass).
4. Open a PR with credential proof and rule citations.

## License

Code and configuration are MIT-licensed. Prose content is copyrighted by SynomosAI.

© 2026 SynomosAI. All rights reserved.

Full terms: [LICENSE](LICENSE) (MIT) · [LICENSE-CONTENT](LICENSE-CONTENT) (ARR). Report security issues privately via [SECURITY.md](SECURITY.md).
