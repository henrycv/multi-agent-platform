# Human Leading Multi-Agents Team

The project is designed for software developers or enthusiasts who want to build  products that inspire them 🚀.

It pretends serve as an environment of AI Agents with different skills and responsibilities collaborating under human leadership for design, development, and validation of IT products around a **Human Founder**. It operates less like an AI coding assistant and more like a **small, coordinated technology organization** in which specialized AI agents collaborate under human leadership.

The central idea is simple:

> **AI agents provide specialized expertise and execution; the Human Founder retains ownership of vision, priorities, and consequential decisions.**

---

## Why this approach?

Software projects involve many different types of work. Product discovery, UX design, frontend development, backend development, infrastructure, testing, security, and documentation require different knowledge and tools.

Giving all these responsibilities to one general-purpose AI agent can make the system difficult to control, understand, and maintain.

---

## How It Works

The organization is centered around the Human Founder, supported by a group of specialized AI roles.

```text
                         ┌─────────────────────┐
                         │ 👤 HUMAN FOUNDER    │
                         │                     │
                         │ Ideas               │
                         │ Vision              │
                         │ Goals               │
                         │ Constraints         │
                         │ Final Decisions     │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    🤝 PARTNER       │
                         │     AI AGENT        │
                         │                     │
                         │ Product             │
                         │ Strategy            │
                         │ Business            │
                         │ CTO Advisory        │
                         │ Decision Support    │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    🏗️ ARCHITECT     │
                         │     AI AGENT        │
                         │                     │
                         │ System Design       │
                         │ Technology Stack    │
                         │ APIs & Services     │
                         │ Data Architecture   │
                         │ Security            │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │   🎯 ORCHESTRATOR   │
                         │     AI AGENT        │
                         │                     │
                         │ Plans Work          │
                         │ Delegates Tasks     │
                         │ Manages Dependencies│
                         │ Coordinates Agents  │
                         │ Tracks State        │
                         └──────────┬──────────┘
                                    │
          ┌─────────────┬───────────┼───────────┬─────────────┐
          ▼             ▼           ▼           ▼             ▼
       ┌───────┐   ┌──────────┐ ┌────────┐ ┌─────────┐   ┌─────────┐
       │ UX/UI │   │ Frontend │ │Backend │ │  Data   │   │   SRE   │
       │ Agent │   │  Agent   │ │ Agents │ │  Agent  │   │  Agent  │
       └───────┘   └──────────┘ └────────┘ └─────────┘   └─────────┘
                                    │
                                    ▼
                              ┌────────────┐
                              │  🔎 QA     │
                              │  AI AGENT  │
                              │            │
                              │ Tests      │
                              │ Browser    │
                              │ Validation │
                              └────────────┘
```

The hierarchy represents **responsibility and decision flow**. It does not mean that every interaction has to pass through every agent.

---

# What We Are Building

A founder can bring something as simple as:

> "I have an idea for a product that helps companies manage X."

The system should be able to help turn that idea into something concrete:

```text
Human Idea
    │
    ▼
Product Discovery
    │
    ▼
Requirements & Validation
    │
    ▼
Technical Architecture
    │
    ▼
Implementation Plan
    │
    ▼
Software Development
    │
    ▼
Testing & Verification
    │
    ▼
Product Increment
    │
    ▼
Human Acceptance
```

The agents can research, ask questions, challenge assumptions, design systems, write software, run tests, and review the results.

The founder remains involved where it matters.

---

# Core Principles

### Human in the Loop

AI should make the founder more effective, not remove the founder from the process.

The Human Founder remains responsible for:

* Product vision and business goals.
* Strategic priorities.
* Major scope changes.
* Significant technology and architecture decisions.
* Business model decisions.
* Security-sensitive decisions.
* Production-impacting actions.
* Irreversible or high-risk operations.
* Final acceptance of important product increments.

### Clear Responsibilities

Each agent should have a well-defined job.

An agent should not become a general-purpose "do everything" agent simply because it can.

Every role should have clear:

* Responsibilities.
* Inputs.
* Outputs.
* Authority.
* Dependencies.
* Escalation rules.

This is important both technically and organizationally. It makes the system easier to understand, test, maintain, and eventually scale.

### Shared Project Knowledge

Agents should not rely on whatever happens to be in their current conversation.

Important project knowledge belongs in the **Project Brain**.

### Evidence Before Big Decisions

For significant decisions, agents should provide useful evidence where possible:

* Research.
* Technical analysis.
* Experiments.
* Prototypes.
* Tests.
* Risk assessments.
* Cost or operational considerations.

### Autonomy With Guardrails

Agents should be free to perform low-risk, reversible work without asking for permission at every step.

Higher-risk actions should require explicit approval.

The objective is **controlled autonomy**, not blind autonomy.

---

# The Main Roles

## 👤 Human Founder

The founder provides the context that AI cannot reliably invent:

