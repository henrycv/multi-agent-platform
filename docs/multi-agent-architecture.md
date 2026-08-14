# AI Agent Team for Dockerized Web Projects

## 1. Introduction

This project aims to create an **AI-native environment for managing and developing an IT product**, designed around a **Human Founder (like you 👤)** who may have a strong product vision but does not necessarily have the experience of a CEO, CTO, Product Manager, Software Architect, or Engineering Manager.

The objective is not simply to create a collection of coding agents.

The objective is to build a **virtual AI organization** that can help transform an initial human idea into a validated product, a coherent technical architecture, and ultimately a working software system.

The main principle is:

> Each agent should have a clearly defined responsibility and should not unnecessarily perform tasks belonging to another agent.

The **Human Founder** remains at the center of the system, while the **Agent Partner** should behave more like a CTO + Product cofounder.

They provide ideas, goals, context, constraints, questions, and decisions. AI agents provide the specialized knowledge, analysis, planning, coordination, implementation, and verification required to move the project forward.

The system should therefore behave less like an AI coding assistant and more like a **small, highly coordinated technology company whose primary human stakeholder is the Founder**.

---

### Human-in-the-Loop by Design

The system is intended to be **AI-assisted and increasingly autonomous, but not blindly autonomous**.

Agents should be able to independently perform appropriate research, analysis, implementation, testing, and other reversible tasks.

However, **important decisions should remain subject to Human Founder approval**.

Examples include:

- Major changes to product direction.
- Significant scope changes.
- Business model decisions.
- Major technology choices.
- Major architecture changes.
- Security-sensitive decisions.
- Production-impacting actions.
- Irreversible operations.
- Decisions involving significant financial or business risk.

The goal is not to remove the Human Founder from the process.

The goal is to allow the Human Founder to operate effectively without personally needing to become an expert in every discipline involved in building a technology company.

---

### The Core Concept

The proposed organization follows this hierarchy:

```text
                         ┌─────────────────────┐
                         │ 👤 HUMAN FOUNDER    │
                         │                     │
                         │ Ideas               │
                         │ Vision              │
                         │ Goals               │
                         │ Questions           │
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
                         │ Project Planning    │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    🏗️ ARCHITECT     │
                         │     AI AGENT        │
                         │                     │
                         │ System Design       │
                         │ Technology Stack    │
                         │ Services & APIs     │
                         │ Data Architecture   │
                         │ Security            │
                         │ Architecture ADRs   │
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
                         │ Tracks State        │
                         │ Coordinates Agents  │
                         │ Resolves Conflicts  │
                         └──────────┬──────────┘
                                    │
                                    │  (AI AGENT SPECIALISTS)
          ┌─────────────┬───────────┼───────────┬─────────────┬─────────────┐
          │             │           │           │             │             │
          ▼             ▼           ▼           ▼             ▼             ▼
     ┌─────────┐   ┌─────────┐ ┌─────────┐ ┌─────────┐   ┌─────────┐   ┌─────────┐
     │  UX/UI  │   │Frontend │ │ Backend │ │ Backend │   │   SRE   │   │  Data   │
     │  Agent  │   │  Agent  │ │   JS    │ │   PHP   │   │  Agent  │   │  Agent  │
     └────┬────┘   └────┬────┘ └────┬────┘ └────┬────┘   └────┬────┘   └────┬────┘
          │             │           │           │             │             │
          └─────────────┴───────────┴───────────┴─────────────┴─────────────┘
                                    │
                                    ▼
                              ┌────────────┐
                              │  🔎 QA     │
                              │  AI AGENT  │
                              │            │
                              │ Browser    │
                              │ E2E        │
                              │ Tests      │
                              │ Validation │
                              └────────────┘
```

### From Human Idea to Working Product

The system is intended to support the complete lifecycle of an IT project.

A typical interaction should look like:

```text
Human Founder
      │
      │ "I have an idea..."
      ▼
Agent Partner
      │
      ├── Understands the idea
      ├── Asks questions
      ├── Identifies assumptions
      ├── Challenges weak points
      ├── Researches unknowns
      ├── Evaluates alternatives
      └── Helps define the desired outcome
      │
      ▼
Human Founder
      │
      │ Decision / approval
      ▼
Agent Partner
      │
      │ Product requirements
      ▼
Architect Agent
      │
      ├── Designs system
      ├── Evaluates technology
      ├── Defines services
      ├── Defines data architecture
      └── Documents technical decisions
      │
      ▼
Human Founder
      │
      │ Architecture approval
      ▼
Orchestrator
      │
      ├── Decomposes work
      ├── Creates tasks
      ├── Determines dependencies
      ├── Delegates to specialists
      └── Coordinates execution
      │
      ▼
Specialized Agents
      │
      ├── UX/UI
      ├── Frontend
      ├── Backend
      ├── Data
      ├── SRE
      └── Other specialists
      │
      ▼
QA / Review Agents
      │
      ├── Automated tests
      ├── Browser testing
      ├── Code review
      ├── Security review
      └── Requirement validation
      │
      ▼
Human Founder
      │
      │ Final acceptance / next decision
      ▼
Product Increment
```

The system should therefore optimize not only for code generation, but for the quality of the entire decision-making and delivery process.

### Company/Project Memory

A central concept of this system is a persistent Project Brain.

Agents should not depend exclusively on conversation history or their own temporary context.

