---
title: EU Standards and Directives
# description: Welcome to the Macrolab knowledge base.
---

!!! info
    The information on this page is for guidance only and does not constitute legal advice. For formal interpretation or compliance decisions, contact TU Delft's legal department or the campus safety office.

## Purpose
This page collects concise references and practical notes about EU directives and harmonised standards that commonly apply to laboratory, test, and prototype equipment. It is written for researchers and engineers who design, build, or operate experimental setups and aims to help you identify areas that need attention during design, testing and handover.

## Scope and caveat
- The examples below are informational and not exhaustive.
- Experimental or rapidly-evolving setups often require bespoke risk assessments — the applicable requirements can change as a system grows or is repurposed.
- Always treat legal and conformity questions as issues for your institution's legal/safety teams.

## Key directives and regulations (high level)
- Machinery Directive (2006/42/EC): essential requirements for machinery safety, risk assessment and CE marking where applicable.
- Low Voltage Directive (2014/35/EU): safety of electrical equipment for use within certain voltage limits.
- Electromagnetic Compatibility (EMC) Directive (2014/30/EU): limits electromagnetic emissions and requires immunity to a reasonable level of disturbance.
- ATEX (equipment for explosive atmospheres, 2014/34/EU): applies if your setup handles explosive gases/ dust — often not relevant for typical lab rigs but essential for special cases.
- PPE Regulation (EU) 2016/425: applies to personal protective equipment placed on the market.

## Commonly referenced standards (examples)
- EN ISO 12100 — Safety of machinery — general principles for design and risk assessment.
- ISO 13849 / IEC 62061 — Functional safety of control systems (safety-related parts of control systems).
- IEC 61010-1 — Safety requirements for electrical equipment for measurement, control and laboratory use (commonly relevant for lab instruments).
- IEC 61508 — Functional safety of electrical/electronic/programmable electronic safety-related systems (higher-level functional safety standard).

Note: standards are updated periodically; always check the current edition before relying on a clause for design or conformity work.

## Practical checklist for experimental setups
1. Identify the intended use and reasonably foreseeable misuse.
2. Perform a basic hazard identification and risk assessment (start simple; iterate as the system changes).
3. Implement basic safeguards: guarding, interlocks, emergency stop, clear labelling and instructions.
4. Ensure electrical safety: correct wiring, earthing/grounding, fusing and safe connectors (refer to IEC 61010 for lab equipment).
5. Validate EMC where the equipment could cause or be affected by interference (or if required by product scope).
6. Keep a technical file / build record documenting design decisions, tests, and maintenance instructions.

If the equipment will be placed on the market or handed over to an external party, stronger conformity steps (formal risk assessments, harmonised standards, technical file, and CE marking where applicable) will likely be required.

## Where to get help
- Contact TU Delft's legal department for questions about directives, conformity, and placing equipment on the market.
- Contact the campus safety office or your local departmental safety officer for risk assessment support and lab-level approvals.
- Use official sources for legislation and harmonised standard references (e.g. EUR-Lex and the CEN/CENELEC documentation portals).

## Notes for Macrolab contributors
- When documenting an experimental rig in this knowledge base, include the intended use, known hazards, and any measures taken to reduce risk.
- Tag pages that describe experimental equipment with a clear disclaimer and maintenance notes so future users understand constraints.