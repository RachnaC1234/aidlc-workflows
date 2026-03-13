# Refactoring Strategy (CONDITIONAL - Brownfield Refactoring)

**Assume the role** of a software architect specializing in legacy modernization

**Conditional Phase**: Executes only for brownfield refactoring, modernization, or migration requests.

**See [depth-levels.md](../common/depth-levels.md) for adaptive depth explanation**

**Execute IF**: Brownfield project AND user requests refactoring, modernization, or migration of existing codebase

**Skip IF**: Greenfield project OR simple feature addition to brownfield OR bug fix OR enhancement within existing architecture

## Prerequisites
- Workspace Detection must be complete
- Reverse Engineering must be complete (brownfield requirement)
- Requirements Analysis must be complete (confirms refactoring intent)

## Execution Steps

### Step 1: Collect Codebase Metrics

**MANDATORY**: Load reverse engineering artifacts to gather baseline metrics:
- Load `aidlc-docs/inception/reverse-engineering/code-structure.md` for LOC
- Load `aidlc-docs/inception/reverse-engineering/code-quality-assessment.md` for test coverage

Extract and record:
- Total lines of code (LOC)
- Test coverage percentage

These metrics are used to **auto-derive** answers for Q1 (Codebase Size) and Q2 (Test Coverage) in Step 3 — the user is NOT asked these questions.

#### Auto-Derivation Rules

**Q1 - Codebase Size** (from LOC):
- Under 10,000 LOC → A (Small)
- 10,000 to 100,000 LOC → B (Medium)
- Over 100,000 LOC → C (Large)

**Q2 - Test Coverage** (from coverage percentage):
- Over 70% → A (High)
- 30% to 70% → B (Medium)
- Under 30% → C (Low)

**MANDATORY**: Log metrics collection and derived answers in audit.md

---

### Step 2: Present Default Weights

Create `aidlc-docs/inception/refactoring-strategy/strategy-weights.md`:

```markdown
# Refactoring Strategy - Factor Weights

Weights determine how much each factor influences the final recommendation.
**All weights must sum to 1.0 (100%)**

| Factor | Default Weight | Your Weight | Description |
|--------|----------------|-------------|-------------|
| Codebase Size | 0.10 | [    ] | Larger codebases favor Strangler Fig |
| Test Coverage | 0.20 | [    ] | Low coverage increases Big Bang risk |
| Team Availability | 0.10 | [    ] | Busy teams favor incremental approach |
| Business Risk | 0.30 | [    ] | High-risk systems need safer approach |
| Architecture Change | 0.20 | [    ] | Major changes favor incremental migration |
| Timeline | 0.10 | [    ] | Urgent timelines may favor Big Bang |
| **TOTAL** | **1.00** | [    ] | Must equal 1.00 |

**Instructions:**
- Leave "Your Weight" blank to use defaults
- Enter decimal (0.00 - 1.00) to override any weight
- Ensure all weights sum to 1.00
- If weights don't sum to 1.00, they will be normalized automatically
```

Present the weights file to the user and ask if they want to customize. If user is satisfied with defaults, proceed to Step 3.

**MANDATORY**: Log any weight customizations in audit.md

---

### Step 3: Ask Decision Questions

**NOTE**: Q1 (Codebase Size) and Q2 (Test Coverage) are auto-derived from reverse engineering metrics in Step 1. They are included in the questions file for transparency but are pre-filled — the user does NOT need to answer them.

Create `aidlc-docs/inception/refactoring-strategy/strategy-questions.md`:

