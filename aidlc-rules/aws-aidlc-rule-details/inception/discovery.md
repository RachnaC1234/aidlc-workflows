# Discovery (Greenfield Only)

**Assume the role** of a product strategist and customer researcher

**Conditional Phase**: Executes only for Greenfield projects as the first analytical step in Inception, before Requirements Analysis.

**Purpose**: Gather and understand customer pain points, then produce a PR/FAQ document that serves as the foundation for Requirements Analysis.

## Prerequisites
- Workspace Detection must be complete
- Project must be identified as Greenfield

## Pain Point Gathering Modes

Discovery supports two mutually exclusive modes for gathering customer pain points:

### Mode 1: Interactive Discovery (Default)
The AI asks structured questions to understand the customer's pain points, target audience, and the problem space the application must address.

### Mode 2: URL-Based Discovery
The user provides a URL containing information about the pain points the application must address. The AI reads **only that URL** and extracts pain points from it.

**CRITICAL**: If the user provides a URL, use **only** that URL. Do NOT fetch, reference, or use any other URLs. All pain point understanding must come exclusively from the user-provided URL.

## Execution Steps

### Step 1: Determine Discovery Mode

Ask the user how they want to provide pain point information:

Create `aidlc-docs/inception/discovery/discovery-mode-questions.md`:

```markdown
# Discovery Mode Selection

## Question 1
How would you like to provide information about the customer pain points this application should address?

A) I will answer questions interactively — ask me about the pain points
B) I have a URL that describes the pain points — I will provide it
X) Other (please describe after [Answer]: tag below)

[Answer]: 
```

### ⛔ GATE: Await User Answer
DO NOT proceed until the user answers the mode selection question.

### Step 2: Gather Pain Points

#### Step 2A: Interactive Discovery (if Mode A selected)

Create `aidlc-docs/inception/discovery/discovery-questions.md` with questions covering:

**MANDATORY question areas:**
- Who is the target customer? Define the specific customer segment.
- What problem(s) does the target customer face today?
- How does the customer currently solve or work around this problem?
- What is the impact of this problem on the customer (time, cost, frustration)?
- What would an ideal solution look like from the customer's perspective?
- How many customers have this problem? Is the problem big enough that customers would pay to solve it?
- Are there existing products or competitors addressing this problem? How do they fall short?
- What would make the customer switch from their current solution to a new one?

Use the standard AIDLC question format (multiple choice with [Answer]: tags, mandatory "Other" option).

**MANDATORY**: Analyze ALL answers for ambiguities and create follow-up questions if needed. Keep asking until all ambiguities are resolved OR user explicitly asks to proceed.

#### Step 2B: URL-Based Discovery (if Mode B selected)

1. Ask the user to provide the URL
2. Fetch and read **only** the provided URL
3. Extract and summarize the pain points found
4. Create `aidlc-docs/inception/discovery/pain-points-from-url.md` documenting:
   - Source URL
   - Extracted pain points (numbered list)
   - Target customer segment (as understood from the URL)
   - Current solutions/workarounds mentioned
   - Gaps or unmet needs identified
5. Present the extracted pain points to the user for confirmation
6. If information is insufficient for PRFAQ creation, ask clarifying questions using the standard AIDLC question format

### ⛔ GATE: Await Pain Point Confirmation
DO NOT proceed to PRFAQ creation until the user confirms the pain points are accurate and complete.

### Step 3: Create PR/FAQ Document

Using the confirmed pain points, create `aidlc-docs/inception/discovery/prfaq.md` following the Working Backwards PR/FAQ format exactly.


**CRITICAL**: Use the PR/FAQ format exactly as defined below. Do NOT deviate from this structure.

#### PR/FAQ Document Structure