Important knowledge should be captured as persistent project artifacts, including:

- Product vision.
- Business objectives.
- User personas.
- Requirements.
- Assumptions.
- Market research.
- Competitor analysis.
- Product roadmap.
- Architecture.
- Architecture Decision Records (ADRs).
- Technical constraints.
- Security requirements.
- Development standards.
- Current backlog.
- Milestones.
- Agent responsibilities.
- Important decisions.
- Open questions.
- Known risks.

This allows every agent to operate from a common understanding of the project.

The Project Brain becomes the project's shared organizational memory.

Every agent should be able to consult this.

Otherwise your agents will gradually develop different interpretations of what you're building.

```text
                    📚 PROJECT BRAIN
                         │
       ┌─────────────────┼─────────────────┐
       ▼                 ▼                 ▼
   Product              Tech              Business
   Vision               Architecture      Market
   Personas             ADRs              Pricing
   Requirements         APIs              Competitors
   Roadmap              Data model        Decisions
   Constraints           Security          Metrics
```

---

## 2. The Human Founder (You)

The **Human Founder** is the owner and ultimate decision-maker of the project.

The Human Founder does not need to have expertise in product management, software architecture, engineering, business strategy, or project management. The purpose of the Agent Partner is specifically to compensate for those gaps while keeping the Human Founder in control.

### Responsibilities

The Human Founder:

- Provides the original ideas, goals, context, constraints, and priorities.
- Describes problems, opportunities, doubts, and desired outcomes in natural language.
- Makes the final decisions when business, product, financial, ethical, or strategic judgment is required.
- Approves or rejects important product and architectural decisions.
- Provides clarification when the Agent Partner identifies missing information.
- Defines personal or business constraints that agents cannot infer reliably.
- Reviews important proposals before irreversible actions are taken.
- Owns the vision, business risk, intellectual property, and final responsibility for the project.

### What the Human Founder does NOT need to do

The Human Founder should not be expected to:

- Know how to design the complete software architecture.
- Know which technologies should be selected.
- Know how to decompose a complex system into engineering tasks.
- Know how to manage multiple specialized coding agents.
- Know how to write detailed technical specifications.
- Understand every implementation detail.
- Personally coordinate every development task.

The Human Founder should be able to say:

> "I have this idea. Help me understand whether it makes sense, what I am missing, and what we should do next."

The AI system should transform that input into structured decisions, plans, and executable work while keeping the Human Founder informed and in control.

---

## 3. High-Level Architecture

```text

                👤 Human Founder
                          │
                          │ ideas / questions /
                          │ decisions / approval
                          ▼
              ┌──────────────────────────┐
              │ 🤝 AGENT PARTNER          │
              │                           │
              │ Product Manager           │
              │ Startup Advisor           │
              │ CTO Advisor               │
              │ Business Analyst          │
              │ Decision Facilitator      │
              │                           │
              │ "What should we build?"   │
              │ "Why?"                    │
              │ "Is it viable?"           │
              │ "What do we do next?"     │
              └────────────┬─────────────┘
                           │
                           ▼
              ┌──────────────────────────┐
              │   🏗️ AGENT ARCHITECT     │
              │                           │
              │ System architecture       │
              │ Technology choices        │
              │ APIs / data / services     │
              │ Security / scalability     │
              │ Architecture decisions     │
              └────────────┬─────────────┘
                           │
                           ▼
              ┌──────────────────────────┐
              │  🎯 AGENT ORCHESTRATOR   │
              │                           │
              │ Break down work           │
              │ Assign specialists        │
              │ Manage dependencies       │
              │ Track progress            │
              │ Request reviews            │
              │ Escalate problems         │
              └────────────┬─────────────┘
                           │
                           │  (AI AGENT SPECIALISTS)
       ┌──────────┬────────┼────────┬──────────┬──────────┐
       ▼          ▼        ▼        ▼          ▼          ▼
     UX/UI    Frontend   Backend   Backend    Data       SRE
                          JS       PHP
       │          │        │        │          │          │
       └──────────┴────────┴────────┴──────────┴──────────┘
                          │
                          ▼
                 ┌────────────────┐
                 │   🔎 AGENT QA  │
                 │    / REVIEW    │
                 │                │
                 │ E2E            │
                 │ Browser        │
                 │ Security       │
                 │ Regression     │
                 └────────────────┘
                          │
                          ▼
                   HUMAN APPROVAL
```

A refined architecture is:

```text
                    ┌───────────────┐
                    │ HUMAN FOUNDER │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │    PARTNER    │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │   ARCHITECT   │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ ORCHESTRATOR  │
                    └───────┬───────┘
                            │
      ┌─────────┼───────────┼─────────────────────────┐
      │         │           │                         │
      ▼         ▼           ▼                         ▼
      UX      DATA       ENGINEERING                 QA
      │         │           │                         │
      │         │   ┌───────┼────────┐                │
      │         │   │       │        │                │
      │         │   ▼       ▼        ▼                │
      │         │ Frontend Backend  SRE               │
      │         │           │                         │
      │         │      ┌────┴────┐                    │
      │         │      ▼         ▼                    │
      │         │      JS       PHP                   │
      │         │                                     │
      └─────────┴───────────┬─────────────────────────┘
                            |
                            ▼
                        PRODUCT

```

---

### Minimum Viable Team

