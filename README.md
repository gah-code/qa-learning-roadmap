# QA Learning Roadmap

## Hands-On Learning Plan for the Quality Analyst (QA) Track

Use the checkboxes below and the project board to track your progress. This repository showcases a lightweight yet scalable workflow for learning Quality Assurance (QA) using GitHub Issues and a GitHub Project board. It allows for concurrent work on multiple topic groups within a single day (e.g., Monday).

---

## Week 1 — Foundation, Artifacts, and Job-ready Setup

**Outcome:** Rebuild QA fundamentals, create interview-ready artifacts, and be ready to apply.

### Monday

- [X] Review SDLC vs STLC
- [X] Review test levels (unit / integration / system / UAT)
- [X] Black-box techniques: Boundary Value Analysis (BVA) essentials
- [X] Black-box techniques: Equivalence Partitioning
- [X] Black-box techniques: State Transition
- [X] Black-box techniques: Error Guessing

### Tuesday

- [ ] Defect lifecycle & reporting
  - [ ] Severity vs priority (impact vs urgency)
  - [ ] Reproducibility (intermittent vs consistent; test data/state)
  - [ ] Minimal steps to reproduce (clear, numbered, self-contained)
  - [ ] Expected vs actual (concise oracles; specs/screenshots)
  - [ ] Environment (device/OS/browser, app build, data/config)

---

### How to use this repo

- Check off items here as you complete them.
- Each checklist item has a matching GitHub Issue you can work from.
- The Project board shows status at a glance.

- [Week 1 — Monday notes](notes/week1-monday.md)
- [Week 1 — Tuesday notes](notes/week1-tuesday.md)

---

# Project Configuration — Repo + Projects v2

This repository demonstrates a lightweight workflow for learning **Quality Assurance (QA)** with **GitHub Issues** and a **GitHub Project (v2)** board. It supports parallel work when a single day (e.g., Monday) includes multiple topic groups.

## Patterns for “multiple topics in the same day/timebox”

### 1) Parent (“Meta”) issue + child issues per topic group

- Create one **parent** issue for the day (e.g., “W1 Mon — Meta: Topic Groups A–F”).
- Create **child issues** per topic (Groups A–F).
- In the parent body, include a checklist that **references** each child via `- [ ] #<issue-number>`.
- **Result:** one-glance progress; each child flows independently on the Project board.

### 2) Single notes file with anchored sections

- Keep **one** notes file per day, e.g., `notes/week1-monday.md`.
- Give each group an **anchor**:  
  `#group-a-sdlc-vs-stlc`, `#group-b-test-levels`, `#group-c-bva`,  
  `#group-d-equivalence-partitioning`, `#group-e-state-transition`, `#group-f-error-guessing`.
- Each child issue **links to its section**.
- **Result:** tidy repo, zero duplication, clean audit trail.

---

## Steps 1–6 (CLI) for Week 1 → Monday (Groups A–F)

> Replace `gah-code/qa-learning-roadmap` and `PROJECT_NUMBER` as needed.  
> Avoid `$USER` (system variable). Use `GH_OWNER` and `GH_REPO`.

```bash
# Variables
GH_OWNER="gah-code"
GH_REPO="qa-learning-roadmap"
PROJECT_NUMBER=5
