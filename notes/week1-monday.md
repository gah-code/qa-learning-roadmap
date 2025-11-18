# Week 1 — Monday Notes

<a id="group-a-sdlc-vs-stlc"></a>

## Group A — SDLC vs STLC

### SDLC (Software Development Life Cycle)

- **Scope:** The entire process of creating and maintaining a software product.
- **Purpose:** To ensure high-quality software is built from start to finish.
- **Typical phases:**
  - **Planning** – define goals, scope, constraints, and feasibility.
  - **Analysis** – gather and analyze requirements.
  - **Design** – design architecture, components, and data structures.
  - **Implementation (Coding)** – write and integrate code.
  - **Testing** – verify the software against requirements.
  - **Deployment** – release the software to users.
  - **Maintenance** – fix bugs, improve performance, and adapt to change.
- **Outcome:** A fully developed software system delivered and maintained over time.

### STLC (Software Testing Life Cycle)

- **Scope:** A structured process specifically for testing activities within the SDLC.
- **Purpose:** To identify defects and ensure the software meets requirements and quality standards.
- **Typical phases:**
  - **Requirement Analysis** – understand what needs to be tested.
  - **Test Planning** – define scope, approach, resources, and schedule.
  - **Test Case Design** – design and document test cases and test data.
  - **Test Environment Setup** – prepare environment, tools, and data.
  - **Test Execution** – run tests, log results, and report defects.
  - **Test Cycle Closure** – evaluate test completion, metrics, and lessons learned.
- **Outcome:** A tested software product with identified defects fed back to the development team.

**Diagram:** `./img/sdlc-vs-stlc.png`  *(or external URL)*

---

<a id="group-b-test-levels"></a>

## Group B — Test levels (unit / integration / system / UAT)

**Test Levels:** The four main levels of software testing are **unit**, **integration**, **system**, and **User Acceptance Testing (UAT)**. They move from testing individual components to validating the final product with end-users.

### Unit Testing

- **What it is:** Tests the smallest testable parts of the software, such as individual functions or methods, in isolation.
- **Focus:** Verifying the correctness of individual code units.
- **Typical owner:** Developers.
- **Failure signals:** Failing assertions, incorrect return values, or exceptions inside a single function/method.

### Integration Testing

- **What it is:** Tests the interaction and data flow between two or more integrated modules or services.
- **Focus:** Ensuring modules work correctly when combined, including interfaces and communication between them.
- **Typical owner:** Developers / QA (shared).
- **Failure signals:** Incorrect data exchanged between modules, broken APIs, interface mismatches.

### System Testing

- **What it is:** Tests the complete and integrated software system as a whole.
- **Focus:** Evaluating the system’s compliance with specified requirements and ensuring it functions correctly in an environment similar to production.
- **Typical owner:** QA team.
- **Failure signals:** End-to-end flows breaking, missing or incorrect features, performance/behavior issues at system level.

### User Acceptance Testing (UAT)

- **What it is:** The final stage of testing before release, where actual users or clients test the software in a real-world scenario.
- **Focus:** Validating that the software meets the users’ needs and is ready for deployment.
- **Typical owner:** Business users / clients / product owners.
- **Failure signals:** “This doesn’t match how we work,” missing business rules, usability problems, or unmet requirements.

---

## Black-box design — Overview

Black-box design techniques like **equivalence partitioning**, **boundary value analysis**, **state transition testing**, and **error guessing** are methods to design effective test cases **without knowing the internal code structure**.

- **Equivalence Partitioning** groups similar inputs.
- **Boundary Value Analysis** tests at the edges of those groups.
- **State Transition** tests a system’s different states and the transitions between them.
- **Error Guessing** relies on the tester’s experience to predict and test for potential defects.

These techniques help reduce the number of test cases while still keeping strong coverage.

---

<a id="group-c-bva"></a>

## Group C — Boundary Value Analysis (BVA)

### What it is

Boundary Value Analysis (BVA) is a black-box testing technique that focuses on testing the **edges** of input ranges, where defects are most likely to occur.

### How it works

For each input partition or range, test values:

- Just **below** the minimum
- Exactly at the **minimum**
- Just **above** the minimum
- Just **below** the maximum
- Exactly at the **maximum**
- Just **above** the maximum
- Optionally, a **nominal** (middle) value

### Example

For an age field that accepts values from **18 to 65**:

- Below min: `17`
- Min: `18`
- Just above min: `19`
- Just below max: `64`
- Max: `65`
- Above max: `66`

These tests stress the points where validation logic often fails.

---

<a id="group-d-equivalence-partitioning"></a>

## Group D — Black-box techniques — Equivalence Partitioning

### What it is

Equivalence Partitioning is a core black-box testing design technique where the input domain of a software application is divided into groups of data, or **“partitions,”** that are expected to be handled the same way by the system.

This method reduces the number of test cases needed while still providing good coverage, because testing **one representative value** from each partition is considered sufficient to represent the entire group.

### How it works

1. Identify valid and invalid input ranges or categories.
2. Group them into **equivalence partitions** (e.g., valid range, below range, above range).
3. Select **one representative value** from each partition.
4. Design test cases around those representative values.

### Example

For a field that accepts ages from **18 to 65**:

- **Valid partition:** `18–65`
- **Invalid partition 1:** `<18`
- **Invalid partition 2:** `>65`

Representative test values:

- `25` → valid partition
- `10` → invalid (too low)
- `70` → invalid (too high)

---

<a id="group-e-state-transition"></a>

## Group E — Black-box techniques — State Transition

### What it is

State Transition Testing is a black-box technique for systems that have different **states**, where specific events cause the system to transition from one state to another.

### How it works

1. Identify all possible **states** the system can be in.
2. Define **events** or conditions that cause the system to move from one state to another.
3. Create a **state transition diagram** or **state table** to visualize these transitions.
4. Design test cases to cover:
   - Valid transitions (allowed moves).
   - Invalid transitions (moves that should be blocked or handled with errors).

### Example

For a login feature:

- **States:**
  - `Logged Out`
  - `Waiting for Password`
  - `Logged In`
- **Events:**
  - Enter correct password
  - Enter incorrect password

**Transitions:**

- `Waiting for Password` → `Logged In` (correct password)
- `Waiting for Password` → `Waiting for Password` (incorrect password; maybe with an incremented attempt count)
- After too many failures, `Waiting for Password` → `Account Locked` (additional state)

Tests should cover each allowed transition and attempt invalid ones (e.g., trying to log out when already logged out).

---

<a id="group-f-error-guessing"></a>

## Group F — Black-box techniques — Error Guessing

### What it is

Error Guessing is a black-box technique where testers use their **experience, intuition, and knowledge of common mistakes** to guess where defects are likely to be found.

There are no strict rules; it is driven by tester judgment.

### How it works

- Think about:
  - Typical input validation problems.
  - Security or edge-case scenarios.
  - Complex logic or “tricky” areas of the application.
- Design tests specifically targeting:
  - Strange or extreme inputs.
  - Sequences of actions users might do “wrong.”
  - Known past bugs or patterns seen in similar systems.

### Example

In an e-commerce cart, a tester might guess the system could have issues with:

- Updating an item to **zero quantity**.
- Applying a discount to an **already-empty cart**.
- Entering **invalid characters** into a quantity field.
- Rapidly adding/removing the same item many times.

Error guessing fills in gaps that more formal techniques might miss.

---

## References

- (Add books, articles, or videos you used for these notes)