Ten agents is the end state, not the starting point. Each additional agent adds token cost and handoff latency. Start with a lean team and grow it as the project demands:

```text
MVP Team
 ├── Partner         (product direction)
 ├── Architect       (technical plans, non-optional)
 ├── Orchestrator    (planning + delegation + state)
 ├── Engineer        (frontend + backend implementation)
 └── QA              (independent verification)
```

Growth path (add an agent only when it stops being optional):

```text
Partner, Architect, Orchestrator, Engineer, QA
   ↓  split Engineer → Frontend + Backend
   ↓  add SRE (infrastructure)
   ↓  add Data (schema / migrations)
   ↓  add Security (independent review)
   ↓  add Documentation (knowledge sync)
```

The Architect is the one exception to the growth rule: technical planning is a trust boundary from day one, so it ships with the MVP team and sits directly above the Orchestrator.

Rule: **do not add an agent until a single agent has demonstrated it is a bottleneck or a trust boundary.**

---

## 4. Agents

### 4.1 Agent Partner

The **Agent Partner** is the primary AI interface between the Human Founder and the multi-agent project team.

Think the Agent Partner has 5 internal hats. You don't necessarily need five separate agents. 

**Initially** you can just make one Agent Partner with five modes:

#### A. 🤝 Partner

Your default conversational interface.

> "Let's think about this."

#### B. 🧭 Product Manager

Turns ideas into:

- problems
- users
- requirements
- user stories
- MVP
- roadmap
- priorities

#### C. 💼 Business Analyst

Challenges:

- market assumptions
- competitors
- pricing
- business model
- validation strategy
- risks

#### D. 🏗️ CTO Advisor

Answers:

- architecture
- technology selection
- scalability
- security
- integrations
- technical debt

#### E. 🎯 Program Manager

Turns decisions into:

- epics
- tasks
- dependencies
- milestones
- agent assignments
- acceptance criteria

This is important because you don't need to understand the distinction between all these roles.

You talk to one person:

> "I think we should add X."

The Partner decides which "hat" is needed.

The Agent Partner is **not simply a chatbot and not primarily a coding agent**.

Its primary responsibility is to help the Human Founder **think, decide, plan, and coordinate**.

The Agent Partner should understand the project's current state and continuously help answer:

> **What are we trying to achieve?**

> **Why are we doing it?**

> **What assumptions are we making?**

> **What do we know and what do we not know?**

> **What should we do next?**

> **Who or what should do that work?**

> **How do we know the result is good enough?**

---

### Responsibilities

#### A. Understand the Human Founder

The Agent Partner translates informal human input into structured project information.

For example:

> "I think restaurants could use AI to predict how much food they need."

The Agent Partner should not immediately create implementation tasks.

Instead, it should identify:

- The underlying problem.
- Potential users and customers.
- Business assumptions.
- Unclear requirements.
- Risks.
- Questions requiring clarification.
- Opportunities for validation.
- Possible MVP boundaries.

---

#### B. Challenge Ideas Constructively

The Agent Partner should not blindly agree with the Human Founder.

It should respectfully challenge assumptions and identify:

- Contradictions.
- Missing information.
- Unrealistic expectations.
- Technical risks.
- Business risks.
- Excessive scope.
- Unvalidated assumptions.
- Alternative approaches.
- Potentially simpler solutions.

The objective is **not to win an argument**.

The objective is to improve the quality of decisions.

The Agent Partner should be comfortable saying:

> "I don't think we have enough information to make this decision yet."

or:

> "I recommend validating this assumption before we spend development effort."

---

#### C. Convert Ideas into Structured Product Decisions

The Agent Partner transforms validated ideas into artifacts such as:

- Product vision.
- Problem statements.
- Personas.
- User journeys.
- Requirements.
- User stories.
- Acceptance criteria.
- MVP definition.
- Product roadmap.
- Priorities.
- Risks.
- Assumptions.
- Validation experiments.

The Agent Partner should distinguish clearly between:

**Fact**

Information supported by evidence.

**Assumption**

Something believed to be true but not yet validated.

**Decision**

A deliberate choice approved by the Human Founder.

**Proposal**

A recommendation that has not yet been approved.

**Task**

An executable piece of work resulting from an approved decision.

---

### Strategic Decision Support

The Agent Partner helps the Human Founder evaluate alternatives.

For significant decisions it should present:

1. The problem.
2. Relevant context.
3. Available options.
4. Advantages and disadvantages.
5. Risks.
6. Cost/complexity implications.
7. Recommendation.
8. Confidence level.
9. Information still missing.
10. Whether Human Founder approval is required.

The Agent Partner should avoid presenting its recommendation as an unquestionable fact.

The Human Founder remains the final authority.

---

### Coordination with Specialized Agents

The Agent Partner does not necessarily execute every task itself.

When appropriate, it delegates work to specialized agents such as:

- Architecture Agent
- UX/UI Agent
- Frontend Agent
- Backend Agent
- Data Agent
- SRE/DevOps Agent
- Security Agent
- QA Agent
- Research Agent

The Agent Partner is responsible for ensuring that delegated work is consistent with the project's approved:

- Vision.
- Requirements.
- Architecture.
- Constraints.
- Decisions.
- Roadmap.

---

### 4.2. Architect Agent

An additional agent proposed during the discussion is the **Architect Agent**.

