# IAM Scenario Note

## Purpose

This note explains **why a Reversible Photonic Computing (RPC) core exists**, who it is for, and under what institutional and system-level constraints it is intended to operate. It is deliberately non-mathematical and non-promotional. Its role is to make the surrounding technical material legible to reviewers, funders, and standards-adjacent readers.

This document is an *interpretive companion* to the formal invariants, simulations, and scaling analyses archived via Zenodo and implemented in this repository.

---

## Scenario Framing: Infrastructure, Not a Product

RPC is not framed as a device, SKU, or near-term product. It is framed as a **minimum closed reversible photonic core**, used here as an **analytical modeling construct**, whose only unavoidable dissipation is configuration.

The relevant question is therefore not:

> “What application does this run?”

but rather:

> “In what infrastructure scenarios does bounded-dissipation, reversible computation become systemically meaningful?”

The IAM (Infrastructure–Assurance–Mission) scenario addresses this question as a **modeling and sensitivity-analysis framework**, not as a forecast or deployment claim.

---

## Infrastructure Context

The target environments are large-scale computational infrastructures where:

* Energy cost dominates lifecycle cost (OPEX > CAPEX)
* Thermal constraints, not transistor density, limit scaling
* Long-lived state, synchronization, and coordination matter more than peak clock rate

Examples include:

* Scientific and climate modeling facilities
* National or regional data infrastructure
* Long-horizon AI training and inference systems
* Mission-critical or continuously operating compute services

RPC is positioned as a **substrate option** within such infrastructures, not as a wholesale replacement for existing architectures.

---

## Assurance Context

A defining feature of RPC is that its energy behavior is *explicitly bounded and audited* **within the assumptions of the formal model**.

Assurance here means:

* Dissipation is structurally accounted for, not empirically hoped for
* Energy loss is confined to configuration and measurement boundaries
* Hybrid electronic–photonic systems compose without hidden cross-terms

This assurance is established through:

* Formal invariants (Lean 4 / Mathlib)
* Explicit energy models
* Simulation-backed scaling analysis

The goal is not optimal performance, but **predictable behavior under scale**.

---

## Mission Alignment

RPC aligns most naturally, *as a scenario construct*, with missions where:

* Energy efficiency is a hard constraint, not a marketing metric
* Long-term operability matters more than short-term benchmarks
* Governance, physics, and accounting must agree

This includes public-interest computing, regulated environments, and systems where externalized energy cost is no longer acceptable.

The framework is intentionally conservative: it prefers proofs, bounds, and invariants over speculative gains.

---

## Relationship to Standards Bodies

This work is **not** a standards proposal and does not claim endorsement by any standards organization.

Concepts, terminology, and framing are chosen to be compatible with standards-adjacent discussion (e.g., energy accounting, system assurance), but no institutional branding, authority, or approval is implied.

Any references to international or public institutions are contextual only and do not imply coordination, endorsement, participation, or standards activity.

---

## Relationship to Zenodo

The associated Zenodo record serves as the **archival, citable technical reference** for this work; all scenario descriptions here are subordinate to and consistent with that archive. This repository:

* Expands, annotates, and operationalizes that record
* Provides working artifacts (code, simulations, diagrams)
* Does not supersede the Zenodo archive

Zenodo and GitHub are used in a complementary way: Zenodo for permanence and citation, GitHub for iteration and transparency.

---

## What This Scenario Is *Not*

* Not a commercialization plan
* Not a deployment commitment
* Not a claim of institutional backing
* Not a performance benchmark report

It is a framing document intended to reduce misinterpretation, not to motivate policy action or investment decisions.

---

## Reading Guidance

Readers looking for:

* **Formal guarantees** → see `lean/`
* **Numerical scaling behavior** → see `sims/`
* **Energy accounting assumptions** → see `docs/engineering_assumptions.md`

This note exists solely to explain *why those artifacts exist at all*.
