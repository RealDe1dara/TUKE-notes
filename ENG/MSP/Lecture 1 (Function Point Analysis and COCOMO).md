# Lecture 1: Function Point Analysis and COCOMO

> **MSP | Software project estimation**

## 1. Why estimate software projects?

Software functionality is difficult to measure. Unlike a civil engineering project, where an architect can estimate square metres, a software architect must estimate effort, time, and cost from less tangible requirements.

Ad hoc or expert estimates are common because early project information is incomplete and domains differ. Their accuracy is inconsistent, which can lead to budget and schedule overruns. Function Point Analysis (FPA) and COCOMO provide more repeatable, evidence-based estimation methods.

## 2. Function Point metrics

Function Points measure the **functional size** of software from the user's perspective. They were developed by Allan Albrecht at IBM.

> **Important:** functional size and development effort are different quantities. They correlate, but are not the same.

FP was introduced partly to move away from Lines of Code (LOC), because LOC depends on the chosen programming language and is difficult to estimate early in the lifecycle.

### Typical uses of FPA

- define and negotiate project scope;
- evaluate requirements and replacement impact;
- estimate replacement cost and project resources;
- allocate testing resources and assess risk;
- phase development and monitor functional creep;
- assess and prioritise work;
- benchmark productivity and identify best practices;
- plan support resources, budgets, and new releases;
- evaluate software assets.

## 3. Estimation workflow

1. Count the system's functions and calculate **Unadjusted Function Points (UFP)**.
2. Assess complexity and calculate the **Value Adjustment Factor (VAF)** and **Adjusted Function Points (AFP)**.
3. Convert FP to LOC using the selected implementation language.
4. Select the appropriate project mode and coefficients from the COCOMO table.
5. Calculate estimated effort, duration, and staffing.

### Core formulas

$$
VAF = 0.65 + \frac{\sum_i SM_i}{100}
$$

$$
AFP = UFP \times VAF
$$

$$
E = a_b(KLOC)^{b_b}\quad\text{[person-months]}
$$

$$
D = c_b(E)^{d_b}\quad\text{[months]}, \qquad P = \frac{E}{D}\quad\text{[people]}
$$

### Formula guide

| Symbol | Meaning |
| --- | --- |
| **UFP** | Raw function-point count before complexity adjustment. |
| **SMᵢ** | Score for the *i*-th system characteristic, such as performance or security. |
| **ΣSMᵢ** | Sum of all characteristic scores. |
| **VAF** | Value Adjustment Factor; a multiplier that reflects system complexity. |
| **AFP** | Adjusted Function Points: **UFP × VAF**. |
| **KLOC** | Thousands of lines of code. **20 KLOC** means 20,000 lines. |
| **E** | Effort in person-months: the total amount of work. |
| **D** | Duration in calendar months: how long the project takes. |
| **P** | Average staffing: **E ÷ D** people. |
| **aᵦ, bᵦ** | Coefficients controlling the effort estimate. |
| **cᵦ, dᵦ** | Coefficients converting effort into calendar duration. |

The subscript **b** identifies the coefficient set for the selected COCOMO mode. These coefficients come from a COCOMO table; they are not guessed.

### In one example

Suppose the project is estimated at 20 KLOC and the selected illustrative coefficients are **aᵦ = 2.4**, **bᵦ = 1.05**, **cᵦ = 2.5**, and **dᵦ = 0.38**:

1. Calculate total work: **E = 2.4 × 20^1.05 ≈ 55.8 person-months**.
2. Calculate calendar time: **D = 2.5 × 55.8^0.38 ≈ 11.5 months**.
3. Calculate average team size: **P = 55.8 ÷ 11.5 ≈ 4.8 people**.

So the estimate is about **56 person-months of work**, completed in **11.5 months** by an average team of **5 people**. The real coefficients depend on the COCOMO mode and project data.

## 4. Experimental rules of thumb

- **1 FP approximately 100 LOC**;
- documentation pages **approximately FP^1.15**;
- estimated tests **approximately FP^1.12**;
- a review finds approximately 30% of errors;
- development time **approximately FP^0.4**;
- development staff **approximately FP / 150**;
- maintenance staff **approximately FP / 500**;
- for an organic project, effort is approximately **2.4 × KLOC^1.05**.

These relationships are empirical approximations and should be calibrated against historical project data.

## 5. COCOMO

**COCOMO** means **Constructive Cost Model**. Barry W. Boehm developed it as an algorithmic model for software cost estimation. It uses regression formulas whose parameters come from historical project data and project characteristics.

### COCOMO 81

- **Basic:** quick, early, rough-order-of-magnitude estimate based mainly on program size;
- **Intermediate:** adds cost drivers and their effort multipliers;
- **Detailed:** also models the influence of individual development phases.

Development modes:

- **Organic:** small, experienced teams and relatively flexible requirements;
- **Semi-detached:** medium teams with mixed experience and mixed requirements;
- **Embedded:** systems developed under tight hardware, software, or operational constraints.

### Intermediate COCOMO cost drivers

The 15 attributes are rated from *very low* to *extra high*. Their effort multipliers are multiplied to produce the **Effort Adjustment Factor (EAF)**. Typical EAF values range from approximately **0.9** to **1.4**.

- **Product:** required reliability, database size, product complexity;
- **Hardware:** runtime performance, memory, virtual-machine volatility, turnaround time;
- **Personnel:** analyst capability, software-engineering capability, application experience, virtual-machine experience, programming-language experience;
- **Project:** software tools, software-engineering methods, required development schedule.

### COCOMO II

COCOMO II is intended for modern software processes. Its model names are **Application Composition**, **Early Design**, and **Post-Architecture**. Its scale factors include **PREC**, **FLEX**, **RESL**, **TEAM**, and **PMAT**.

## Exam checklist

- Explain why FP is not the same as effort.
- Distinguish UFP, VAF, and AFP.
- Know the FP-to-LOC conversion and estimation workflow.
- State the three COCOMO 81 levels and project modes.
- Explain Basic, Intermediate, and Detailed COCOMO.
- Name the COCOMO II model stages and scale factors.

### Key takeaway

Use FPA to estimate **what the software provides** (functional size), then use a calibrated cost model such as COCOMO to estimate **what it takes to build it** (effort, time, and people).