The Architect translates product-level requirements into a technical system and implementation plan.

### Responsibilities

* Translate product requirements into technical architecture
* Identify application boundaries
* Determine technologies
* Define service relationships
* Define data flow
* Identify affected components
* Break larger requirements into technical tasks
* Create implementation plans
* Define technical dependencies

### Example

Partner says:

> "We want a SaaS application where users can create projects."

Architect produces something like:

```text
Frontend
React / Next.js

Backend
Laravel API

Database
PostgreSQL

Authentication
...

Storage
...

Infrastructure
Docker Compose

Production
...
```

Then creates technical tasks:

```text
PROJECT-001
Create authentication system

PROJECT-002
Create user model

PROJECT-003
Create login UI

PROJECT-004
Create Docker development environment

PROJECT-005
Create authentication E2E tests
```

The Architect does not necessarily implement those tasks.

Its main role is:

> **Define what the specialists need to implement.**

### Handoff with the Partner

Partner and Architect both make decisions, so define an explicit sign-off boundary to stop them drifting:

```text
Human     →  Have an initial Idea                 (idea)
Partner   →  What should we build and why?        (product)
Architect →  How should the system be structured? (technical)
           ↓
Architect presents the plan to the Partner
           ↓
Partner confirms it matches the product intent
           ↓
Tasks are created
```

Neither agent may unilaterally change a decision the other has already signed off on without surfacing the change to the human.

The Partner should say:

> "This is now sufficiently defined. We need architecture."

Then:

```text
Human Founder
      │
      │ Partner Validation Request
      ▼
Agent Partner
      │
      │ Architecture Request
      ▼
Architecture Agent
      │
      ├── evaluates options
      ├── identifies constraints
      ├── creates ADR
      ├── proposes stack
      ├── designs services
      └── identifies dependencies
             │
             ▼
        Agent Partner
             │
             │ "Here is the architecture.
             │  Do you approve?"
             ▼
        Human Founder
```

That human approval gate is extremely important.

You shouldn't allow an autonomous agent to silently decide:

>"We're now going to build 17 microservices with Kubernetes."

😂

---

### 4.3. Orchestrator Agent

The **Orchestrator Agent** is the workflow coordinator of the team. It is the agent that plans, assigns, and tracks work across all specialists — and the one that merges the results back together.

It does **not** need to be the most intelligent agent, and it does **not** implement features itself.

### Responsibilities

* Understand the current project state
* Select the appropriate specialist for a task
* Create and assign narrowly scoped tasks
* Give each specialist the necessary context
* Collect results and update project state
* Send failures back to the responsible agent
* Manage the dependency-aware backlog
* Resolve conflicts between agents
* Verify the Definition of Done before closing a task
* Escalate important decisions to the human
* Recover in-flight work after a crash (idempotent restart)

### Example

> Architect: "PROJECT-001: Create the authentication system."

Orchestrator:

```text
1. Check dependencies — the SRE dev environment must be done first
2. Dispatch PROJECT-001 to the Backend JS Agent
3. Dispatch PROJECT-003 (login UI) to the Frontend Agent
4. Collect results and update task state
5. Dispatch QA E2E-001 (authentication flow)
6. Review diffs and merge approved branches to main
7. Mark tasks DONE, or send failures back for rework
```

The Orchestrator's full behavior — backlog, escalation, and crash recovery — is described in §8.

---

### 4.4 SRE / DevOps Agent

The **SRE Agent** owns infrastructure and deployment concerns.

### Responsibilities

```text
Docker
Docker Compose
Dockerfiles
CI/CD
GitHub Actions
Kubernetes
Terraform
Nginx
Traefik
Reverse proxies
TLS
Secrets
Environment configuration
Monitoring
Logging
Backups
Deployments
```

### Principle

Backend agents should be able to communicate requirements to SRE, but they should not automatically modify infrastructure.

For example:

> Backend PHP: "The application requires DATABASE_URL and REDIS_URL."

> SRE: "I'll integrate these requirements into the deployment environment."

This creates a clean separation between application code and infrastructure.

### Environment Parity

Keep dev, staging, and production distinct:

```text
Dev        → agents work here, freely
Staging    → integration + QA verification, SRE-managed
Production → no agent touches it directly
```

Rules:

* Agents operate in the development environment only.
* Promotion from dev → staging → production is an SRE-only activity.
* Releases to production always require a human approval (see Human Approval Gates).

---

### 4.5 Data / Database Agent

The **Data Agent** owns everything related to persistent data. Without an explicit owner, schema design, migrations, and seed data fall between the backend agents — exactly the kind of fragmentation this architecture tries to avoid.

### Responsibilities

```text
Database schema design
Migrations
Seed / fixture data
Data modeling (entities, relations)
Indexes and query performance
Referential integrity
Data validation rules at rest
Backup/restore of application data (with SRE)
```

### Principle

Backend agents propose data requirements; the Data Agent owns the schema and the migration lifecycle.

> Backend PHP: "Users need a `profiles` table with a unique email."

> Data Agent: "I'll add the migration and the model mapping."

The Data Agent does not own infrastructure (that is SRE) and does not implement business logic (that is the backend agents). It is the single source of truth for the data layer.

---

### 4.6. UX Agent

The **UX/UI Agent** owns product interaction and visual design.

### Technologies / Tools / Skills