```markdown
# Refactoring Strategy Assessment

Answer each question to determine the recommended refactoring approach.

## Q1: Codebase Size (AUTO-DERIVED)
What is the approximate size of the codebase being refactored?

A) Small - under 10,000 lines of code
B) Medium - 10,000 to 100,000 lines of code
C) Large - over 100,000 lines of code

[Answer]: [AUTO-DERIVED FROM REVERSE ENGINEERING: X — based on Y LOC]

## Q2: Test Coverage (AUTO-DERIVED)
What is the current test coverage of the codebase?

A) High - over 70% coverage
B) Medium - 30% to 70% coverage
C) Low - under 30% coverage

[Answer]: [AUTO-DERIVED FROM REVERSE ENGINEERING: X — based on Y% coverage]

## Q3: Team Availability
Can feature development be paused during refactoring?

A) Yes - team can focus exclusively on refactoring
B) No - must continue delivering features in parallel
X) Other (please describe after [Answer]: tag below)

[Answer]:

## Q4: Business Risk
How critical is this system to business operations?

A) Low - internal tool, limited impact if issues occur
B) Medium - business application, moderate impact from downtime
C) High - revenue-critical, cannot afford downtime
X) Other (please describe after [Answer]: tag below)

[Answer]:

## Q5: Architecture Change
What level of architectural change is needed?

A) Same architecture - improving code quality within existing structure
B) New architecture - fundamental structural change required
X) Other (please describe after [Answer]: tag below)

[Answer]:

## Q6: Timeline
What is the timeline expectation for the refactoring?

A) Fast - need results quickly, tight deadline
B) Long-term - can invest time for lower risk
X) Other (please describe after [Answer]: tag below)

[Answer]:
```

Present the questions file to the user and STOP. User only needs to answer Q3-Q6.

### ⛔ GATE: Await User Answers
DO NOT proceed to Step 4 until Q3-Q6 in strategy-questions.md are answered and validated.
**MANDATORY**: Analyze ALL answers for contradictions and ambiguities per `common/question-format-guide.md`. Create clarification questions if needed.

---

### Step 4: Calculate Weighted Scores

**PREREQUISITE**: Step 3 gate must be passed — all answers received and validated.

#### 4.1 Base Score Matrix

| Answer | Big Bang Score | Strangler Fig Score |
|--------|----------------|---------------------|
| Q1: A (Small) | +1 | 0 |
| Q1: B (Medium) | 0 | +0.5 |
| Q1: C (Large) | -1 | +1 |
| Q2: A (High coverage) | +1 | 0 |
| Q2: B (Medium coverage) | 0 | +0.5 |
| Q2: C (Low coverage) | -1 | +1 |
| Q3: A (Can pause) | +1 | 0 |
| Q3: B (Must deliver) | -1 | +1 |
| Q4: A (Low risk) | +1 | 0 |
| Q4: B (Medium risk) | 0 | +0.5 |
| Q4: C (High risk) | -1 | +1 |
| Q5: A (Same arch) | +1 | 0 |
| Q5: B (New arch) | -1 | +1 |
| Q6: A (Fast) | +0.5 | -0.5 |
| Q6: B (Long-term) | -0.5 | +1 |

#### 4.2 Weight Application

| Factor | Question | Default Weight |
|--------|----------|----------------|
| Codebase Size | Q1 | 0.10 |
| Test Coverage | Q2 | 0.20 |
| Team Availability | Q3 | 0.10 |
| Business Risk | Q4 | 0.30 |
| Architecture Change | Q5 | 0.20 |
| Timeline | Q6 | 0.10 |
| **TOTAL** | | **1.00** |

Use custom weights from `strategy-weights.md` if provided, otherwise use defaults.

#### 4.3 Calculation

```
Weighted Score = Base Score × Weight
Final Score = Sum of all Weighted Scores
```

#### 4.4 Decision Rule
- Higher final score wins
- If scores are within 0.05 of each other → Default to Strangler Fig (safer approach)

---

### Step 5: Generate Strategy Decision Document

Create `aidlc-docs/inception/refactoring-strategy/strategy-decision.md`:

```markdown
# Refactoring Strategy Decision

## Codebase Metrics (from Reverse Engineering)
- **Total LOC**: [number]
- **Test Coverage**: [percentage]

## Weights Used

| Factor | Weight | Source |
|--------|--------|--------|
| Codebase Size | [0.XX] | [Default/Custom] |
| Test Coverage | [0.XX] | [Default/Custom] |
| Team Availability | [0.XX] | [Default/Custom] |
| Business Risk | [0.XX] | [Default/Custom] |
| Architecture Change | [0.XX] | [Default/Custom] |
| Timeline | [0.XX] | [Default/Custom] |
| **TOTAL** | **1.00** | |

## Assessment Summary

| Factor | Answer | Base BB | Base SF | Weight | Weighted BB | Weighted SF |
|--------|--------|---------|---------|--------|-------------|-------------|
| Codebase Size | [A/B/C] | [±X] | [±X] | [0.XX] | [±X.XX] | [±X.XX] |
| Test Coverage | [A/B/C] | [±X] | [±X] | [0.XX] | [±X.XX] | [±X.XX] |
| Team Availability | [A/B] | [±X] | [±X] | [0.XX] | [±X.XX] | [±X.XX] |
| Business Risk | [A/B/C] | [±X] | [±X] | [0.XX] | [±X.XX] | [±X.XX] |
| Architecture Change | [A/B] | [±X] | [±X] | [0.XX] | [±X.XX] | [±X.XX] |
| Timeline | [A/B] | [±X] | [±X] | [0.XX] | [±X.XX] | [±X.XX] |
| **TOTAL** | | | | **1.00** | **[±X.XX]** | **[±X.XX]** |

## Recommendation
**[Big Bang / Strangler Fig]**

## Rationale
[Explanation based on weighted factors, highlighting the dominant factors that drove the decision]

## Implications for Construction Phase
[Description of how the chosen strategy affects subsequent workflow stages]
```

---

### Step 6: Update State Tracking

Update `aidlc-docs/aidlc-state.md`:

```markdown
## Stage Progress
### 🔵 INCEPTION PHASE
- [x] Workspace Detection
- [x] Reverse Engineering
- [x] Requirements Analysis
- [x] Refactoring Strategy
  - **Decision**: [Big Bang / Strangler Fig]
  - **BB Score**: [±X.XX]
  - **SF Score**: [±X.XX]
```

---

### Step 7: Log and Present Completion Message

**MANDATORY**: Log approval prompt with timestamp in `aidlc-docs/audit.md`

Present completion message:

```markdown
# 🔀 Refactoring Strategy Complete

## Weighted Scores
- **Big Bang**: [±X.XX]
- **Strangler Fig**: [±X.XX]

**Recommended Approach**: [Big Bang / Strangler Fig]

[Brief rationale — 2-3 sentences explaining the key factors]

> **📋 <u>**REVIEW REQUIRED:**</u>**  
> Please examine the strategy documents at: `aidlc-docs/inception/refactoring-strategy/`
> - `strategy-weights.md` — Factor weights used
> - `strategy-questions.md` — Your assessment answers
> - `strategy-decision.md` — Full scoring breakdown and recommendation

> **🚀 <u>**WHAT'S NEXT?**</u>**
>
> **You may:**
>
> 🔧 **Request Changes** - Adjust your answers or customize weights and recalculate
> ✅ **Approve & Continue** - Accept recommendation and proceed to **[User Stories/Workflow Planning]**

---
```

**Note**: Replace [User Stories/Workflow Planning] with the actual next stage name based on workflow determination.

---

### Step 8: Wait for Explicit Approval

- **MANDATORY**: Do not proceed until user explicitly approves
- If user adjusts weights, validate they sum to 1.00 (normalize if not)
- If user changes answers, recalculate scores and regenerate strategy-decision.md
- **MANDATORY**: Log user's response in audit.md with complete raw input

---

## Workflow Behavior Based on Decision

The chosen strategy fundamentally shapes the CONSTRUCTION phase:

### If Big Bang Selected
- Workflow Planning creates a single comprehensive refactoring plan
- All code changes generated in one construction pass (single unit or tightly coupled units)
- Single build and test cycle covering the entire refactoring
- Higher risk but faster completion

### If Strangler Fig Selected
- Workflow Planning defines migration chunks/boundaries as separate units
- Units Generation decomposes the migration into incremental chunks
- Each chunk goes through its own construction cycle with approval gates
- Iterative build and test per chunk
- Lower risk with incremental validation
