# AI-PLC Welcome Message

**Purpose**: This file contains the user-facing welcome message that should be displayed ONCE at the start of any AI-PLC workflow.

---

# Welcome to AI-PLC Discovery Phase

I'll guide you through the Discovery phase — a Product Manager-focused workflow for defining and validating AI product ideas before development begins.

## What is PDLC?

PDLC (Product Development Life Cycle) is the step that comes before building software. It uses AI-assisted technology to complete a Discovery phase — helping you figure out what to build before writing any code.

```
PDLC (Product Discovery)  →  DLC (Development)
Figure out WHAT               Build it
```

## The Three Scenarios

The Discovery phase supports three scenarios, each building on the previous one:

| Scenario | You start with... | You get... |
|---|---|---|
| A. Customer pain points | Customer feedback, reviews, or complaints | A PR/FAQ and prototype specs |
| B. Use case prioritization | A list of AI ideas (3, 5, 10, or more) | A ranked list and prototype specs for the top ideas |
| C. Build prototypes | Prototype spec files from scenario A or B | Working prototype code |

In all three cases, the final output is a set of prototype specifications (PROTOTYPE-*.md files) and optionally working prototypes — ready to explore the art of the possible.

### Scenario A: Starting from Customer Pain Points

**When to use**: You have customer feedback, reviews, or complaints and want to discover AI solutions.

**What happens**:
1. Gather and confirm customer pain points (from URLs or interactively)
2. Generate a PR/FAQ using the Working Backwards method
3. Solution Analysis identifies one or more solutions
4. Generate PROTOTYPE-*.md specification files
5. Optionally build prototypes
6. Define Product Strategy and Go-to-Market

**Example prompt**: `I want to start AI-PLC Discovery from customer pain points`

---

### Scenario B: Prioritizing a List of Use Cases

**When to use**: You have multiple AI ideas (3, 5, 10, 20+) and need to decide which ones to pursue.

**What happens**:
1. Provide details for all your use cases
2. Categorize them (Agentic vs Application)
3. Prioritize using scoring frameworks (business value, risk, cost, strategic alignment)
4. Select top 3 for prototyping
5. Generate PROTOTYPE-*.md specification files
6. Optionally build prototypes
7. Define Product Strategy and Go-to-Market

**Example prompt**: `I have 10 use cases that need prioritization using AI-PLC`

---

### Scenario C: Building from Existing Prototype Specs

**When to use**: You already have PROTOTYPE-*.md files (from Scenario A, Scenario B, or a workshop).

**What happens**:
1. Workspace Detection finds your PROTOTYPE-*.md files
2. Skips all discovery phases
3. Builds prototypes directly from the specifications
4. You validate and iterate
5. Define Product Strategy and Go-to-Market

**Example prompt**: `I want to build prototypes from existing PROTOTYPE files using AI-PLC`

---

## Workflow Overview

```
Your Request
      |
      v
Workspace Detection
      |
      v
  +-------+
  |       |
  v       v
Scenario  Scenarios
   C       A & B
  |       |
  +---+---+
      |
      v
Prototype Building (Optional)
      |
      v
Product Strategy
      |
      v
Go-to-Market
      |
      v
Discovery Document Complete
```

## What You'll Get

The Discovery phase produces:
- A comprehensive **Discovery Document** (`discovery-document.md`)
- **PROTOTYPE-*.md** specification files (portable, shareable)
- **Product Strategy** and **Go-to-Market** plans
- A complete **audit trail** of all decisions

## What Happens After Discovery?

The prototype spec files can be used right away in Scenario C to build a working prototype — great for demos, validation, and getting early feedback.

However, prototypes are not production-ready. To prepare for a production environment, we recommend following the DLC (Development Lifecycle) process, where Product Managers and developers collaborate to:

1. Analyze requirements and plan the architecture
2. Generate production-quality code
3. Build, test, and deploy

## Key Principles

- **PM-Focused**: This workspace is for Product Managers — no coding required
- **Three Scenarios**: Flexible starting points based on your situation
- **Scalable**: Supports any number of use cases (3, 5, 10, 20+)
- **Workshop-Friendly**: PROTOTYPE-*.md files are portable and shareable
- **Transparent**: Always shows defaults, asks for your input
- **Documented**: Complete audit trail of all decisions
- **Handoff-Ready**: Produces comprehensive Discovery Document for developers

## What Happens Next

1. I'll check your workspace for existing PROTOTYPE-*.md files
   - If found: We'll build prototypes directly (Scenario C)
   - If not found: I'll ask how you want to start (Scenario A or B)
2. We'll work through the Discovery stages together
3. You review and approve each stage before moving forward
4. You'll get a complete Discovery Document ready for handoff

> **Tip**: If I start asking questions directly in chat instead of creating a file, say:
> `Please create a question file (.md) with [Answer]: tags instead of asking in chat`

Let's begin!
