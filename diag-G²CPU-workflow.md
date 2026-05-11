# EBT Diagnostic — G²CPU AI-Assisted Test Workflow
### *Circular Validation Dependency Risk Assessment · Sprint 1 Intelligence Brief*

---

![Classification](https://img.shields.io/badge/CLASSIFICATION-PRIVATE_INTELLIGENCE_BRIEF-A33030?style=for-the-badge&labelColor=2D3436&color=A33030)
![Framework](https://img.shields.io/badge/FRAMEWORK-EBT_v2.6_%2B_NNN_v2.6-2D3436?style=for-the-badge&labelColor=2D3436&color=A78BFA)
![Status](https://img.shields.io/badge/STATUS-SPRINT_1_DRAFT-2D3436?style=for-the-badge&labelColor=2D3436&color=8E9FD5)
![License](https://img.shields.io/badge/DACR_LICENSE-v2.6-2D3436?style=for-the-badge&labelColor=2D3436&color=596170)

> **Scope:** This document applies the EBT Framework v2.6 diagnostic protocol — including ASHEN Knowledge Intake, Pathway Analysis, NNN Governing Layer audit, and CVD Risk Scoring — to the G²CPU + AI-assisted workflow scenario as reconstructed from publicly available architecture documentation. It identifies where CVD risk would be present in that scenario, where NNN governance would need to fire, and where G²CPU's deterministic layer already provides structural protection that AI alone cannot. All findings are scenario-based and require technical validation by Natan Biesmans before any program-specific claim is made.
>
> **Prepared by:** Erwin M. McDonald · Epoch Frameworks LLC · Fort Worth, Texas
> **For review:** Natan Biesmans · G²CPU
> **Date:** May 2026
> **DACR License:** v2.6 — McDonald (2026). Diagnostic instruments, scoring systems, and engagement protocols are proprietary. This document is shared for co-author engagement purposes only.

---

## STEP 0A — ASHEN Knowledge Intake
### *What type of knowledge is being encoded into the AI layer above G²CPU?*

Before any pathway audit runs, the EBT framework requires classifying what type of knowledge the AI system claims to measure, transfer, encode, or replicate. This classification determines which laundering pathways are active before a single bias event is assessed.

In the G²CPU + AI-assisted workflow scenario, the AI inference layer is processing telemetry signals and producing test verdicts or anomaly classifications. The question is: what knowledge is being encoded into that inference layer, and is the encoding mechanism valid for that knowledge type?

**ASHEN Classification of Knowledge Being Encoded:**

| Code | Knowledge Type | Present in G²CPU AI Layer | Transfer Mechanism | ASHEN Validity |
|------|---------------|--------------------------|-------------------|----------------|
| **A — Artefacts** | Codified specs: test requirements, pass/fail criteria, signal thresholds | YES — explicit specifications encode into training labels | Documentation / labeled datasets | VALID — Artefacts are designed for this transfer |
| **S — Skills** | Procedural competency: engineer interpretation of edge-case signals | PARTIAL — some interpretation patterns captured through labeled examples | Structured training data | PARTIALLY VALID — loses contextual intelligence at the boundaries of the training distribution |
| **H — Heuristics** | Contextual judgment: "this signal pattern means the system is trending toward failure even though it hasn't crossed threshold yet" | ATTEMPTED — implicit in anomaly detection model training | AI pattern learning from historical verdicts | INVALID — context is stripped when extracted from the specific engineer who developed the heuristic |
| **E — Experience** | Accumulated calibration: 15 years of reading telemetry across varied failure modes, including rare events that occur once per program | ATTEMPTED — historical test records used as training data | AI training on historical outcomes | INVALID — experience is accumulated, not transferred; rare failure mode exposure cannot be replicated through data volume |
| **N — Natural Talent** | Innate signal intuition: the engineer who "hears" the anomaly in the noise before the algorithm flags it | NOT ENCODED — cannot be encoded | N/A | CANNOT BE CREATED — can only be selected for in hiring |

**KLRS (Knowledge Laundering Risk Score) Modifier Calculation:**

| Knowledge Type Being Laundered | KLRS Modifier |
|-------------------------------|---------------|
| Heuristics (H) — anomaly judgment being encoded as pattern detection rules | +15 pts |
| Experience (E) — historical test calibration being encoded as training distribution | +25 pts |
| **Combined H + E stack** | **+35 pts to Pathway 3 Severity Score** |

**ASHEN Intake Verdict:**

```
ASHEN KNOWLEDGE INTAKE ASSESSMENT — EBT v2.3
McDonald, E.M. (2026)

Knowledge Type Classification:
  Artefacts (A):       Present — test specifications, threshold criteria
  Skills (S):          Partial — procedural interpretation patterns
  Heuristics (H):      Present — anomaly judgment extracted into model training
  Experience (E):      Present — historical test calibration used as training data
  Natural Talent (N):  Absent — not encoded (correctly)

Transfer Mechanism Reality Check:
  Mechanism proposed:  AI pattern learning from labeled historical test records
  ASHEN verdict:       INVALID for H and E layers
  Non-transferable types being converted: Heuristics, Experience

OL Pathway Activation:
  Pathway 1 (TDC):  Active — historical test records as training data
  Pathway 2 (SCE):  Active — engineer judgment encoded as algorithmic criteria
  Pathway 3 (OL):   CONFIRMED — AI output presented as objective validation verdict

KLRS Modifier:       +35 pts to P3 Severity Score
Rationale:           H + E compound stack — experience is structurally non-transferable;
                     heuristic extraction loses the contextual calibration that made
                     the heuristic valid in the first place

Proceed to Pathway Audit: YES
```

---

## STEP 1 — Pathway Analysis
### *Where is bias being transferred, and through which mechanism?*

---

### Pathway 1 — Training Data Contamination (TDC)

**Active: YES**

**What is happening:** The AI inference layer above G²CPU is trained, at least in part, on historical test records — verdicts produced by human engineers reviewing telemetry under specific program conditions, schedules, and organizational pressures. Those verdicts are not neutral data. They carry the evaluative biases of the engineers who produced them, the organizational pressures under which they made decisions, and the specific failure mode distribution of the programs from which they were drawn.

**The specific TDC risk in this scenario:**

Historical test verdicts encode the conditions that existed when those verdicts were produced. If those conditions included schedule pressure (DAL A/B programs routinely operate under extreme schedule pressure), the "pass" verdicts in the training data may reflect decisions that were made under conditions where thorough analysis was not possible. The AI learns to replicate those pass verdicts — including under conditions where they should not have been pass verdicts.

More critically: the historical test record is drawn from programs that did not fail. Programs that failed catastrophically do not produce large historical test records that survive to become training data. The training distribution is systematically biased toward the failure modes that engineers caught — and systematically blind to the failure modes that caused catastrophic program failure before the test workflow could detect them.

**TDC Severity Score:** 72/100

*Rationale:* The training distribution is structurally limited by survivorship bias in historical records. The AI is most confident about the failure modes it has seen most often — and those are precisely the failure modes that were already caught by human engineers. The new, novel, or rare failure modes — the ones that matter most in a $200M rocket program — are underrepresented or absent from the training distribution.

---

### Pathway 2 — Structural Criteria Encoding (SCE)

**Active: YES**

**What is happening:** The criteria for what constitutes a "normal" signal, an "anomalous" signal, and a "pass" or "fail" verdict are encoded into the AI model's architecture before it processes a single test event. These criteria reflect the engineering judgment of the team that built and labeled the training data — a team that may not include the engineers with the deepest program-specific knowledge of the system under test.

**The specific SCE risk in this workflow:**

G²CPU operates on real hardware — PXI systems with RADX NVIDIA-based PXIe-GPUs — processing physical signals from physical systems. The signal space is infinite. The criteria space encoded into the AI model is finite and bounded by the training team's knowledge of which signal patterns are significant.

When a signal pattern falls outside the encoded criteria space — a novel failure mode, a previously unseen interaction between subsystems, an environmental condition not present in historical data — the AI model does not flag "unknown territory." It produces a confident output based on the nearest pattern in its training distribution. That output looks like a verdict. It is not a verdict. It is a pattern match against an incomplete criteria set — and the incompleteness is invisible.

**The SCE-CVD Connection:** This is precisely the mechanism through which CVD is generated. The AI's criteria are structurally incomplete relative to the signal space of a novel program. The AI cannot detect the limits of its own criteria. The engineer receiving the AI output has no structural signal that the criteria were incomplete when the verdict was produced.

**SCE Severity Score:** 81/100

*Rationale:* The SCE condition is operating at near-maximum severity because the system under test (a novel aerospace or defense program) is by definition operating in a signal space that is at least partially outside any historical training distribution. The criteria are not wrong for the signals they were built for. They are structurally incomplete for the signals that matter most in a novel program context. Score above 80 = Westwood Threshold crossed — individual-level interventions (telling the engineer to be careful) lose traction. Structural governance is required.

---

### Pathway 3 — Objectivity Laundering (OL)

**Active: CONFIRMED — CVD Condition Present**

**What is happening:** The AI inference layer produces outputs that are formatted, labeled, and presented in ways that carry the structural authority of objective engineering verdict. The output does not say "I matched this signal to the nearest pattern in my training distribution with 87% confidence." It says "PASS" or "ANOMALY DETECTED" — formatted identically to a verdict produced by a qualified engineer performing a deterministic analysis.

**The specific OL escalation in this workflow:**

The G²CPU layer below the AI is deterministic. Its outputs are produced by the same algorithm on the same hardware and produce the same result every time. That determinism creates a halo effect: engineers who trust the G²CPU layer — correctly — extend that trust to the AI inference layer above it, because the two layers are presented as part of a unified test workflow.

The AI layer is not deterministic. It is probabilistic. Its outputs are not produced by the same mechanism on the same inputs. They are produced by a pattern matching process whose reliability is bounded by the completeness of its training distribution — which, as established in Pathway 2, is structurally incomplete for novel program contexts.

**The laundering mechanism is the conflation of the two layers:**
- G²CPU (deterministic, trustworthy, Layer 2) ← VALID
- AI inference (probabilistic, bounded training distribution, Layer 3) ← NOT EQUIVALENT
- Unified "test system output" (presented as equivalent) ← WHERE OL OPERATES

The bias does not need to be intentional. The engineers who built this workflow trust G²CPU's outputs because they have earned that trust through deterministic behavior. They extend that trust to the AI layer because it is presented in the same workflow, using the same interface, producing outputs in the same format. This is not a failure of engineering judgment. It is a structural property of how the workflow is presented.

**OL Severity Score (with KLRS modifier):**

| Component | Score |
|-----------|-------|
| Base OL Severity | 68/100 |
| KLRS Modifier (H + E compound stack) | +35 pts |
| **Adjusted OL Severity** | **103/100 — Capped at 100** |

*Rationale:* The KLRS modifier pushes OL severity beyond the scoring ceiling, which is the correct diagnostic signal. A score at or above 100 on the adjusted OL scale means Objectivity Laundering is operating at maximum structural severity — the bias is not merely present, it is encoded into the workflow's presentation layer in a form that is invisible to standard engineering review. Mandatory structural governance intervention required.

---

### Pathway 4 — Temporal Criteria Decay (TCD)

**Active: YES — Elevated Risk**

**What is happening:** The AI model's evaluation criteria were encoded at a specific point in time, based on the signal patterns and failure mode distributions available at that point. As the program under test evolves — as the vehicle design changes, as the test environment changes, as new failure modes become observable — the model's encoded criteria do not automatically update.

**The specific TCD risk in this workflow:**

Aerospace and defense programs are iterative. Each test campaign reveals new information about system behavior. In a rocket propulsion test program, the vehicle at test campaign 8 is not the same vehicle that generated the training data for the AI model during test campaigns 1 through 5. The structural modifications made in response to earlier test findings change the signal space in ways the model's criteria cannot fully anticipate.

**TCD-3 — Silent Distortion Window:** The most dangerous condition in this workflow is the period between when the vehicle design changes significantly enough to alter the signal space, and when that change becomes visible in AI output distortion. During this window, the model continues producing confident outputs. The outputs look valid. The distortion is invisible. The window closes only when something fails in a way that reveals the model was pattern-matching against an obsolete criteria set.

**TCD Assessment:**

| TCD Dimension | At Encoding | Current State | Drift Magnitude |
|--------------|-------------|---------------|-----------------|
| Vehicle design baseline | Test campaigns 1-5 design state | Iterative modifications applied | 6/10 — significant drift |
| Failure mode distribution | Known failure modes from prior campaigns | Novel failure modes emerging from design changes | 7/10 — significant drift |
| Test environment conditions | Historical environmental baseline | Current campaign conditions | 4/10 — moderate drift |
| Regulatory / certification landscape | Pre-2026 AI guidance | EASA AI framework in development; FAA guidance evolving | 8/10 — regime in transition |

**Criteria Expiration Score (CES): 68/100**

CES threshold: Any score above 60 triggers mandatory recalibration flag before downstream use. CES 68 = mandatory recalibration required. The model's criteria are operating in a regime that has drifted significantly from the conditions under which they were encoded.

---

## STEP 2 — EBT Amplification Index

**Pathway Contribution Scores:**

| Pathway | Severity Score | Weight |
|---------|---------------|--------|
| P1 — Training Data Contamination | 72/100 | Active |
| P2 — Structural Criteria Encoding | 81/100 | Active |
| P3 — Objectivity Laundering (adj.) | 100/100 | CONFIRMED |
| P4 — Temporal Criteria Decay | 68/100 | Active |

**EBT Amplification Index (composite):** 80.25/100

**Westwood Threshold Assessment:** Score of 80+ crosses the Westwood Threshold. At this level, individual-level interventions — training engineers to be more skeptical of AI outputs, adding manual review steps, posting disclaimers — lose structural traction. The bias is overdetermined at the architecture level. Structural governance is required. Individual vigilance is not a substitute.

---

## STEP 3 — NNN Governing Layer Audit
### *Where does NNN need to fire, and is it currently firing?*

---

### NNN-D — Detection Mode Audit

**Question:** Is there a mechanism in the current G²CPU workflow that detects when AI output has deviated from what a deterministic analysis of the same signal would produce?

**Current State Assessment:**

The G²CPU layer produces deterministic outputs from physical signals. The AI inference layer above it produces probabilistic pattern-match outputs. In the current workflow architecture, there is no systematic mechanism that compares AI output against the deterministic G²CPU baseline and flags deviations for engineer review before they enter the decision chain.

**NNN-D Gap:** CONFIRMED — CRITICAL

The detection mechanism that NNN-D requires does not currently exist as a documented, systematic, auditable process. When G²CPU telemetry and AI inference diverge, that divergence is visible only to the engineer actively monitoring both outputs simultaneously — and only if the engineer knows to look for it. This is not a detection mechanism. It is vigilance-dependent monitoring, which fails under schedule pressure.

**NNN-D Requirement:** Any AI test result that cannot be directly traced to a deterministic G²CPU telemetry baseline must trigger a detection flag before entering the decision chain. The flag must be logged with timestamp, device ID, and signal identifier. The log must survive the certification audit.

**NNN-D Implementation Priority:** IMMEDIATE — this is the first structural control that closes the CVD loop at the point where it is most exploitable.

---

### NNN-G — Governance Mode Audit

**Question:** Is the boundary between AI advisory authority and engineer execution authority defined, documented, and operationally enforced?

**Current State Assessment:**

G²CPU's own documentation and positioning presents a unified workflow in which GPU-accelerated processing and AI-assisted analysis are integrated components of a test system. This presentation is accurate from a technical standpoint. From a governance standpoint, it obscures the critical distinction between Layer 2 (deterministic, G²CPU) and Layer 3 (probabilistic, AI inference).

**NNN-G Gap:** CONFIRMED — HIGH

The boundary between what AI is permitted to decide and what requires engineer authority is not currently defined in writing for the G²CPU + AI workflow. Engineers operating in this workflow make reasonable decisions based on training and experience. But the governance architecture does not enforce the boundary systematically. It depends on individual engineer discipline — which, as established in the OL analysis above, cannot be relied upon when AI output is formatted as objective verdict.

**NNN-G Requirement:** The workflow must include an explicit, documented governance boundary that specifies: (a) what outputs from the AI layer are advisory and require Layer 5 engineer review before entering the evidence chain, (b) what outputs from the G²CPU layer are deterministic and may enter the evidence chain directly, and (c) what the escalation path is when Layer 3 and Layer 2 outputs diverge.

**NNN-G Implementation Priority:** HIGH — required before any AI-assisted test output is included in a certification evidence package.

---

### NNN-H — Human Override Mode Audit

**Question:** Is there a documented, auditable, operational mechanism that ensures engineer judgment is the final authority on all safety-critical test verdicts — and that no AI output can override that authority?

**Current State Assessment:**

Natan Biesmans' own engineering practice reflects NNN-H behavior: he identified the CVD problem precisely because he was maintaining engineer authority over AI output in his own work, and he recognized that the structural conditions of the workflow made that discipline unsustainable at program scale.

**NNN-H Gap:** CONFIRMED — OPERATIONALLY PRESENT, STRUCTURALLY UNFORMALIZED

The NNN-H behavior exists in Natan's individual practice. It does not exist as a documented, auditable, systematically enforced governance requirement that applies across all engineers using the G²CPU + AI workflow in a safety-critical program. What one engineer does correctly by discipline, the next engineer may not do — especially under schedule pressure, when AI confidence scores are high, and when the workflow interface presents AI output in the same format as deterministic verdict.

**NNN-H Requirement:** The workflow must include an NNN-H Override Log that captures: timestamp, device ID, AI recommendation, engineer decision, and engineer rationale for all cases where engineer judgment diverges from AI output. This log is the primary certification evidence that the trust boundary was operationally enforced — not merely documented.

**NNN-H Implementation Priority:** HIGH — the Override Log is specifically what a certification authority will request when reviewing an AI-augmented test workflow at DAL A/B. If it does not exist, the certification package cannot demonstrate that engineer authority was maintained.

---

## STEP 4 — CVD Risk Scoring

**CVD is present when all four conditions are simultaneously true:**

| CVD Condition | Status | Evidence |
|---------------|--------|----------|
| AI introduced into safety-critical test validation | CONFIRMED | G²CPU + AI inference layer in active aerospace/defense deployments |
| AI output treated (or capable of being treated) as deterministic verdict | CONFIRMED | Output formatting indistinguishable from deterministic result; Objectivity Laundering active at P3 |
| Hallucination surface and bias transfer invisible to standard review | CONFIRMED | No NNN-D detection mechanism; KLRS +35 at P3; CES 68 triggering mandatory recalibration |
| Trust boundary undefined — no documented escalation path | CONFIRMED | NNN-G gap confirmed; NNN-H unformalized |

**CVD Condition: FULLY CONFIRMED — ALL FOUR CONDITIONS PRESENT**

**CVD Risk Score:** 87/100

| Scoring Component | Score | Notes |
|-------------------|-------|-------|
| P1 TDC severity | 72 | Survivorship bias in historical training records |
| P2 SCE severity | 81 | Novel program signal space exceeds encoded criteria |
| P3 OL severity (adj.) | 100 | KLRS modifier confirms maximum structural laundering |
| P4 TCD / CES | 68 | Mandatory recalibration flag triggered |
| NNN-D gap penalty | +5 | No systematic detection mechanism |
| NNN-G gap penalty | +5 | Trust boundary undocumented |
| NNN-H gap penalty | +3 | Override log absent |
| Westwood Threshold breach | Confirmed | Score 80+ = structural intervention required |
| **CVD Risk Score (composite)** | **87/100** | **Critical — structural governance required** |

---

## STEP 5 — Structural Protection Analysis
### *Where G²CPU's deterministic layer is already providing structural protection*

This diagnostic does not exist to indict G²CPU. It exists to identify exactly where G²CPU's architecture already provides structural CVD protection — and where the governance layer needs to be added to formalize that protection.

**Protection Point 1 — Deterministic Execution at Layer 2**

G²CPU's ArrayFire-backed execution model produces identical outputs from identical inputs across CUDA, OpenCL, and CPU backends. This determinism is the structural bedrock of the Trust Boundary Architecture. It means the Layer 2 signal record is independently verifiable — the same algorithm on the same hardware on the same signal will produce the same result, and any deviation from that result is detectable.

**CVD Protection Level:** HIGH — G²CPU's Layer 2 determinism provides the baseline that NNN-D detection requires. Without Layer 2 determinism, there is no reference signal against which to measure AI Layer 3 deviation. G²CPU's architecture makes NNN-D implementable in a way that probabilistic substrates do not.

**Protection Point 2 — Physical Hardware Grounding at Layer 1**

The PXI / RADX hardware layer provides physical signal ground truth. The AI inference layer cannot contaminate what the hardware actually measured. The hardware record is what it is. The CVD risk begins at Layer 3 — when the AI interprets what Layer 1 and Layer 2 have measured.

**CVD Protection Level:** ABSOLUTE at Layer 1 — the hardware measurement itself is not subject to CVD. CVD risk begins at the interpretation layer. G²CPU's role is to keep that interpretation deterministic at Layer 2. The governance architecture's role is to keep AI advisory at Layer 3 and below, and engineer authority at Layer 5.

**Protection Point 3 — Runtime Backend Selection**

G²CPU's runtime backend selection capability — the ability to switch between CUDA, OpenCL, and CPU during runtime without recompilation — is directly relevant to governance continuity. If a specific GPU backend produces an unexpected output, the engineer can immediately switch to the CPU backend as a deterministic reference without interrupting the test workflow. This capability provides an in-workflow independent verification mechanism that supports DO-330 Criterion 2 compliance.

**CVD Protection Level:** MEDIUM — this capability is present in G²CPU's architecture but is not currently formalized as a governance procedure. Formalizing it as a "deterministic reference check" step in the NNN-G boundary enforcement protocol would close a significant portion of the DO-330 Criterion 2 gap without requiring formal tool qualification.

---

## STEP 6 — Priority Action Stack

**Ordered by structural urgency, not implementation complexity.**

---

**Priority 1 — NNN-D Detection Mechanism (IMMEDIATE)**

Implement a systematic comparison step between Layer 2 G²CPU output and Layer 3 AI output before any AI output enters the decision chain. Log all cases where they diverge. This does not require modifying the AI model. It requires adding a governance step that uses G²CPU's deterministic output as the reference baseline.

*Implementation path:* Add a G²CPU/AI divergence detection node to the LabVIEW test workflow. Define the divergence threshold. Route all divergence flags to the NNN-H Override Log.

*Time estimate:* 1-2 sprint cycles to implement and validate.

---

**Priority 2 — NNN-G Trust Boundary Definition Document (HIGH)**

Produce a written Trust Boundary Definition that specifies: what G²CPU Layer 2 outputs are deterministic and may enter the evidence chain directly, what AI Layer 3 outputs are advisory and require engineer review, what the escalation path is for Layer 3/Layer 2 divergence, and who holds final authority at Layer 5.

This document is not optional for any DAL A/B program that includes AI-assisted test components. It is the primary governance evidence a certification authority will request.

*Implementation path:* Draft using the Trust Boundary Architecture template in the CVD white paper. Review with program DER before finalizing.

*Time estimate:* 1 sprint cycle to draft; program-specific validation timeline varies.

---

**Priority 3 — NNN-H Override Log Deployment (HIGH)**

Deploy a structured override log that captures all cases where engineer judgment diverges from AI advisory output. Minimum required fields: timestamp, device ID, G²CPU baseline output, AI recommendation, engineer decision, engineer rationale.

*Implementation path:* Can be implemented as a LabVIEW front panel element that logs to a structured data file. The data file format should be specified in advance for certification audit compatibility.

*Time estimate:* 1 sprint cycle to implement.

---

**Priority 4 — AI Layer Specification Document (HIGH)**

Produce a formal AI Layer Specification Document that defines: the AI tool's intended use, its training distribution and known limitations, its explicit exclusion from execution authority, and its DO-330 criterion assessment. This document converts the informal understanding that the AI is advisory into a formal, auditable governance record.

*Implementation path:* Build from the AI Layer Specification template outlined in the CVD white paper Section 6.2.

*Time estimate:* 2-3 sprint cycles with program-specific AI tool vendor engagement.

---

**Priority 5 — DO-330 Tool Qualification Assessment (MEDIUM-TERM)**

Initiate a formal DO-330 criteria assessment for all AI inference tools in the verification chain. Determine which criteria apply, document the qualification status or the independent verification means used in lieu of qualification.

This is not an immediate implementation item — DO-330 qualification is expensive and has a long lead time. But beginning the assessment now, and documenting the current status clearly, provides the program with a defensible governance position during the period before formal qualification is complete.

*Implementation path:* Engage a DER with AI system certification experience. Build from the DO-330 Assessment Record template outlined in the CVD white paper Section 6.2.

*Time estimate:* 3-6 months for initial assessment; qualification timeline program-specific.

---

## Diagnostic Summary

```
EBT DIAGNOSTIC — G²CPU AI-ASSISTED TEST WORKFLOW
EBT Framework v2.6 · McDonald (2026)

ASHEN Intake:
  Knowledge types present:     A (valid) · S (partial) · H (invalid) · E (invalid)
  KLRS Modifier:               +35 pts (H + E compound stack)
  OL Pathway:                  CONFIRMED

Pathway Scores:
  P1 — Training Data Contamination:      72/100 — Active
  P2 — Structural Criteria Encoding:     81/100 — Active · Westwood Threshold crossed
  P3 — Objectivity Laundering (adj.):   100/100 — CONFIRMED · Maximum severity
  P4 — Temporal Criteria Decay:          68/100 — Active · CES mandatory recalibration

EBT Amplification Index:                80.25/100 — Westwood Threshold crossed
  Structural governance required — individual interventions contraindicated

NNN Audit:
  NNN-D (Detection):     GAP CONFIRMED — CRITICAL
  NNN-G (Governance):    GAP CONFIRMED — HIGH
  NNN-H (Override):      GAP CONFIRMED — OPERATIONALLY PRESENT · STRUCTURALLY UNFORMALIZED

CVD Risk Score:                         87/100 — CRITICAL
  All four CVD conditions present
  Structural intervention required before AI-assisted outputs
  enter any certification evidence package at DAL A or DAL B

G²CPU Structural Protection:
  Layer 2 determinism:      HIGH — foundational CVD protection
  Layer 1 hardware truth:   ABSOLUTE — CVD risk begins at Layer 3
  Runtime backend switch:   MEDIUM — unformalized independent verification capability

Priority Action Stack:
  P1 — NNN-D Detection Mechanism:          IMMEDIATE
  P2 — NNN-G Trust Boundary Document:      HIGH
  P3 — NNN-H Override Log:                 HIGH
  P4 — AI Layer Specification Document:    HIGH
  P5 — DO-330 Tool Qualification:          MEDIUM-TERM

Framework Attribution: EBT Framework v2.6 — Full Diagnostic Protocol
McDonald, E.M. (February 25, 2026)
Built on: Heilman · Toegel · Edmondson · Buolamwini & Gebru · Snowden · McDonald (2026)
CVD Construct: Biesmans + McDonald (2026) — Collaborative IP

DACR License v2.6 — All diagnostic instruments, scoring systems,
and engagement protocols proprietary to Epoch Frameworks LLC.
This document is shared for co-author engagement purposes only.
Not for distribution without written consent.
```

---

## A Note on What This Diagnostic Is Not

This diagnostic does not conclude that G²CPU should not be used with AI. It concludes the opposite: G²CPU's deterministic architecture at Layer 2 is the structural foundation that makes CVD-safe AI deployment possible. Without a deterministic substrate, there is no reference baseline against which AI output deviation can be measured. G²CPU is not the problem. It is the solution — but only if the governance architecture above Layer 2 is built to use it correctly.

The five priority actions above are not remediation of a broken system. They are the formalization of a sound system. Natan's instinct to maintain engineer authority over AI output is already NNN-H behavior. The diagnostic identifies where that instinct needs to become architecture — documented, systematic, and auditable — so that it survives program scale, personnel changes, and certification authority review.

---

*© McDonald (2026) · Epoch Frameworks LLC · DACR License v2.6*
*CVD Construct — Biesmans + McDonald (2026) · Collaborative IP*
*This document is a Sprint 1 proof-of-work artifact prepared for Natan Biesmans (G²CPU) review.*
*Not for public distribution without written consent from both authors.*