```text
Figma
Wireframes
Design systems
Components
User flows
Information architecture
Visual hierarchy
Responsive layouts
Accessibility
```

Its outputs do not necessarily need to be code.

Example workflow:

```text
Requirement
    ↓
UX Agent
    ↓
User flow
    ↓
Wireframe
    ↓
Visual design
    ↓
Design specification
    ↓
Frontend Agent
```

The UX/UI Agent defines what users should experience.

The Frontend Agent implements it.

---

### 4.7. Backend JS Agent

The **Backend JS Agent** owns server-side JavaScript and TypeScript implementation.

### Technologies / Skills

```text
Node.js
TypeScript
JavaScript
Express
Fastify
NestJS
Next.js API
ORMs
REST
GraphQL
WebSockets
Backend tests
```

### Responsibility

> Implement server-side JavaScript/TypeScript functionality and its tests.

Example task:

```text
Task:
Create POST /api/users

Backend JS Agent:

1. Inspect existing architecture
2. Implement endpoint
3. Implement validation
4. Implement service
5. Implement tests
6. Run tests
7. Report result
```

The Backend JS Agent should not normally modify Docker infrastructure unless explicitly delegated to do so.

---

### 4.8. Backend PHP Agent

The **Backend PHP Agent** owns PHP application development.

### Technologies / Skills

```text
PHP
Laravel
Symfony
Composer
PHPUnit
Pest
Doctrine
Eloquent
REST APIs
Queues
Console commands
```

### Responsibility

> Implement PHP application functionality and tests.

This agent can eventually coexist with other backend agents:

```text
Backend JS Agent
Backend PHP Agent
Backend Python Agent
Backend Go Agent
Backend Rust Agent
```

The Data Agent owns schema, migrations, and seed data (§3.5). Backend agents implement business logic against the schema but coordinate any schema change through the Data Agent rather than modifying migrations directly.

---

### 4.9. Frontend Agent

The **Frontend Agent** owns frontend implementation.

### Technologies / Skills

```text
HTML
CSS
JavaScript
TypeScript
React
Next.js
Vue
Svelte
Tailwind
Component libraries
Frontend state
Forms
Accessibility
Frontend tests
```

### Responsibility

> Implement the frontend based on requirements and UX/UI specifications.

The Frontend Agent should not be responsible for visual/product design decisions themselves.

That belongs to the UX/UI Agent.

Example:

```text
UX Agent:
"The login page should have these elements and this interaction."

Frontend Agent:
"I'll implement that design."
```

This creates a clean division.

---

### 4.10. QA Agent

The **QA Agent** is responsible for independent verification.

An important design principle is:

> The agent that implements a feature should not be the sole authority deciding whether the feature works.

### Responsibilities

```text
Browser automation
End-to-end testing
API testing
Database inspection
Test runners
Screenshots
Accessibility testing
Performance testing
```

Potential tool:

```text
Playwright
```

### Example

```text
Backend Agent
      │
      ▼
 implementation
      │
      ▼
 QA Agent
      │
      ├── PASS
      │
      └── FAIL
             │
             ▼
        bug report
             │
             ▼
       Backend Agent
```

Example QA report:

```text
QA-142

Scenario:
User registration

Result:
FAIL

Steps:
1. Open /register
2. Enter valid email
3. Enter password
4. Submit

Expected:
Account created and redirect to dashboard.

Actual:
500 Internal Server Error.

Evidence:
...
```

The responsible implementation agent then fixes the problem.

---

### 4.11. Security Agent

A Security Agent was also proposed as a useful additional specialization.

### Responsibilities

```text
Dependency vulnerabilities
Authentication review
Authorization
OWASP issues
Secrets
Docker security
API security
Input validation
XSS
CSRF
SQL injection
SSRF
Permissions
```

Its primary role is to **find problems and report them**, rather than being the main implementation agent.

This provides an independent security verification layer.

---

### 4.12. Documentation Agent

A Documentation Agent can own project knowledge that must remain synchronized with the implementation.

### Responsibilities

```text
README
API documentation
Architecture documentation
ADR
Developer documentation
Deployment documentation
Changelog
```

The Documentation Agent observes the work performed by other agents and updates the project's documented knowledge.

---

## 5. Agent vs. Skill

An important architectural refinement is to distinguish between:

* **Agent**
* **Skill**
* **Tool**

An agent represents a responsibility/domain.

A skill represents a reusable capability.

A tool represents an external operation.

For example:

```text
Frontend Agent
      │
      ├── React skill
      ├── Vue skill
      ├── Svelte skill
      ├── Tailwind skill
      └── Accessibility skill
```

Similarly:

```text
Backend Agent
      │
      ├── JavaScript skill
      ├── TypeScript skill
      ├── PHP skill
      ├── Python skill
      └── Go skill
```

This suggests that skills should be **composable**.

The architecture should not fundamentally depend on creating a separate agent for every programming language.

Agents can still remain distinct when they require different:

* responsibilities
* permissions
* tools
* workflows
* review rules
* system prompts
* isolation boundaries

---

## 6. Shared Project Knowledge

Agents should not primarily communicate through huge conversational exchanges.

Instead, the project should contain **shared artifacts and state**.

Example:

