# Engineering Assumptions

## Purpose and Scope

This document enumerates the **engineering-level assumptions** used across the formal invariants, simulations, and schematic representations in this repository. It exists to make implicit choices explicit and to bound interpretation. It is not a performance claim, a product specification, or a deployment forecast.

All quantities and ranges here are intended as **modeling parameters** suitable for sensitivity analysis and reproducibility, not as guaranteed achievable values in any specific fabrication process.

---

## Architectural Boundary

The assumptions below apply to a **minimum closed reversible photonic core** with the following properties:

* Optical energy is stored within high-Q photonic structures during reversible evolution.
* Logical state evolution is bijective during hold phases.
* Dissipation occurs only at explicit boundaries: configuration, measurement, or controlled loss.
* Hybrid electronic subsystems (control, biasing, sensing) are operated under adiabatic regimes.

No assumptions are made about system packaging, network topology, or commercial deployment.

---

## Energy Accounting Model

### Stored Energy (E_store)

* Represents total optical (and auxiliary electrical) energy actively participating in reversible evolution.
* Modeled as conserved during hold phases.
* Scales with the number of photonic elements under active phase control.

Typical modeling range (illustrative):

* **Per resonant element:** 10–300 pJ
* **Aggregated cores:** linear scaling with element count

These values are chosen to remain well above thermal noise floors while remaining compatible with low-loss photonic operation.

---

### Configuration Energy (ε_cfg)

Configuration energy represents the **irreversible energy expenditure** required to change system state, including:

* Phase shifter adjustments
* Carrier depletion or injection events
* Electronic control transitions

Assumed properties:

* Configuration events are discrete and countable.
* Energy per event is bounded and does not scale with hold time.

Illustrative modeling range:

* **Per phase adjustment:** ~0.05–0.2 pJ
* **Per configuration cycle:** proportional to number of adjusted elements

---

### Configuration Count (N_cfg)

* Counts the number of distinct reconfiguration events over an operational interval.
* Independent of clock frequency during hold phases.
* Treated as sparse relative to reversible evolution steps.

In simulations, N_cfg is treated as an external workload parameter rather than an architectural constant.

---

## Dissipation Bound Assumption

Across this repository, dissipation is modeled using a **fractional bound**:

> Total dissipated energy ≤ k × E_store

where:

* *k* is a dimensionless dissipation fraction (0 < k < 1)
* *E_store* is the total stored energy participating in reversible evolution

Illustrative modeling range:

* **k ≈ 0.05–0.1** for combined photonic + electronic subsystems

This bound is enforced structurally in formal proofs and numerically in simulations. It is not assumed to be optimal or minimal.

---

## Leakage and Loss During Hold

Passive loss during reversible hold phases is modeled as:

* Negligible relative to configuration loss for sufficiently high-Q systems
* Independent of computational depth

For modeling purposes:

* Hold-phase leakage is either neglected or treated as a small additive term well below configuration loss

This assumption is explicitly stated in all analyses that omit hold-phase dissipation.

---

## Hybrid System Composition

When electronic and photonic subsystems are composed:

* Dissipation contributions are treated as **additive**.
* No hidden cross-terms are assumed between subsystems.
* Adiabatic governors ensure monotonic energy transitions.

This assumption underpins the hybrid additivity invariant formalized in Lean.

---

## Scaling Interpretation

All scaling plots and tables in this repository should be interpreted as:

* **Energy-envelope illustrations**, not throughput guarantees
* Valid only within the stated dissipation bounds
* Independent of specific workloads, algorithms, or software stacks

No claim is made that any particular scale is economically or practically optimal.

---

## What These Assumptions Do *Not* Imply

* No guarantee of fabrication yield
* No claim of near-term manufacturability
* No assertion of superiority over existing commercial systems
* No implied endorsement by institutions or standards bodies

They exist solely to make the formal and numerical work interpretable.

---

## Relationship to Other Documents

* **Formal enforcement:** `lean/`
* **Numerical exploration:** `sims/`
* **Scenario framing:** `docs/iam_scenario_note.md`
* **Archival reference:** Zenodo technical note

This document is intentionally conservative and incomplete by design.