* Vision.
* Business goals.
* Constraints.
* Priorities.
* Risk tolerance.
* Final decisions.

The founder should not have to personally manage every technical detail or coordinate every engineering task.

---

## 🤝 Agent Partner

The Agent Partner is the founder's primary AI counterpart.

Think of it as a combination of:

* Product partner.
* Business analyst.
* Product manager.
* CTO advisor.
* Strategic advisor.

It should:

* Understand the founder's intent.
* Ask useful questions.
* Identify assumptions.
* Challenge weak ideas.
* Research unknowns.
* Explore alternatives.
* Help define requirements.
* Identify product and business risks.
* Prepare important decisions for the founder.

It should **not** take over the Architect's or Orchestrator's responsibilities.

---

## 🏗️ Architect Agent

The Architect owns the technical design.

It is responsible for:

* System architecture.
* Technology choices.
* Service boundaries.
* APIs and integrations.
* Data architecture.
* Security architecture.
* Technical constraints.
* Architecture risks.
* Architecture Decision Records (ADRs).

The Architect should define **how the system should be built**, rather than becoming the team's main implementation agent.

---

## 🎯 Orchestrator Agent

The Orchestrator turns approved plans into coordinated work.

It handles:

* Breaking work into tasks.
* Managing dependencies.
* Assigning tasks to specialist agents.
* Tracking progress.
* Handling blockers.
* Coordinating handoffs.
* Detecting conflicts.
* Escalating decisions when necessary.

The Orchestrator is the team's **delivery coordinator**, not another developer competing with the specialist agents.

---

# Specialist Agents

The organization can include as many specialist roles as the project actually needs.

| Agent       | Responsibility                                            |
| ----------- | --------------------------------------------------------- |
| UX/UI       | User experience, interaction and visual design            |
| Frontend    | Client-side application development                       |
| Backend JS  | JavaScript/TypeScript backend development                 |
| Backend PHP | PHP backend development                                   |
| Data        | Data models, pipelines, analytics and data quality        |
| SRE         | Infrastructure, deployment, reliability and observability |
| Security    | Security analysis, controls and review                    |
| QA          | Functional, technical and end-to-end validation           |
| Research    | Market, technical and domain research                     |

More roles can be introduced later when there is a real need for them.

---

# Human Approval and Autonomy

Not every action needs a meeting with the founder.

### Agents can normally work autonomously on:

* Research.
* Documentation.
* Prototypes.
* Code generation.
* Refactoring.
* Unit tests.
* Static analysis.
* Local experiments.
* Test execution.
* Other reversible engineering tasks.

### Founder approval should normally be required for:

* Major product direction changes.
* Significant scope changes.
* Business model decisions.
* Major technology choices.
* Major architecture changes.
* Security-sensitive decisions.
* Production-impacting actions.
* Irreversible operations.
* Significant financial or business risk.

A useful rule is:

> **The more expensive, risky, irreversible, or strategic the decision, the stronger the human approval requirement should be.**

---

# Project Brain

The **Project Brain** is the shared memory of the organization.

It keeps agents aligned on what the team is actually building and why.

```text
                    📚 PROJECT BRAIN
                         │
       ┌─────────────────┼─────────────────┐
       ▼                 ▼                 ▼
   Product              Tech              Business
   Vision               Architecture      Market
   Personas             ADRs              Pricing
   Requirements         APIs              Competitors
   Roadmap              Data model        Metrics
   Constraints          Security          Decisions
```

It should contain important project artifacts such as:

* Product vision.
* Personas.
* Requirements.
* Roadmap.
* Market and competitor research.
* Architecture.
* ADRs.
* APIs and data models.
* Security requirements.
* Development standards.
* Backlog and milestones.
* Important decisions.
* Open questions.
* Risks and constraints.
* Agent responsibilities.

The Project Brain should become the **shared source of organizational context** for every agent.

---

# From Idea to Product

A typical workflow looks like this:

```text
Human Founder
      │
      │ "I have an idea..."
      ▼
Agent Partner
      │
      ├── Understands the problem
      ├── Asks questions
      ├── Identifies assumptions
      ├── Researches unknowns
      ├── Challenges weak points
      └── Defines desired outcomes
      │
      ▼
Human Founder
      │
      │ Approval / decision
      ▼
Agent Partner
      │
      │ Product requirements
      ▼
Architect
      │
      ├── Designs system
      ├── Evaluates technology
      ├── Defines services and APIs
      ├── Designs data architecture
      └── Documents technical decisions
      │
      ▼
Human Founder
      │
      │ Architecture approval
      ▼
Orchestrator
      │
      ├── Breaks work into tasks
      ├── Determines dependencies
      ├── Delegates work
      └── Coordinates execution
      │
      ▼
Specialist Agents
      │
      ├── UX/UI
      ├── Frontend
      ├── Backend
      ├── Data
      ├── SRE
      └── Other specialists
      │
      ▼
QA / Review
      │
      ├── Automated tests
      ├── Browser / E2E tests
      ├── Code review
      ├── Security checks
      └── Requirement validation
      │
      ▼
Human Founder
      │
      │ Acceptance / next decision
      ▼
Product Increment
```