```text
project/
│
├── AGENTS.md
│
├── docs/
│   ├── product.md
│   ├── architecture.md
│   ├── decisions/
│   └── requirements/
│
├── design/
│   ├── wireframes/
│   └── design-system.md
│
├── tasks/
│   ├── TODO/
│   ├── IN_PROGRESS/
│   ├── REVIEW/
│   └── DONE/
│
├── frontend/
├── backend/
├── infrastructure/
└── tests/
```

Example communication flow:

```text
UX Agent
   ↓
design/login.md
   ↓
Frontend Agent
   ↓
frontend implementation
   ↓
QA Agent
   ↓
qa/login-report.md
   ↓
Frontend Agent
   ↓
fix
```

This is preferable to passing large conversation histories from one agent to another.

## 7. Versioned Artifacts and State Consistency

Because artifacts are the primary communication channel, keep them consistent:

* **One artifact = one owner.** Each artifact has a designated owning agent; concurrent writers route through that owner or the Orchestrator.
* **Version artifacts.** Give important artifacts (plans, specs, decisions) a revision history so changes are reviewable.
* **Orchestrator context rebuild.** The Orchestrator should be able to reconstruct its working context from (a) per-agent summaries and (b) the artifact index — without replaying full conversations. This makes restart cheap and state auditable.

---

## 8. Agent-Specific Constitutions and Skills

Each agent should have its own instructions and capabilities.

Example structure:

```text
agents/
│
├── partner/
│   ├── AGENT.md
│   └── skills/
│       ├── product-discovery/
│       ├── brainstorming/
│       └── requirements/
│
├── architect/
│   ├── AGENT.md
│   └── skills/
│       ├── architecture/
│       ├── system-design/
│       └── task-decomposition/
│
├── orchestrator/
│   ├── AGENT.md
│   └── skills/
│       ├── workflow/
│       ├── task-decomposition/
│       ├── backlog-management/
│       └── escalation/
│
├── sre/
│   ├── AGENT.md
│   └── skills/
│       ├── docker/
│       ├── github-actions/
│       ├── nginx/
│       └── deployment/
│
├── data/
│   ├── AGENT.md
│   └── skills/
│       ├── schema-design/
│       ├── migrations/
│       ├── seed-data/
│       └── query-optimization/
│
├── backend-js/
│   ├── AGENT.md
│   └── skills/
│       ├── node/
│       ├── typescript/
│       ├── express/
│       ├── nextjs/
│       └── testing/
│
├── backend-php/
│   ├── AGENT.md
│   └── skills/
│       ├── php/
│       ├── laravel/
│       ├── symfony/
│       └── phpunit/
│
├── frontend/
│   ├── AGENT.md
│   └── skills/
│       ├── react/
│       ├── nextjs/
│       ├── tailwind/
│       └── accessibility/
│
├── ux/
│   ├── AGENT.md
│   └── skills/
│       ├── wireframing/
│       ├── design-systems/
│       └── user-flows/
│
├── qa/
│   ├── AGENT.md
│   └── skills/
│       ├── playwright/
│       ├── api-testing/
│       └── accessibility/
│
├── security/
│   ├── AGENT.md
│   └── skills/
│       ├── web-security/
│       ├── dependency-audit/
│       └── container-security/
│
└── documentation/
    ├── AGENT.md
    └── skills/
        ├── markdown/
        ├── api-docs/
        └── architecture-docs/
```

This gives the overall system a **plugin-like architecture**.

---

## 9. The Orchestrator

The **Orchestrator** is the key component.

It doesn't necessarily need to be the most intelligent agent.

Its primary responsibilities are:

1. Understand current project state
2. Select the appropriate specialist
3. Create or assign a narrowly scoped task
4. Give that specialist the necessary context
5. Collect the result
6. Update project state
7. Invoke another specialist when necessary
8. Send failures back to the responsible agent
9. Escalate important decisions to the human

Conceptually:

```text
                         ┌─────────────────────┐
                         │       PARTNER       │
                         │                     │
                         │ Product / Decisions │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    ARCHITECT        │
                         │                     │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    ORCHESTRATOR     │
                         │                     │
                         │ Understand state    │
                         │ Select specialist   │
                         │ Assign task         │
                         │ Collect result      │
                         │ Manage workflow     │
                         └──────────┬──────────┘
                                    │
       ┌───────────────┬────────────┼───────────────┬───────────────┐
       │               │            │               │               │
       ▼               ▼            ▼               ▼               ▼
      UX          Frontend      Backend JS      Backend PHP         DATA
       │               │            │               │               │
       └───────────────┴────────────┴───────────────┴───────────────┘
                                    │
                                    ▼
                                   SRE
                                    │
                                    ▼
                                  Docker
                                    │
                                    ▼
                               Running app
                                    │
                     ┌──────────────┴─────────────┐
                     ▼                            ▼
                    QA                         Security
                     │                            │
                     └──────────────┬─────────────┘
                                    ▼
                               Documentation
```

### Dependency-Aware Backlog

The Orchestrator manages a backlog, not a simple queue. Tasks may have dependencies; a task with unmet dependencies is not dispatched.

```text
Backlog (ordered by dependency + priority)
 ├── [ ] SRE: dev environment compose        (blocks everything)
 ├── [ ] Backend: user model + auth API      (blocks E2E-001)
 ├── [ ] Frontend: login UI                  (blocks E2E-001)
 └── [ ] QA: E2E-001 auth flow               (needs the three above)
```

### Escalation to the Human

