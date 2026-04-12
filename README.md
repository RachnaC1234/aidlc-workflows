# AI-PLC Discovery Workspace

A Product Manager-focused workspace for defining and validating AI product ideas using the AI Product Lifecycle (AI-PLC) Discovery Phase.

## What is This?

This workspace helps Product Managers complete the Discovery phase of AI-PLC - the critical first step where you define **WHO** your customer is, **WHAT** problem you're solving, and **WHY** it matters, before any technical development begins.

## Who Should Use This?

- **Product Managers** leading AI product initiatives
- **Product Teams** evaluating multiple use cases
- **Workshop Facilitators** running AI product discovery sessions
- **Innovation Teams** exploring AI opportunities

## What You'll Get

### Main Output
A comprehensive **Discovery Document** containing:
- Customer pain points and insights
- PR/FAQ using Amazon's Working Backwards method
- Use case analysis and prioritization
- PROTOTYPE-*.md specifications (portable, shareable)
- Product strategy and positioning
- Go-to-market plan

### Ready for Handoff
Everything developers need to start building in their own workspace:
- Clear product vision and requirements
- Validated use cases
- Prototype specifications
- Strategic context

## Three Ways to Start

### Entry Point 1: Existing Prototype Specs
**You have**: PROTOTYPE-*.md files from a workshop or previous session  
**What happens**: Build prototypes immediately, skip discovery phases  
**Best for**: Workshop teams with pre-generated specifications

### Entry Point 2: Customer Pain Points
**You have**: Customer feedback, reviews, or pain points  
**What happens**: Create PR/FAQ → Analyze solutions → Build prototypes  
**Best for**: Starting from customer insights

### Entry Point 3: Multiple Use Cases
**You have**: 3, 5, 10, or 20+ use case ideas to evaluate  
**What happens**: Prioritize → Select top 3 → Generate specs → Build prototypes  
**Best for**: Teams with many ideas needing prioritization

## Quick Start

### Prerequisites
- Kiro IDE installed
- Basic understanding of your product domain
- Customer insights or use case ideas (optional)

### Getting Started

1. **Clone this repository**
   ```bash
   git clone <repository-url>
   cd ai-plc-discovery-workspace
   ```

2. **Open in Kiro IDE**
   ```bash
   kiro .
   ```

3. **Start the workflow**
   - The AI will automatically detect your workspace
   - Check for existing PROTOTYPE-*.md files
   - Guide you through the appropriate entry point

4. **Follow the guided process**
   - Answer questions using [Answer]: format
   - Review and approve each stage
   - Make product decisions on strategy and positioning

## Workflow Overview

```
Product Manager Request
         ↓
Workspace Detection
         ↓
Check for PROTOTYPE-*.md files?
         ↓
    ┌────┴────┐
    ↓         ↓
Entry Point 1  Entry Points 2 & 3
Existing Files Pain Points or Use Cases
    ↓              ↓
    └──────┬───────┘
           ↓
   Prototype Building (Optional)
           ↓
   Product Strategy
           ↓
   Go-to-Market
           ↓
   Discovery Document Complete
```

## Key Features

- **PM-Focused**: No coding required - focuses on product vision
- **Three Entry Points**: Flexible starting points based on your situation
- **Scalable**: Supports any number of use cases (3, 5, 10, 20+)
- **Workshop-Friendly**: PROTOTYPE-*.md files are portable and shareable
- **Transparent**: Always shows defaults, asks for your input
- **Documented**: Complete audit trail of all decisions
- **Handoff-Ready**: Produces comprehensive Discovery Document for developers

## What Happens After Discovery?

Developers receive your Discovery Document in a **separate workspace** where they:
1. **Inception Phase**: Requirements analysis, workflow planning, application design
2. **Construction Phase**: Code generation, build, and test
3. **Operations Phase**: Deployment and monitoring

## Example Use Cases

### Workshop Scenario
- Facilitator generates 5 PROTOTYPE-*.md files
- Distributes to 5 teams
- Each team opens workspace, builds their prototype
- Teams present and compare results

### Startup Scenario
- PM has 10 potential AI agent ideas
- Uses Entry Point 3 to prioritize
- Selects top 3 for prototyping
- Generates PROTOTYPE-*.md files
- Hands off to engineering team

### Customer-Driven Scenario
- PM collects customer reviews from Trustpilot
- Uses Entry Point 2 with URL
- Creates PR/FAQ
- Builds and validates prototype
- Defines strategy and GTM

## Directory Structure

```
ai-plc-discovery-workspace/
├── README.md                          # This file
├── .kiro/
│   ├── aws-aiplc-rule-details/       # Workflow rules
│   │   ├── common/                   # Common guidelines
│   │   ├── discovery/                # Discovery phase rules
│   │   └── inception/                # Workspace detection only
│   └── steering/
│       └── aws-aiplc-rules/          # Core workflow
└── aiplc-docs/                       # Generated during workflow
    ├── discovery/
    │   ├── discovery-document.md     # Main output ★
    │   ├── envision/                 # Pain points & PR/FAQ
    │   ├── use-case-intake/          # Use case details
    │   ├── prioritization/           # Scoring & ranking
    │   ├── prototypes/               # PROTOTYPE-*.md files ★
    │   ├── product-strategy/         # Strategy docs
    │   └── go-to-market/             # GTM plans
    ├── aiplc-state.md               # Session state
    └── audit.md                      # Complete audit trail
```

## Support

For questions, issues, or contributions:
- Open an issue in this repository
- Refer to the documentation in `.kiro/aws-aiplc-rule-details/`
- Check the welcome message for detailed workflow guidance

## License

[Add your license here]

## Contributing

[Add contribution guidelines here]

---

**Ready to start?** Open this workspace in Kiro IDE and let the AI guide you through your Discovery journey!
