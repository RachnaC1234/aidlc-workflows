# AI-PLC: AI-Assisted Product Lifecycle — Discovery Workspace

## What is PDLC?

PDLC (Product Development Life Cycle) is the step that comes before building software. It uses AI-assisted technology to complete a Discovery phase — helping you figure out what to build before writing any code.

Think of it this way:

```
PDLC (Product Discovery)  →  DLC (Development)
Figure out WHAT               Build it
```

The Discovery phase supports three scenarios:

| Scenario | You start with... | You get... |
|---|---|---|
| A. Customer pain points | Customer feedback, reviews, or complaints | A PR/FAQ and prototype specs |
| B. Use case prioritization | A list of AI ideas (3, 5, 10, or more) | A ranked list and prototype specs for the top ideas |
| C. Build prototypes | Prototype spec files from scenario A or B | Working prototype code |

In all three cases, the final output is a set of prototype specifications (PROTOTYPE-*.md files) and optionally working prototypes — that will explore the art of the possible.

---

## Getting Started — Step by Step

Follow these steps in order. You will need about 15 minutes.

### Step 1: Install Kiro IDE

Kiro is the AI-powered IDE that runs the Discovery workflow.

1. Go to [kiro.dev](https://kiro.dev/) and download the installer for your operating system
2. Run the installer and follow the prompts
3. Sign in with a personal identity provider (Gmail, GitHub, etc.)
4. When prompted to select a folder, create a new empty folder — this will be your workspace (you can change it later)

### Step 2: Install Git

Git is needed to download the workflow files.

First, check if Git is already installed. Open a terminal and run:

```
git --version
```

If you see a version number, skip to Step 3.

If not, install Git:

**Windows:**
1. Open Command Prompt or PowerShell
2. Run: `winget install Git.Git`
3. Close and reopen the terminal
4. Verify: `git --version`

**macOS:**
1. Open Terminal and run: `git --version`
2. macOS will prompt you to install it — click Install
3. Verify: `git --version`

### Step 3: Clone the Workflow Repository

1. Open a terminal and navigate to the folder where you want to work
2. Run:
   ```
   git clone -b ai-plc-prioritize-prototype-agents https://github.com/mauriciofm/aidlc-workflows.git
   ```
3. Enter the new folder:
   ```
   cd aidlc-workflows
   ```

### Step 4: Open the Project in Kiro

1. In Kiro, go to **File → Open Folder**
2. Select the `aidlc-workflows` folder you just cloned

### Step 5: Verify You Are Signed In

1. Click the user icon in the lower-left corner of the Kiro window
2. Confirm your account is active

### Step 6: Open the Chat Interface

1. Click the chat icon (the speech bubble in the sidebar)
2. Kiro will ask you to choose between **Vibe** and **Spec** mode — always select **Vibe**
3. Test it by asking Kiro any question — for example: `Hello, what can you do?`

> **Important**: Always choose **Vibe** mode, not Spec. The AI-PLC workflow is designed to run in Vibe mode.

### Step 7: Start the Discovery Workflow

Send a prompt to Kiro based on your scenario. Always mention "AI-PLC" so Kiro activates the correct workflow.

**Scenario A — Starting from customer pain points:**
```
I want to start AI-PLC Discovery from customer pain points
```

**Scenario B — Prioritizing a list of use cases:**
```
I have 10 use cases that need prioritization using AI-PLC
```

**Scenario C — Building from existing prototype specs:**
```
I want to build prototypes from existing PROTOTYPE files using AI-PLC
```

From here, Kiro will guide you through each stage. Answer the questions it presents, review each stage, and approve before moving forward.

> **Tip**: If Kiro starts asking questions directly in chat instead of creating a file, say:
> `Please create a question file (.md) with [Answer]: tags instead of asking in chat`

---

## What Happens After Discovery?

The Discovery phase produces prototype specification files (PROTOTYPE-*.md). You can use these files right away in Scenario C to build a working prototype — great for demos, validation, and getting early feedback.

However, prototypes are not production-ready. To prepare for a production environment, we recommend following the DLC (Development Lifecycle) process, where Product Managers and developers collaborate to:

1. Analyze requirements and plan the architecture
2. Generate production-quality code
3. Build, test, and deploy

---

## Appendix

### System Requirements

- Internet connection (required for downloads and API access)
- Permissions to install software on your machine
- For AI agent prototypes: LLM API keys (e.g., AWS Bedrock, OpenAI, Anthropic)

### Workflow Diagram

```
Your Request
      ↓
Workspace Detection
      ↓
  ┌───┴───┐
  ↓       ↓
Scenario  Scenarios
   C       A & B
  ↓       ↓
  └───┬───┘
      ↓
Prototype Building
      ↓
Product Strategy
      ↓
Go-to-Market
      ↓
Discovery Document Complete
```

### Directory Structure

```
aidlc-workflows/
├── README.md                          # This file
├── .kiro/
│   ├── aws-aiplc-rule-details/       # Workflow rules
│   └── steering/                     # Core workflow steering files
└── aiplc-docs/                       # Generated during the workflow
    ├── discovery/
    │   ├── discovery-document.md     # Final output
    │   ├── prototypes/               # PROTOTYPE-*.md files
    │   ├── prioritization/           # Scoring and ranking
    │   ├── product-strategy/         # Strategy docs
    │   └── go-to-market/             # GTM plans
    ├── aiplc-state.md               # Session progress
    └── audit.md                      # Audit trail
```

### Additional Resources

- [Kiro IDE documentation](https://kiro.dev/docs/)
- [Git installation guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