```markdown
# PR/FAQ: [Product Name]

---

## Press Release

### Heading
[Product name so the target customer will understand — one sentence under the title]

### Subheading
[Describe the customer for the product and what benefits they will gain — one sentence]

### Summary Paragraph
[City, media outlet, proposed launch date]. [Summary of the product and its benefits.]

### Problem Paragraph
[Describe the problem(s) the product solves from the customer's point of view. Identify the problem with a large total addressable market. The market size is the number of customers who have this problem multiplied by how much each is willing to pay to solve it.]

### Solution Paragraph(s)
[Describe the product in detail and how it simply and easily solves the customer's problem. Address how the product is meaningfully differentiated from existing solutions. Include: "Today, customers with this problem use x, y, or z products to meet their needs. Those products fall short of solving x problem(s). Our product addresses these unmet needs in the following ways."]

### Quotes
**Company Spokesperson Quote:**
> "[Quote from company spokesperson about the product]"

**Customer Quote:**
> "[Quote from a hypothetical customer describing the benefit of using the product]"

### Getting Started
[Describe how easy it is to get started and where customers can get more information.]

---

## External FAQs (Customer-Facing)

### Q: What is the price?
A: [Answer]

### Q: How does it work?
A: [Answer]

### Q: How do I get help/customer support?
A: [Answer]

### Q: Where can I buy/access it?
A: [Answer]

[Add additional external FAQs relevant to the specific product]

---

## Internal FAQs (Business & Technical)

### Q: What products or solutions does the target customer use today to solve this problem?
A: [Answer]

### Q: What problem(s) does this product solve for customers?
A: [Answer]

### Q: How does this proposed product solution create value for customers? In what way(s) is this product better, cheaper, and faster than the alternatives?
A: [Answer]

### Q: What/who are the current competitors for this product?
A: [Answer]

### Q: How large is the estimated consumer demand, and what is the TAM (total addressable market)?
A: [Answer]

### Q: How many consumers have this need or problem?
A: [Answer]

### Q: For how many consumers is this problem big enough that they are willing to spend money to do something about it? If so, how much money would they be willing to spend?
A: [Answer]

### Q: How many of these consumers have the characteristics/capabilities/constraints necessary to use the product?
A: [Answer]

### Q: What happens if a customer encounters [edge case]? How does the product deal with [use case]?
A: [Answer]

### Q: What are the challenging problems (business model, engineering, legal, UI, etc.) that will need to be solved to enable this new product?
A: [Answer]

### Q: What new capabilities will we need to establish to support this product?
A: [Answer]

### Q: Do we have any third-party business relationships or dependencies to build this product?
A: [Answer]

### Q: What third-party technologies are we dependent on for this product to work as promised?
A: [Answer]

### Q: Are there any potential regulatory or legal issues to consider?
A: [Answer]

### Q: What are the per-unit economics of the product? What is the expected Gross Profit and Contribution profit per unit?
A: [Answer]

### Q: How much will we need to invest upfront to build this product (people, technology, inventory, etc.)?
A: [Answer]

### Q: How will we manage the risk of the upfront investment required?
A: [Answer]

### Q: Based on the upfront investment and per-unit economics, how many months/years before we achieve profitability?
A: [Answer]

### Q: What assumptions need to be true for this product to be successful?
A: [Answer]

### Q: What are the top three reasons this product will not succeed?
A: [Answer]

[Add additional internal FAQs relevant to the specific product]
```

#### PRFAQ Clarifying Questions

If information gathered from pain points (interactive or URL-based) is insufficient to complete any section of the PRFAQ, create `aidlc-docs/inception/discovery/prfaq-clarifying-questions.md` using the standard AIDLC question format.

**MANDATORY**: Ask clarifying questions for ANY PRFAQ section where information is missing or ambiguous. Do not guess or fabricate answers.

### ⛔ GATE: Await PRFAQ Clarifying Question Answers
If clarifying questions were created, DO NOT finalize the PRFAQ until all answers are received and validated.

### Step 4: Present PRFAQ for Review

Present the completed PRFAQ to the user with the following message:

```markdown
# 🔍 Discovery Phase Complete

**Pain Point Gathering**: [Interactive / URL-Based]
**Pain Points Identified**: [Count]
**PRFAQ Document**: `aidlc-docs/inception/discovery/prfaq.md`

## Summary
[Brief summary of the key pain points and proposed product vision]

## Artifacts Created
- `aidlc-docs/inception/discovery/prfaq.md` — PR/FAQ document
- `aidlc-docs/inception/discovery/discovery-mode-questions.md` — Mode selection
- [Additional artifacts based on mode used]

## Next Step
The PRFAQ will be used as input to **Requirements Analysis**, providing context for gathering detailed functional and non-functional requirements.

**Please review the PRFAQ document and confirm to proceed to Requirements Analysis.**
```

### ⛔ GATE: Await User Approval
DO NOT proceed to Requirements Analysis until the user explicitly approves the PRFAQ.

### Step 5: Update State Tracking

Update `aidlc-docs/aidlc-state.md`:

```markdown
## Stage Progress
### 🔵 INCEPTION PHASE
- [x] Workspace Detection
- [x] Discovery
```

### Step 6: Log and Proceed

- Log completion in `aidlc-docs/audit.md`
- Proceed to Requirements Analysis with PRFAQ as input context
