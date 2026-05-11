# G²CPU × EBT Framework
### *AI Governance Architecture for Safety-Critical Engineering*

![Epoch Frameworks LLC](https://img.shields.io/badge/EPOCH_FRAMEWORKS_LLC-Fort_Worth%2C_TX-2D3436?style=for-the-badge&labelColor=2D3436&color=8E9FD5)
![EBT Framework](https://img.shields.io/badge/EBT_FRAMEWORK-v2.6_%2B_NNN-2D3436?style=for-the-badge&labelColor=2D3436&color=A78BFA)
![DACR License](https://img.shields.io/badge/DACR_LICENSE-v2.6-2D3436?style=for-the-badge&labelColor=2D3436&color=596170)
![CVD Construct](https://img.shields.io/badge/CVD_CONSTRUCT-Biesmans_%2B_McDonald_(2026)-A33030?style=for-the-badge&labelColor=2D3436&color=A33030)

---

> **You cannot use AI to validate a system that AI is not yet qualified to assess.**
>
> — CVD Construct, Biesmans + McDonald (2026)

---

## What This Repository Is

This repository is the proof-of-work artifact for a live framework collaboration between **Erwin M. McDonald** (Epoch Frameworks LLC, Fort Worth TX) and **Natan Biesmans** (G²CPU), a LabVIEW aerospace and defense engineer working at the intersection of GPU-accelerated high-performance computing and safety-critical test validation.

The conversation that generated this work is documented in [`natan-intelligence-conversation.md`](./natan-intelligence-conversation.md). The interactive brief is deployed at [`index.html`](./index.html) via GitHub Pages.

This is not a hypothetical framework exercise. Natan is operating inside an active $200M rocket engineering program, navigating a governance gap that the current certification standards — DO-178C, ARP4754B, DO-330 — formally acknowledge they cannot fully address. The frameworks here are built for that gap.

---

## The Core Problem — Circular Validation Dependency (CVD)

**CVD** is a new construct coined collaboratively by Natan Biesmans and Erwin M. McDonald in 2026. It describes a specific structural failure mode in safety-critical AI deployment:

> A condition where an AI system is employed to validate a safety-critical architecture it is structurally unqualified to assess — because the validation tool and the system under test share the same probabilistic foundation. The result is a closed loop where evaluative bias is never surfaced, because the evaluator and the evaluated cannot be meaningfully separated.

Natan described this in conversation as the **egg-to-chicken problem**: AI was introduced to assist rocket test validation, but its output began to be treated as deterministic test verdict. The hallucination surface is invisible — until something fails. At $200M per launch vehicle, that surface is unacceptable.

This is not a hallucination problem. It is a circular dependency problem. And it maps precisely to EBT Pathway 2: Objectivity Laundering operating at its most dangerous scale.

---

## The CVD Loop

```
┌─────────────────────────────────────────────────────────────┐
│                     THE CVD LOOP                            │
│                                                             │
│  [01] AI introduced to assist rocket test validation        │
│         ↓                                                   │
│  [02] AI output treated as deterministic test verdict  ◄──┐ │
│         ↓                                                  │ │
│  [03] Hallucination surface invisible until failure        │ │
│         ↓                                                  │ │
│  [04] Trust boundary was never defined ────────────────────┘ │
│                                                             │
│  CVD = Objectivity Laundering at $200M scale                │
└─────────────────────────────────────────────────────────────┘
```

---

## The Regulatory Context

DO-178C is the primary software certification standard used by EASA, the FAA, and Transport Canada for airborne software. Its formal limitation — documented in the standard itself — is that it does not fully cover the challenges of AI-enabled systems. For neural networks, the DO-178C process breaks down when requirements cannot be flowed down to explicit lines of code.

**That is the technical articulation of what Natan described colloquially as the egg-to-chicken problem. The standard admits it cannot handle what he is being asked to do.**

### Design Assurance Levels — The Stakes Table

| DAL | Failure Condition | AI Tool Permissibility | Verification Rigor |
|-----|------------------|----------------------|-------------------|
| **DAL A** | Catastrophic | Extremely constrained | Maximum |
| **DAL B** | Hazardous | Heavily constrained | High |
| **DAL C** | Major | Restricted | Moderate |
| **DAL D** | Minor | Limited | Basic |
| **DAL E** | No Effect | No constraint | Minimal |

A $200M rocket program operates at DAL A or DAL B. As Design Assurance Levels increase toward DAL A, trust in automated tools decreases correspondingly — and AI usage becomes not just technically risky but regulatorily unsupported at those levels.

### The DO-330 Tool Qualification Gap

DO-330 defines three criteria that determine whether and how a software tool must be formally qualified before it can be used in a safety-critical verification chain:

| Criterion | Definition | Risk If Unqualified |
|-----------|-----------|---------------------|
| **Criterion 1** | Tool output is part of airborne software — could insert an error | Invalidates downstream verification |
| **Criterion 2** | Tool automates verification — could fail to detect an error | Compromises coverage audit confidence |
| **Criterion 3** | Tool could fail to detect an error within its intended use | Undermines certification evidence |

The critical question that most programs never formally answer: **What Tool Qualification Level (TQL) has G²CPU been assessed at under DO-330?** If an AI inference layer sits above an unqualified G²CPU substrate, the entire stack is uncertifiable under DO-330.

---

## EBT Framework — Pathway Analysis

The EBT Framework (Evaluative Bias Transference), coined McDonald (February 25, 2026), identifies three pathways through which human evaluative bias enters AI architectures as unchallengeable output. In the G²CPU rocket context:

**Pathway 1 — Structural Criteria Encoding**
The criteria for what constitutes a valid rocket test are encoded — often implicitly — into AI training data and prompt architecture. Once encoded, those criteria become unchallengeable output. The AI does not know what it does not know about the system it is evaluating.

**Pathway 2 — Objectivity Laundering (CVD Zone)**
AI-generated test analysis is presented as objective validation output. Engineers under schedule pressure treat probabilistic output as deterministic verdict. The hallucination surface is invisible until something fails. This is where CVD lives.

**Pathway 3 — G²CPU as the Trusted Substrate (Solution Layer)**
G²CPU's deterministic, hardware-level execution model creates the trust boundary CVD requires. AI informs the engineer. The engineer commands G²CPU. G²CPU executes without probabilistic ambiguity. The intelligence layer and the execution layer are structurally separated.

---

## NNN Governing Layer

The Neural Network Navigation (NNN) layer is an EBT v2.6 governing instrument that defines where AI authority ends and human authority begins. Three modes apply directly to Natan's context:

| NNN Mode | Function | Application |
|----------|----------|-------------|
| **NNN-D · Detection** | Monitors AI output for deviation from defined engineering criteria | Any AI test result untraceable to a deterministic substrate triggers a detection flag before entering the decision chain |
| **NNN-G · Governance** | Defines where AI authority ends and engineer authority begins | AI governs pattern recognition and anomaly flagging — G²CPU governs execution — the boundary is enforced, not assumed |
| **NNN-H · Human Override** | Ensures no AI output can override a qualified engineer's safety-critical judgment | Formal expression of what Natan already practices intuitively — NNN-H makes it auditable |

Natan already operates this way instinctively. NNN-H formalizes what he does into a documented, auditable governance layer — which is exactly what a certification authority will eventually require.

---

## Proposed Trust Boundary Architecture

```
┌────────────────────────────────────────────────────────────────┐
│  LAYER 5  │  ENGINEER DECISION AUTHORITY                        │
│           │  Final call on all safety-critical test verdicts    │
│           │  NNN-H enforced · No AI output overrides this layer │
├───────────┼────────────────────────────────────────────────────┤
│  LAYER 4  │  CGM + NNN GOVERNANCE                               │
│           │  Criteria drift detection · Output deviation scoring │
│           │  Prompt integrity · Certification audit logging      │
├───────────┼────────────────────────────────────────────────────┤
│  LAYER 3  │  AI-ASSISTED PATTERN RECOGNITION                    │
│           │  Anomaly detection · Telemetry pattern analysis      │
│           │  Advisory only · EBT gated · No direct execution    │
├───────────┼────────────────────────────────────────────────────┤
│  LAYER 2  │  G²CPU SIGNAL PROCESSING                            │
│           │  GPU-accelerated HPC · ArrayFire · CUDA / OpenCL    │
│           │  Deterministic execution · The trusted substrate     │
├───────────┼────────────────────────────────────────────────────┤
│  LAYER 1  │  PXI / RADX HARDWARE                                │
│           │  Physical measurement · NVIDIA PXIe-GPUs             │
│           │  Ground truth source · Hardware reality              │
└───────────┴────────────────────────────────────────────────────┘
```

G²CPU is not just a performance tool in this architecture. It is the structural answer to the trust boundary that CVD demands. The deterministic execution model at Layer 2 is what makes every AI-assisted layer above it valid. Without it, the governance architecture has no substrate to stand on.

---

## Collaborative Framework Contributions

This repository represents four discrete contributions that emerge from the Biesmans + McDonald conversation:

**Contribution 01 — CVD as a Named EBT Construct**
Biesmans + McDonald (2026). EBT v2.7 candidate. Publishable contribution to AI governance literature in safety-critical engineering. The construct addresses a gap that neither the AI safety community nor the aerospace engineering community has formally named.

**Contribution 02 — G²CPU as NNN Layer 2 Reference Architecture**
G²CPU's deterministic execution model becomes the reference implementation for NNN Layer 2 — the trusted computational substrate that NNN governance requires before AI output can be considered valid in a safety-critical workflow. This positions G²CPU not just as an HPC toolkit, but as a governance-aware engineering platform with a defined role in the certification trust chain.

**Contribution 03 — Joint White Paper for GDevCon + NI Tools Network**
*"Why AI Cannot Be Trusted to Validate What It Cannot Deterministically Execute"* — co-authored, dual distribution channel. Targets the LabVIEW aerospace and defense community at the exact moment regulators are developing new AI guidance that does not yet exist.

**Contribution 04 — EBT Diagnostic on Active Rocket Client Workflow**
A private intelligence brief identifying exactly where CVD risk is present in Natan's current client engagement, where NNN governance is required, and where G²CPU provides structural protection AI alone cannot. Sprint 1 candidate for a working engagement.

---

## Repository Structure

```
epoch-g2cpu-ebt-framework/
├── README.md                          # This file
├── index.html                         # GitHub Pages interactive brief (deployed)
└── natan-intelligence-conversation.md # Full pre-engagement intelligence document
                                       # — DO-178C / DO-330 regulatory deep dive
                                       # — The three conversation questions and sequencing
                                       # — CVD construct definition and loop diagram
                                       # — NNN mode table with G²CPU application
                                       # — Trust boundary architecture diagram
                                       # — All four collaborative contributions
```

---

## The Three Conversation Questions — In This Order

The intelligence brief documents a specific conversation architecture designed to surface the governance gap before introducing any frameworks. The sequencing is not optional:

**Q1 — The Certification Trigger**
*"When your rocket client's program manager submits for certification review, what documentation trail exists to show that the AI-assisted test layer did not contaminate the validation chain? Not the G²CPU output — the AI layer above it."*

This is not a question about technical capability. It is about the paper trail the program manager will need when a certification authority asks. The gap between what Natan can answer and what the PM can answer is where the engagement lives.

**Q2 — The Tool Qualification Status**
*"Has G²CPU been through a DO-330 Tool Qualification Level assessment for the DAL level your client is operating at? And if an AI inference layer sits above it in the test workflow, has that layer been assessed under DO-330 Criterion 2?"*

This demonstrates knowledge of the regulatory environment at a level most consultants — and most engineers outside the certification world — do not have. The pause that follows is the conversation.

**Q3 — The CVD Governance Gap**
*"If the AI layer produces a result that conflicts with the G²CPU telemetry output — who owns that decision, what is the documented escalation path, and how does that decision get logged in a way that survives a certification audit?"*

There is no existing standard that answers this question for an AI-assisted LabVIEW test workflow at DAL A/B. EASA's AI trustworthiness framework is still being developed. The FAA has not published binding guidance. The answer does not exist yet — and that is precisely where CVD and NNN governance become relevant.

The sequencing rule: ask Q1, listen. Ask Q2, listen. Ask Q3, listen. Then say: *"I've been developing a framework construct for exactly that condition. I'd like to share it with you and get your technical reaction to it."*

---

## About Natan Biesmans

Natan Biesmans is the developer behind G²CPU — a GPU-accelerated HPC framework built for LabVIEW, targeting safety-critical aerospace and defense test environments. His work sits at the intersection of deterministic signal processing (ArrayFire, CUDA, OpenCL, PXI/RADX hardware) and the governance gap that emerges when AI is introduced into certification workflows that were designed for deterministic code.

Natan identified the CVD problem from inside an active $200M rocket engineering engagement. That observation — made in conversation, not in a paper — is the intellectual origin of this repository.

LinkedIn: [Natan Biesmans](https://www.linkedin.com/in/natan-biesmans-2875ab101/)

---

## About Epoch Frameworks LLC

Epoch Frameworks LLC is a behavioral intelligence and AI governance consultancy founded by Erwin M. McDonald, operating as a Behavioral Intelligence Architect, Fractional CXO, and AI Adoption Architect. The firm's core practice is built on the EBT Framework (Evaluative Bias Transference), coined February 25, 2026.

The McDonald Suite of frameworks — EBT, NNN, WCIS, DARE, CGM, ESIL, MOC, MBEL, and related instruments — is designed to surface the structural conditions under which AI produces unchallengeable output that should not be trusted. CVD is the safety-critical engineering expression of that same structural failure.

---

## Interactive Brief

The GitHub Pages deployment at `index.html` presents the full framework integration brief in a visual format designed for professional sharing with Natan, his clients, and the GDevCon / NI Tools Network community. It covers the CVD construct, NNN mode table, trust boundary architecture, and all four collaborative contributions in a dark-mode engineering aesthetic aligned with the G²CPU brand context.

---

## IP and Attribution

All frameworks in this repository are protected under the **DACR License v2.6**, McDonald (2026). GitHub commit history serves as IP timestamping.

The **CVD Construct** is collaborative intellectual property: **Biesmans + McDonald (2026)**. Neither party may commercialize the CVD construct independently without written agreement. All other framework instruments remain the sole property of Epoch Frameworks LLC.

No methodology is disclosed in full in any public artifact. The framework names and construct definitions are public signals. The diagnostic instruments, scoring systems, and engagement protocols are proprietary.

---

## Contact

**Erwin M. McDonald**
Epoch Frameworks LLC · Fort Worth, Texas
[erwin.mcdonald@outlook.com](mailto:erwin.mcdonald@outlook.com?subject=G2CPU%20×%20EBT%20Framework%20Collaboration%20—%20Natan%20Biesmans)
[LinkedIn](https://www.linkedin.com/in/emcdo411/)
[GitHub](https://github.com/emcdo411)

---

*© McDonald (2026) · Epoch Frameworks LLC · DACR License v2.6 · All rights reserved*
*CVD Construct · Biesmans + McDonald (2026) · Collaborative IP*