---

# Quality and Verification

Writing code is only part of delivering a product.

The organization should verify both:

1. **Does the software work correctly?**
2. **Does it solve the problem we intended to solve?**

Verification can include:

* Unit tests.
* Integration tests.
* End-to-end tests.
* Browser testing.
* API testing.
* Static analysis.
* Security checks.
* Performance testing.
* Requirement validation.
* Code review.
* Human acceptance.

---

# Security and Risk

Security should be considered throughout the lifecycle, not added at the end.

It should be part of:

* Architecture.
* Data design.
* Authentication and authorization.
* Application development.
* Infrastructure.
* Dependencies.
* Deployment.
* Monitoring.
* Incident response.

Agents should never independently perform potentially damaging production or security operations outside their defined authority.

---

# Agent Handoffs

Agents should communicate primarily through:

* tasks
* artifacts
* structured reports
* project documentation
* code changes
* test results
* design specifications
* infrastructure state

rather than by passing large natural-language conversations around.

Example:

```text
Partner
   ↓
Requirement
   ↓
Architect
   ↓
Orchestrator
   ↓
Technical tasks
   ├── UX task
   ├── Frontend task
   ├── Backend task
   └── SRE task
         ↓
       QA
         ↓
     Verification
         ↓
     Orchestrator
         ↓
      Partner
         ↓
      Human Founder
```

The handoffs between agents should be **clear and structured**, rather than assuming that another agent knows what happened earlier:

* What needs to be done.
* Why it matters.
* Relevant context.
* Constraints.
* Expected output.
* Dependencies.
* Acceptance criteria.

This keeps the organization predictable and makes failures easier to diagnose.

---

# Decision Governance

Not every decision deserves the same level of process.

### Routine decisions

Agents can normally make these themselves.

Examples:

* Refactoring an internal implementation.
* Adding tests.
* Improving documentation.
* Choosing implementation details.
* Running a local experiment.

### Significant decisions

These should be reviewed and escalated appropriately.

Examples:

* Changing the database technology.
* Changing a public API.
* Introducing a significant external dependency.
* Changing authentication architecture.
* Increasing infrastructure costs substantially.
* Changing product scope.
* Making a potentially disruptive production change.

Important decisions should be recorded so that the organization remembers **what was decided and why**.

---

# Suggested Repository Structure

```text
.
├── README.md
├── docs/
│   ├── product/
│   ├── architecture/
│   ├── decisions/
│   ├── security/
│   └── operations/
│
├── agents/
│   ├── partner/
│   ├── architect/
│   ├── orchestrator/
│   ├── ux/
│   ├── frontend/
│   ├── backend-js/
│   ├── backend-php/
│   ├── data/
│   ├── sre/
│   ├── security/
│   └── qa/
│
├── project-brain/
├── tasks/
├── tests/
└── .github/
    ├── workflows/
    ├── ISSUE_TEMPLATE/
    └── PULL_REQUEST_TEMPLATE.md
```

This structure is intentionally flexible. The repository should evolve with the product rather than forcing the product to fit the repository.

---

# Project Status

**Status: Concept / Early Design**

The current focus is on defining:

* Agent responsibilities.
* Human approval boundaries.
* Project Brain structure.
* Agent communication.
* Decision governance.
* Product and engineering workflows.
* Technical architecture.

Implementation should follow the validated organizational model rather than getting ahead of it.

---

# Roadmap

### Phase 1 — Organization

* [ ] Define agent roles and boundaries.
* [ ] Define approval and escalation rules.
* [ ] Define project artifacts.
* [ ] Define agent communication contracts.

### Phase 2 — Project Brain

* [ ] Implement persistent project memory.
* [ ] Define artifact schemas.
* [ ] Implement context retrieval.
* [ ] Implement decision and ADR management.
* [ ] Implement project state management.

### Phase 3 — Core Agents

* [ ] Agent Partner.
* [ ] Architect.
* [ ] Orchestrator.
* [ ] Initial specialist agents.
* [ ] QA and review capabilities.

### Phase 4 — Automation

* [ ] Task decomposition.
* [ ] Agent delegation.
* [ ] Dependency management.
* [ ] Automated verification.
* [ ] Approval workflows.
* [ ] Escalation mechanisms.

### Phase 5 — Controlled Autonomy

* [ ] Agent permissions.
* [ ] Risk-based execution policies.
* [ ] Audit trails.
* [ ] Production safety controls.
* [ ] Gradual expansion of autonomous workflows.

---

# Design Philosophy

The goal is to give an enthusiastic person (Human Founder) something closer to a **small, experienced technology team**—one that can research, think, design, build, test, explain, and raise concerns when necessary.

This project aims to combine both with AI while keeping people firmly in control of the decisions that matter.