Decisions the Orchestrator cannot make locally are escalated. Define the triggers explicitly:

```text
Ambiguous or contradictory requirements
Cross-domain conflicts (UX vs Frontend, Backend vs SRE)
Security findings above a set severity threshold
Any task that exhausts its budget (see Budgets, Timeouts, and Retries)
Anything touching production
```

### Recovery After a Crash

State lives on disk (see Project State), so a crash should not lose work:

* Task records must be **idempotently resumable** — restarting the Orchestrator must not duplicate in-flight work.
* On restart, the Orchestrator re-reads the artifact index and re-assigns only tasks in `IN_PROGRESS`/`REVIEW` whose owning agent is not still running.

---

## 10. Project State

The system should maintain explicit task/project state instead of relying only on conversation context.

A task could conceptually contain:

```text
Task
 ├── requirements
 ├── assumptions
 ├── plan
 ├── files_changed
 ├── commands_executed
 ├── tests
 ├── failures
 ├── fixes
 └── final_status
```

Task lifecycle can be:

```text
TODO
  ↓
IN_PROGRESS
  ↓
REVIEW
  ↓
DONE
```

or, when something fails:

```text
IN_PROGRESS
  ↓
FAILED
  ↓
REWORK
  ↓
REVIEW
  ↓
DONE
```

### Definition of Done

Every task carries explicit completion criteria before it is marked `DONE`:

```text
Unit tests pass
Integration / E2E tests pass (where applicable)
QA verified the behavior independently
No unresolved security findings at or above threshold
Documentation affected by the change is updated
```

A task is not `DONE` on the implementer's word alone; the criteria are checked by the Orchestrator and, where applicable, by QA.

### Budgets, Timeouts, and Retries

A task that can run forever can burn unbounded tokens and time. Every task gets a budget:

```text
max_steps      → hard cap on agent actions
max_time       → wall-clock timeout
max_retries    → retry cap on FAILED → REWORK cycles
cost_budget    → token / cost ceiling
```

When a budget is exhausted the task moves to `FAILED` with a report, and the Orchestrator escalates to the human. A task exceeding its retry cap is **not automatically re-dispatched** — it signals a deeper problem: a weak agent, bad requirements, or wrong decomposition.

---

## 11. Agent Communication

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
       Partner
         ↓
        YOU
```

---

## 12. Separation of Responsibilities

A core principle is that agents should have **isolated responsibilities**.

Examples:

### UX vs Frontend

```text
UX:
What should the user experience?

Frontend:
How is that experience implemented?
```

### Backend vs SRE

```text
Backend:
What application functionality is needed?

SRE:
How is that application built, configured, deployed, monitored, and operated?
```

### Implementation vs QA

```text
Implementation:
Build the feature.

QA:
Independently verify the feature.
```

### Product vs Architecture

```text
Partner:
What should we build and why?

Architect:
How should the system be structured technically?
```

This separation helps prevent one agent from becoming an uncontrolled "do everything" agent.

---

## 13. QA Feedback Loop

The QA feedback loop is especially important.

```text
Implementation Agent
        │
        ▼
    Code change
        │
        ▼
       Build
        │
        ▼
    QA Agent
        │
   ┌────┴─────┐
   │          │
  PASS       FAIL
   │          │
   ▼          ▼
  Done     Bug report
              │
              ▼
       Responsible Agent
              │
              ▼
            Fix
              │
              ▼
             QA
```

The same model should not be the only authority evaluating its own implementation.

---

## 14. Docker / SRE Feedback Loop

The infrastructure workflow can similarly be automated:

```text
Application change
        ↓
SRE
        ↓
Docker build
        ↓
docker compose up
        ↓
Health checks
        ↓
Logs
        ↓
Validation
        │
   ┌────┴─────┐
   │          │
 PASS        FAIL
   │          │
   ▼          ▼
 Continue   Diagnose
              │
              ▼
          Responsible Agent
```

This creates an iterative engineering environment rather than simple code generation.

---

## 15. Git as a Safety Boundary

Git should provide a strong boundary around autonomous changes.

Conceptually:

```text
main
 │
 ├── agent/task-123
 │
 └── agent/task-124
```

For a task:

```text
Create branch
    ↓
Implement
    ↓
Test
    ↓
Review diff
    ↓
Commit
    ↓
Open PR / Request approval
```

The system can eventually become more autonomous, but the human should remain able to review or reject changes.

### Human Approval Gates

Git is the boundary, but not every merge needs a human. Define which events require explicit human approval:

```text
Always approve:    schema migrations, dependency version changes,
                   secrets / config, infrastructure changes,
                   production releases
Usually approve:   cross-module refactors, PRs touching many files
Auto-approve:      small, well-tested changes inside a single module
                   (only after the team has a proven track record)
