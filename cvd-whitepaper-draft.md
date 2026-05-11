# Why AI Cannot Be Trusted to Validate What It Cannot Deterministically Execute
### *Introducing the Circular Validation Dependency (CVD) — A New Governance Construct for AI-Augmented Safety-Critical Test Systems*

---

![Status](https://img.shields.io/badge/STATUS-DRAFT_v0.1-A33030?style=for-the-badge&labelColor=2D3436&color=A33030)
![Attribution](https://img.shields.io/badge/AUTHORS-Biesmans_%2B_McDonald_(2026)-2D3436?style=for-the-badge&labelColor=2D3436&color=8E9FD5)
![Framework](https://img.shields.io/badge/FRAMEWORK-EBT_v2.7_%2B_NNN_v2.6-2D3436?style=for-the-badge&labelColor=2D3436&color=A78BFA)
![License](https://img.shields.io/badge/IP-DACR_v2.6_%2B_Joint_Attribution-2D3436?style=for-the-badge&labelColor=2D3436&color=596170)

> **Draft Status:** This document is a working draft prepared for co-author review by Natan Biesmans (G²CPU) prior to submission for publication at GDevCon and the NI Tools Network. All framework constructs are attributed as specified. No methodology is disclosed in full in this public draft.

---

**Natan Biesmans**
CEO, G²CPU | LabVIEW Champion | Certified LabVIEW Architect
g2cpu.com · info@g2cpu.com

**Erwin M. McDonald**
Founder and CEO, Epoch Frameworks LLC | Behavioral Intelligence Architect | AI Adoption Architect
Fort Worth, Texas · erwin.mcdonald@outlook.com

*Submitted for publication: GDevCon Annual Conference · NI Tools Network Technical Library*
*Manuscript version: 0.1 — Co-author review draft*
*Date: May 2026*

---

## Abstract

The integration of AI-assisted tooling into safety-critical test and validation workflows has accelerated faster than the governance frameworks needed to support it. Current certification standards — including DO-178C, ARP4754B, and DO-330 — formally acknowledge limitations in their applicability to AI and neural network-based systems, yet organizations continue to deploy AI inference layers above deterministic test substrates without a defined trust boundary between them.

This paper introduces the **Circular Validation Dependency (CVD)**, a new governance construct that names and formalizes a specific structural failure mode in AI-augmented test architectures: the condition where an AI system is employed to validate a safety-critical architecture it is structurally unqualified to assess, because the validation tool and the system under test share the same probabilistic foundation.

We propose a five-layer Trust Boundary Architecture grounded in the **Neural Network Navigation (NNN) Governing Layer** and the **Evaluative Bias Transference (EBT) Framework**, with G²CPU's deterministic GPU execution model positioned as the trusted computational substrate that CVD governance requires. We demonstrate that deterministic HPC execution is not merely a performance optimization in safety-critical contexts — it is a structural governance requirement.

The construct applies directly to LabVIEW-based test systems operating under DO-178C Design Assurance Levels A and B, including aerospace propulsion test, electronic warfare signal validation, and radar test platforms. The paper concludes with a proposed certification audit trail architecture and a set of governance questions program managers and system integrators should be able to answer before any AI-assisted test layer is accepted as part of a formal verification chain.

**Keywords:** Circular Validation Dependency, AI governance, safety-critical systems, DO-178C, DO-330, LabVIEW, G²CPU, EBT Framework, NNN Governing Layer, deterministic computing, tool qualification, trust boundary architecture

---

## 1. Introduction

### 1.1 The Problem in Plain Language

Imagine a test engineer at a $200M rocket program who is asked to use an AI-assisted analysis layer to validate flight-critical telemetry. The AI is fast, confident, and produces outputs that look like deterministic verdicts. The engineer, under schedule pressure, accepts the output. The program manager, reviewing the certification package, has no documentation showing where the AI layer ends and the deterministic substrate begins. A certification authority, reviewing the package, asks a question no one has prepared an answer for: *How do you know the AI did not contaminate the validation chain?*

This is not a hypothetical. It is a structural condition present in any organization that has introduced AI tooling into a safety-critical test workflow without first defining a governance boundary between the probabilistic inference layer and the deterministic execution layer.

The problem does not arise from bad engineering. It arises from the absence of a formal construct that names the failure mode and specifies the boundary conditions under which AI inference can and cannot be trusted in a verification chain.

This paper provides that construct.

### 1.2 The Gap in Current Standards

DO-178C, the primary software certification standard used by EASA, the FAA, and Transport Canada for airborne software, was designed for deterministic code. Its verification methodology — requirements traceability, structural coverage analysis, and review of outputs — assumes that software behavior can be fully specified in advance and tested against those specifications.

Neural networks do not satisfy this assumption. The DO-178C standard itself acknowledges this: the standard does not fully cover the challenges of AI-enabled systems. The FAA has issued guidance acknowledging that existing certification frameworks are not fully applicable to machine learning systems. EASA's AI trustworthiness framework — covering AI Assurance, Human Factors for AI, and AI Safety Risk Mitigation — is still in development as of 2026.

The result is a governance gap that grows wider every time an AI-assisted tool is introduced into a DAL A or DAL B verification workflow. **The standard admits it cannot handle what engineers are being asked to do. This paper proposes what fills that gap.**

### 1.3 The G²CPU Context

G²CPU is a GPU-accelerated high-performance computing toolkit for LabVIEW, built on the ArrayFire backend and fully compatible with NVIDIA CUDA, OpenCL, and Intel OneAPI. It is designed to enable LabVIEW developers to implement parallel signal processing, real-time data acquisition, and machine vision capabilities at performance levels that approach or exceed dedicated FPGA implementations — without the development overhead of FPGA-based solutions.

G²CPU's deterministic execution model — where the same algorithm produces the same output on the same hardware every time — is precisely the architectural property that makes it the correct substrate for safety-critical test systems. This is not incidental. It is the structural reason G²CPU belongs in the trust boundary architecture this paper proposes.

### 1.4 The EBT Framework Context

The Evaluative Bias Transference (EBT) Framework, coined by McDonald (February 25, 2026), identifies three pathways through which human evaluative bias enters AI architectures as unchallengeable output: Training Data Contamination, Structural Criteria Encoding, and Objectivity Laundering. The CVD construct described in this paper is a domain-specific instantiation of EBT Pathway 2 (Objectivity Laundering) operating in safety-critical engineering contexts.

The EBT Framework is licensed under the DACR License v2.6. The CVD construct is a collaborative contribution jointly attributed to Biesmans + McDonald (2026).

---

## 2. Background

### 2.1 Design Assurance Levels and AI Permissibility

DO-178C organizes software certification requirements by Design Assurance Level (DAL), which reflects the severity of failure conditions:

| DAL | Failure Condition | Consequence |
|-----|-----------------|-------------|
| A | Catastrophic | May cause loss of aircraft and occupants |
| B | Hazardous | Large negative impact on safety or performance |
| C | Major | Significant reduction in safety margins |
| D | Minor | Noticeable reduction in safety margins |
| E | No Effect | No impact on operational capability |

At DAL A and DAL B, the verification requirements are most stringent and the tolerance for unverifiable tool behavior is lowest. The use of automated tools — including AI inference tools — in DAL A/B verification chains is not prohibited by DO-178C, but it is subject to stringent Tool Qualification requirements under the companion standard DO-330.

**The practical implication is direct:** any AI-assisted tool used in a DAL A or DAL B verification chain must either be qualified under DO-330 or its outputs must be independently verified by means that do not rely on the tool itself. Most AI tools deployed in engineering workflows as of 2026 have not undergone DO-330 Tool Qualification. This is not a criticism — qualification is expensive and time-consuming. It is a statement of the governance gap.

### 2.2 DO-330 Tool Qualification and the AI Trust Problem

DO-330 defines three criteria under which a software tool must be formally qualified before it can be used in a safety-critical verification chain:

**Criterion 1:** The tool's output is part of, or contributes directly to, the airborne software — and could insert an error without being detected.

**Criterion 2:** The tool automates a verification process — and could fail to detect an error that the verification process was intended to find.

**Criterion 3:** The tool is used in a way where it could fail to detect an error within its intended use without detection by other means.

AI inference tools used to interpret test results, flag anomalies, or validate telemetry data against specifications fall under Criterion 2 at minimum and potentially Criterion 1 depending on how their outputs are consumed by downstream processes. To date, no widely available AI inference toolkit has undergone DO-330 Tool Qualification for DAL A or DAL B applications.

**This is the precise technical location of the CVD problem:** the AI layer exists in the verification chain, it meets one or more DO-330 qualification criteria, and it has not been qualified.

### 2.3 The EASA AI Trustworthiness Gap

EASA has acknowledged that the AI trustworthiness framework it is developing comprises three components: AI Assurance, Human Factors for AI, and AI Safety Risk Mitigation. As of 2026, this framework is still under development. There is no binding regulatory guidance that tells a LabVIEW systems integrator how to govern the boundary between an AI inference layer and a deterministic test execution layer in a DAL A/B workflow.

This absence of binding guidance does not mean the problem does not exist. It means organizations that resolve it proactively — before regulators require it — will have a governance advantage in certification audits.

---

## 3. The Circular Validation Dependency (CVD)

### 3.1 Formal Definition

**Circular Validation Dependency (CVD)** describes the structural condition in a safety-critical test architecture where:

1. An AI system is introduced to assist in the validation of test results or system behavior.
2. The AI system's outputs are treated as validation verdicts — deterministic conclusions about the system under test.
3. The AI system and the system under test share the same probabilistic foundation — meaning the AI cannot identify failure modes that were not represented in its training distribution.
4. No trust boundary is defined between the AI inference layer and the deterministic execution layer.
5. The result is a closed loop in which evaluative bias encoded in the AI system is never surfaced, because the evaluator and the evaluated cannot be meaningfully separated.

CVD is not a hallucination problem. Hallucination refers to AI-generated content that is factually incorrect. CVD refers to a structural architectural condition in which the AI is systematically unqualified to assess the system it is being asked to validate — and in which no mechanism exists to detect that disqualification.

CVD is, in the terminology of the EBT Framework, **Objectivity Laundering at safety-critical scale:** the process by which probabilistic AI output acquires the apparent authority of objective engineering verdict without the structural basis to support that authority.

### 3.2 The CVD Loop

The CVD failure mode follows a consistent four-step progression:

```
┌─────────────────────────────────────────────────────────────────┐
│                        THE CVD LOOP                             │
│                                                                 │
│  STEP 01  AI is introduced to assist safety-critical            │
│           test validation                                       │
│              ↓                                                  │
│  STEP 02  AI output is treated as deterministic test  ◄──────┐  │
│           verdict by engineers under schedule pressure         │  │
│              ↓                                                 │  │
│  STEP 03  The hallucination surface and bias transfer         │  │
│           remain invisible — until system-level failure        │  │
│              ↓                                                 │  │
│  STEP 04  Root cause analysis reveals the trust              ──┘  │
│           boundary was never defined                              │
│                                                                   │
│  OUTCOME  Certification authority cannot reconstruct             │
│           the validation chain — program delayed or failed        │
└───────────────────────────────────────────────────────────────────┘
```

### 3.3 Why CVD Is Different from Standard AI Risk

Standard AI risk frameworks address concerns including bias, fairness, transparency, and adversarial robustness. These are important concerns for enterprise AI deployments, but they do not address the specific structural condition that CVD names.

CVD is distinct in three ways:

**It is architecturally generated, not behaviorally generated.** CVD does not arise because the AI makes a wrong prediction. It arises because the architecture in which the AI operates does not provide the structural conditions necessary for the AI's outputs to be trustworthy in the first place.

**It is invisible at the point of failure.** Unlike a hallucination, which produces a clearly incorrect output, CVD allows the AI to produce outputs that are internally consistent and confidently presented — but structurally unsound relative to the safety-critical context.

**It is a governance failure before it is a technical failure.** The engineering team may have done technically competent work. The failure is in the absence of a defined boundary between what the AI is permitted to decide and what requires human engineering authority.

### 3.4 CVD in the LabVIEW Aerospace Context

In a typical LabVIEW-based aerospace or defense test system, the architecture at the point of CVD risk looks like this:

```
Physical Hardware (PXI / RADX PXIe-GPUs)
    ↓
Signal Acquisition and Processing (G²CPU / LabVIEW RT)
    ↓
[AI Inference Layer]  ← CVD RISK ZONE
    ↓
Test Verdict / Certification Evidence
```

The AI inference layer sits between the deterministic signal processing substrate and the certification evidence package. If the AI layer is unqualified under DO-330 and no trust boundary is defined, the certification evidence package contains outputs whose provenance is structurally ambiguous.

The G²CPU layer below the AI is deterministic. The certification evidence above the AI is binding. The AI layer in between is neither. **That is where CVD lives.**

---

## 4. The Trust Boundary Architecture

### 4.1 Design Principles

A trust boundary architecture for AI-augmented safety-critical test systems must satisfy four requirements:

1. **Structural separation:** The AI inference layer and the deterministic execution layer must be architecturally distinct, with a defined interface between them.
2. **Governed escalation:** Any AI output that approaches safety-critical decision territory must pass through a governed escalation path before entering the certification evidence chain.
3. **Auditable authority:** Every decision in the verification chain must have an identifiable human authority owner whose judgment is documented and traceable.
4. **Certification survivability:** The governance architecture must produce documentation that survives a certification authority review — meaning it must answer the question of how AI output was validated before being accepted into the evidence package.

### 4.2 The Five-Layer Architecture

We propose the following five-layer Trust Boundary Architecture for AI-augmented safety-critical test systems using G²CPU:

```
┌────────────────────────────────────────────────────────────────────┐
│  LAYER 5  │  ENGINEER DECISION AUTHORITY                           │
│           │  Final call on all safety-critical test verdicts.      │
│           │  No AI output, regardless of confidence score,         │
│           │  overrides this layer. NNN-H enforced.                 │
│           │  Authority: Designated Engineer / DER                  │
├───────────┼────────────────────────────────────────────────────────┤
│  LAYER 4  │  NNN GOVERNANCE + CGM CRITERIA MONITORING              │
│           │  Criteria drift detection. Output deviation scoring.   │
│           │  Prompt integrity verification. Escalation path        │
│           │  enforcement. Certification audit log generation.      │
│           │  All AI recommendations logged before Layer 5 review.  │
├───────────┼────────────────────────────────────────────────────────┤
│  LAYER 3  │  AI-ASSISTED PATTERN RECOGNITION                       │
│           │  Anomaly detection. Telemetry pattern analysis.        │
│           │  Signal processing intelligence. Advisory output only. │
│           │  EBT-gated: outputs flagged, not acted upon, without   │
│           │  Layer 4 clearance. No direct execution authority.     │
├───────────┼────────────────────────────────────────────────────────┤
│  LAYER 2  │  G²CPU SIGNAL PROCESSING (DETERMINISTIC SUBSTRATE)     │
│           │  GPU-accelerated HPC via ArrayFire.                    │
│           │  CUDA / OpenCL / CPU backends.                         │
│           │  Same algorithm, same hardware, same output every time. │
│           │  This is the trust substrate. Everything above it      │
│           │  depends on this layer for structural validity.        │
├───────────┼────────────────────────────────────────────────────────┤
│  LAYER 1  │  PXI / RADX HARDWARE                                   │
│           │  Physical measurement and signal acquisition.          │
│           │  RADX NVIDIA-based PXIe-GPUs.                          │
│           │  Ground truth source. Hardware reality.                │
└───────────┴────────────────────────────────────────────────────────┘
```

### 4.3 The NNN Governing Layer

The Neural Network Navigation (NNN) Governing Layer, a component of the EBT Framework v2.6, operates at Layer 4 of the Trust Boundary Architecture. It provides three governance modes relevant to safety-critical test systems:

**NNN-D (Detection Mode)**
Monitors AI output for deviation from defined engineering criteria. In the G²CPU context, any AI-generated test result that cannot be traced to a deterministic execution record in Layer 2 triggers a detection flag before the result enters Layer 4 processing. Detection flags are logged with timestamp and device ID for certification audit purposes.

**NNN-G (Governance Mode)**
Defines and enforces the boundary between AI advisory authority and engineer execution authority. AI governs pattern recognition and anomaly flagging at Layer 3. G²CPU governs deterministic execution at Layer 2. The boundary between these layers is enforced by NNN-G, not assumed. Boundary violations — cases where AI output is treated as execution instruction without Layer 4 review — are flagged and logged.

**NNN-H (Human Override Mode)**
Ensures that no AI output, regardless of confidence score or output format, can override a qualified engineer's judgment on a safety-critical test verdict. NNN-H is not a technical control. It is a documented governance requirement that specifies: (a) who holds final decision authority, (b) what the escalation path is when AI output conflicts with engineering judgment, and (c) how that decision is logged in a form that survives certification audit.

**NNN-H formalizes what competent engineers already do intuitively.** The value is not in creating new engineering behavior. The value is in making that behavior auditable and documentable for certification purposes.

### 4.4 The Three Questions a Program Manager Must Be Able to Answer

Before any AI-assisted test layer is accepted as part of a formal verification chain, the program manager should be able to answer three questions. These questions are not engineering questions — they are governance questions. If the engineering team can answer them but the program manager cannot, the governance architecture does not yet exist.

**Question 1 — The Certification Trigger**
*"When this program submits for certification review, what documentation trail exists to show that the AI-assisted test layer did not contaminate the validation chain? Not the G²CPU output — the AI layer above it."*

This question asks for the paper trail. It forces the organization to articulate, in advance of a certification review, how AI output was governed before it entered the evidence package.

**Question 2 — The Tool Qualification Status**
*"Has the AI inference layer been assessed under DO-330 Criterion 2 for the DAL level this program is operating at? If not, how has its output been independently verified by means that do not rely on the tool itself?"*

This question asks whether the organization has satisfied the regulatory requirement for tools used in automated verification processes. The answer is almost always that formal DO-330 qualification has not been completed — and the response to that answer must be a defined independent verification process, not an assumption that the tool is sufficiently reliable.

**Question 3 — The CVD Governance Gap**
*"If the AI layer produces a result that conflicts with the G²CPU telemetry output — who owns that decision, what is the documented escalation path, and how does that decision get logged in a form that survives a certification audit?"*

This question asks whether the trust boundary is actually defined. If the answer is "the engineer" without a documented escalation path, a designated authority owner, and an audit log, the governance architecture does not exist. The engineer may do the right thing — but the certification evidence package will not be able to prove it.

---

## 5. CVD in Electronic Warfare and Radar Test Systems

### 5.1 Expanding the Application Context

While the CVD construct was initially developed in the context of aerospace propulsion test validation, its application extends directly to any safety-critical or mission-critical system where AI inference is introduced above a deterministic test substrate. Electronic warfare (EW) and radar test systems represent a second major application domain where CVD risk is present and the governance gap is equally unaddressed.

In EW applications, the G²CPU Wideband RTSA Toolkit — deployed with RADX NVIDIA-based PXIe-GPUs — enables real-time signal analysis at up to 1.25 Gigasamples per second with 100% Probability of Intercept for signals as short as 1.6 nanoseconds. At this performance level, the system is operating at the boundary of what any human operator can independently verify in real time.

When AI-assisted signal classification or threat identification is introduced into this workflow, CVD risk becomes acute: the AI is being asked to classify signals whose correct classification depends on pattern recognition across a training distribution that may not include the specific threat signatures the system is expected to detect in the field.

### 5.2 The EW-Specific CVD Condition

In an EW test context, the CVD condition manifests as follows:

The AI classifier is trained on a library of known signal signatures. It performs well on signals that resemble its training distribution. It produces confident outputs — including on signals that fall outside its training distribution, where it may misclassify or fail to classify at all.

The G²CPU RTSA layer below the AI is providing deterministic FFT processing and spectrum analysis. The AI layer above it is providing signal classification. The human operator at the top of the chain is receiving a classification verdict without visibility into whether that verdict was produced from a signal within the AI's competence boundary.

**If the AI produces a false negative on a threat signal — classifying it as benign — the mission-critical consequence is not a failed certification. It is a failed mission.** CVD at this level is not a regulatory risk. It is an operational risk.

### 5.3 The NNN-H Requirement in EW Contexts

The NNN-H requirement — that no AI output can override a qualified human operator's judgment on a safety-critical or mission-critical decision — takes on specific operational meaning in EW and radar test contexts:

The AI layer must be explicitly configured as an advisory layer. Its outputs must be presented to the human operator as recommendations, not verdicts. The operator must have unambiguous authority to override any AI classification. And the system must log the operator's override decision with the AI's original recommendation, enabling post-mission analysis of cases where human judgment diverged from AI output.

This is not a novel operational security requirement. It is a formal expression of what competent EW operators and test engineers already practice. The governance value of NNN-H in this context is: it makes the boundary documentable, auditable, and systematically enforceable across an entire program — not dependent on the individual discipline of each operator.

---

## 6. Proposed Certification Audit Trail Architecture

### 6.1 What a Certification Authority Will Ask

Based on the DO-178C verification requirements and the emerging EASA AI trustworthiness framework, a certification authority reviewing an AI-augmented test system in a DAL A or DAL B program will need to answer at least the following questions from the evidence package:

1. Is the AI tool used in the verification chain qualified under DO-330? If not, how has its output been independently verified?
2. Can the program demonstrate that the AI layer did not introduce undetected errors into the verification evidence?
3. Is there a documented boundary between AI advisory outputs and engineer decision authority?
4. Is there a documented escalation path for cases where AI output conflicts with engineering judgment?
5. Are all cases where human judgment overrode AI recommendation logged and traceable?

### 6.2 The Minimum Viable Governance Package

An organization deploying AI-assisted tooling in a DAL A or DAL B test workflow should maintain the following minimum governance documentation:

**AI Layer Specification Document**
Defines the AI tool's intended use, its input and output specifications, its known limitations (including training distribution boundaries), and its explicit exclusion from execution authority.

**Trust Boundary Definition**
A formal architecture document — equivalent in rigor to an Interface Control Document — specifying Layer 2 (deterministic substrate), Layer 3 (AI advisory), Layer 4 (NNN governance), and Layer 5 (engineer authority). Defines the escalation path for Layer 3 output before it may influence Layer 5 decisions.

**DO-330 Assessment Record**
Documents the DO-330 criteria assessment for each AI tool in the verification chain, identifies which criteria apply, and specifies either the qualification evidence or the independent verification means used in lieu of qualification.

**NNN-H Override Log**
A systematic log of all cases where Layer 5 engineer authority diverged from Layer 3 AI advisory output, with: timestamp, device ID, AI recommendation, engineer decision, and engineer rationale. This log is the primary evidence that the trust boundary was operationally enforced — not merely documented.

**CVD Risk Assessment**
A structured assessment of where in the test workflow CVD conditions are present, what mitigation is in place at each CVD risk point, and which DO-330 criteria are triggered by each AI tool in the chain.

---

## 7. Implications for G²CPU Users

### 7.1 G²CPU as Governance Infrastructure

The argument of this paper has implications for how G²CPU users should understand the role of their toolkit in a safety-critical architecture. G²CPU is positioned by its developers as a performance toolkit — delivering up to 250x faster performance compared to standard LabVIEW processing. This is accurate and significant.

But in a safety-critical context, G²CPU's deterministic execution model is not merely a performance property. It is a governance property. It is the structural characteristic that makes G²CPU a valid Layer 2 substrate in the Trust Boundary Architecture: the same algorithm produces the same output on the same hardware every time, and that output can be logged, traced, and independently verified.

When an AI layer is introduced above G²CPU, the deterministic property of Layer 2 does not automatically extend to Layer 3. The governance architecture must be explicitly designed to prevent Layer 3's probabilistic outputs from contaminating the Layer 2 traceability chain.

### 7.2 Practical Implementation Guidance

For G²CPU users operating in DAL A/B environments or in mission-critical EW/radar test contexts, the following practical implementation guidance follows from the Trust Boundary Architecture:

**Do not expose G²CPU execution parameters to AI layer control.** AI advisory outputs should inform engineer decisions at Layer 5. They should not dynamically configure execution parameters at Layer 2 without Layer 4 review and Layer 5 authorization.

**Log G²CPU outputs independently of AI processing.** Maintain a raw output log from the G²CPU layer that exists before AI processing occurs. This log provides the independent verification baseline that DO-330 requires when AI tool qualification has not been completed.

**Define the conflict resolution protocol before deployment.** Before any AI inference layer goes into operational use in a verification chain, the answer to Question 3 above must exist in writing: who owns the decision when AI output conflicts with G²CPU telemetry, what is the documented escalation path, and how is the resolution logged.

**Treat NNN-H as an operational requirement, not a best practice.** In DAL A/B and EW/radar contexts, NNN-H is not optional. The boundary between AI advisory authority and human engineering authority must be operationally enforced, not merely acknowledged in architecture documentation.

---

## 8. Conclusion

The introduction of AI into safety-critical test and validation workflows is not inherently unsafe. AI-assisted pattern recognition, anomaly detection, and telemetry analysis can meaningfully enhance engineering capability in complex test environments. The problem is not the AI. The problem is the absence of a governance architecture that defines where AI authority ends and human engineering authority begins.

The Circular Validation Dependency names a specific structural failure mode that emerges when that boundary is absent. CVD is not a prediction of AI behavior. It is a description of an architectural condition that makes AI behavior ungovernable in the contexts where it matters most.

The Trust Boundary Architecture proposed in this paper — grounded in G²CPU's deterministic execution model at Layer 2, the NNN Governing Layer at Layer 4, and documented engineer authority at Layer 5 — provides the structural framework within which AI-assisted test tooling can be deployed without creating CVD conditions.

The three questions posed in Section 4.4 are the diagnostic instrument. If a program manager can answer them — in writing, with documentation that survives a certification audit — the governance architecture is sound. If not, CVD is present, and the program's certification risk is higher than the engineering team may realize.

**The standard admits it cannot handle what engineers are being asked to do.** This paper proposes what fills the gap.

---

## References

Biesmans, N. (2025). *G2CPU Wideband RTSA Software Toolkit.* Press release, RADX Technologies and G2CPU, AOC 2025, National Harbor, MD.

EASA (2023). *Artificial Intelligence Roadmap 2.0 — Human-Centric Approach to AI in Aviation.* European Union Aviation Safety Agency.

FAA (2023). *FAA Safety Risk Management Policy for AI/ML in Aviation.* Federal Aviation Administration.

RTCA (2012). *DO-178C: Software Considerations in Airborne Systems and Equipment Certification.* RTCA.

RTCA (2011). *DO-330: Software Tool Qualification Considerations.* RTCA.

SAE International (2010). *ARP4754B: Guidelines for Development of Civil Aircraft and Systems.* SAE International.

McDonald, E.M. (2026). *Evaluative Bias Transference (EBT) Framework v2.6.* Epoch Frameworks LLC. DACR License v2.6.

McDonald, E.M. (2026). *Neural Network Navigation (NNN) Governing Layer v2.6.* In: EBT Framework v2.6. Epoch Frameworks LLC. DACR License v2.6.

Biesmans, N. & McDonald, E.M. (2026). *Circular Validation Dependency (CVD) — Collaborative Construct.* G²CPU / Epoch Frameworks LLC. Joint attribution, DACR License v2.6.

---

## Appendix A — CVD Risk Assessment Template

The following template provides a structured starting point for a CVD Risk Assessment in a LabVIEW-based safety-critical test system. This template does not constitute complete DO-330 documentation and should be supplemented with program-specific evidence as required by the applicable certification basis.

| Assessment Item | Description | CVD Risk Level | Mitigation |
|----------------|-------------|---------------|------------|
| AI tool identification | List all AI inference tools in the verification chain | N/A | Document tool name, version, supplier |
| DO-330 criteria assessment | Assess each tool against Criteria 1, 2, and 3 | N/A | Document which criteria apply and why |
| Qualification status | Has the tool been qualified under DO-330? | High if unqualified | Independent verification means or formal qualification |
| Training distribution boundary | What signal types / failure modes are outside the AI's training distribution? | High if undocumented | Formal limitation documentation per AI Layer Specification |
| Trust boundary definition | Is Layer 3 / Layer 4 / Layer 5 boundary documented? | Critical if absent | Trust Boundary Definition document |
| Conflict resolution protocol | Is Question 3 answered in writing? | Critical if absent | Documented escalation path and authority assignment |
| NNN-H override log | Is the override log operational? | High if absent | NNN-H log system deployed and in operational use |
| Independent output baseline | Is a raw Layer 2 output log maintained pre-AI processing? | High if absent | Automated logging of G²CPU outputs before AI processing |

---

## Appendix B — Author Notes on Co-Authorship and IP

The CVD construct is the result of a collaborative intellectual exchange between Natan Biesmans (G²CPU) and Erwin M. McDonald (Epoch Frameworks LLC). The construct was first articulated in conversation and subsequently formalized through the EBT Framework architecture.

**Attribution:** Biesmans + McDonald (2026). Both authors retain joint attribution rights on the CVD construct as defined in Appendix B of the DACR License v2.6.

**EBT Framework elements** (NNN Governing Layer, Objectivity Laundering, Trust Boundary Architecture) are proprietary to Epoch Frameworks LLC under DACR License v2.6. Their inclusion in this paper is for purposes of construct formalization and does not constitute public disclosure of diagnostic instruments, scoring systems, or engagement protocols.

**G²CPU technical content** (architecture, performance specifications, RADX integration details) is proprietary to G²CPU and Natan Biesmans. Its inclusion in this paper is for purposes of Trust Boundary Architecture specification and does not constitute disclosure of G²CPU source code or internal implementation details.

This paper may be shared, cited, and distributed with full attribution. It may not be modified or adapted without written consent from both authors.

---

*© Biesmans + McDonald (2026) · G²CPU / Epoch Frameworks LLC*
*CVD Construct — Collaborative IP · Joint Attribution*
*All EBT Framework elements — DACR License v2.6 · McDonald (2026)*
*All G²CPU technical content — Proprietary · Biesmans (2026)*