```

The approval matrix should be conservative at first and relaxed only as trust is earned.

### Concurrency and Merge Ownership

Multiple agents working in parallel on one repository will collide. Two rules keep it safe:

* **One active implementer per shared workspace/module**, or
* **Parallel agents on strictly disjoint modules**, with the Orchestrator as the merge owner.

Branching model (per task) is the default:

```text
agent/task-123  →  implement + test  →  Orchestrator reviews diff  →  merge to main
```

Whoever merges is responsible for conflict resolution. When parallel agents touch the same file, merge back through the Orchestrator rather than letting the agents merge directly.

---

## 16. One Important Architectural Principle

The system should be designed around:

> **Agent = responsibility**
>
> **Skill = reusable capability**
>
> **Tool = external operation**
>
> **Task = unit of work**
>
> **Artifact = persistent result**
>
> **Orchestrator = workflow coordination**
>
> **Human = final authority**
>
> **Budget = bounded work (time / steps / tokens)**
>
> **Definition of Done = explicit completion criteria**
>
> **Approval = human-controlled gate**

This gives the system a clean set of abstractions.

---

## 17. Meta-Observability & Learning Loop

The team that monitors the product should also monitor itself. Track per-agent operational metrics so a weak agent is visible before it wastes the whole project:

```text
Failure rate per agent
Rework cycles per task (FAILED → REWORK → DONE)
Cost per task and per agent
Average completion time per task
Escalation frequency to the human
```

### The Learning Loop

The system should get smarter over time. After a `FAILED → REWORK → DONE` cycle, run a lightweight post-mortem and fold the lessons back into the project knowledge:

```text
What failed?
Why did it fail?
What rule would have prevented it?
Update AGENTS.md / ADRs accordingly
```

Without this loop the same failure class recurs indefinitely; with it, the team behaves like a real team that reviews its own incidents.

---

## 18. Anti-Patterns

This architecture is not the right tool for every job. Recognize when the overhead of a multi-agent team is a net loss:

```text
Cross-cutting refactors
   → one change touching every module; handoff overhead dominates

Tiny one-off tasks
   → writing a task, dispatching, and collecting the result
     costs more than the task itself

Live / exploratory iteration
   → fast human-in-the-loop iteration beats asynchronous delegation

Tightly coupled work
   → if two agents must constantly coordinate, you have one task, not two

Very small projects
   → the MVP team already covers it; more agents = more ceremony
```

When these signals appear, collapse to fewer agents or handle the work in a single session with the Orchestrator.

---

## 19. Example Agent Ecosystem

A possible final ecosystem:

```text
                    ┌─────────────────┐
                    │  HUMAN FOUNDER  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  🤝 PARTNER     │
                    │ Product / Ideas │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    ARCHITECT    │
                    │ Technical Plan  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  ORCHESTRATOR   │
                    │  Delegation/    │
                    │  Workflow state │
                    └────────┬────────┘
                             │
          ┌──────────────────┼───────────────┬──────────────────┐
          │                  │               │                  │
          ▼                  ▼               ▼                  ▼
      ┌───────┐         ┌──────────┐      ┌─────┐           ┌───────┐
      │  UX   │         │Frontend  │      │ SRE │           │  Data │
      └───┬───┘         └────┬─────┘      └──┬──┘           └───┬───┘
          │                  │               │                  │
          │                  │               ▼                  │
          │                  │            Docker                │
          │                  │               │                  │
          │            ┌─────┴─────┐         │                  │
          │            ▼     │     ▼         │                  │
          │       Backend JS │ Backend PHP   │                  │
          │            │     │     │         │                  │
          └────────────┴─────┴─────┴─────────┴──────────────────┘
                             │
                             ▼
                      ┌────────────┐
                      │     QA     │
                      └─────┬──────┘
                            │
                            ▼
                      ┌────────────┐
                      │  Security  │
                      └─────┬──────┘
                            │
                            ▼
                    ┌────────────────┐
                    │ Documentation  │
                    └────────────────┘
```

---

## 20. Final Concept

The overall idea can be summarized as:

```text
You
 ↓
Agent Partner
 ↓
Architect
 ↓
Orchestrator
 ↓
Specialized Agents
 ├── UX/UI
 ├── Frontend
 ├── Backend JS
 ├── Backend PHP
 ├── Data
 ├── SRE / DevOps
 ├── QA
 ├── Security
 └── Documentation
 ↓
Shared project state
 ↓
Tasks + Artifacts + Code + Infrastructure + Tests
```

The system should behave less like:

```text
"Ask one AI to build my app."
```

and more like:

```text
"Run a virtual software team where each AI has
a narrow responsibility, explicit skills, controlled
tools, persistent project knowledge, and a coordinator
that moves work between specialists."
```

The key architectural goal is **specialization without fragmentation**:

* Agents are specialized.
* Skills are reusable.
* Tools are isolated.
* Tasks are explicit.
* Artifacts persist.
* QA is independent.
* Infrastructure is separated from application development.
* Product decisions remain human-guided.
* Work is bounded by budgets, retries, and human approval gates.
* The Orchestrator coordinates the whole system.

---
## 21. Guiding Philosophy

The system should follow a simple principle:

> **The Human Founder decides what and why. The AI organization helps determine how, coordinates the work, executes it, and verifies the result.**

The system should favor:

* Clarity over complexity.
* Evidence over assumptions.
* Validation before implementation.
* Small incremental steps.
* Explicit decisions.
* Persistent knowledge.
* Clear responsibilities.
* Constructive disagreement.
* Human approval at important decision points.
* Specialized agents where specialization provides real value.
* Automation of repetitive execution and coordination.

The ultimate goal is to create an **AI-native project organization that amplifies a human founder**, allowing a person with an idea and limited experience in technology management to operate with the support of a coordinated virtual product, architecture, engineering, and quality organization.

This project is therefore not primarily about building more agents.

It is about building a **coherent system in which humans and specialized AI agents can work together as an organization**.