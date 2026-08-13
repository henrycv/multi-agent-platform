# AI Agent Team for Dockerized Web Projects

## 1. Vision

The goal is to build a **team of specialized AI agents** that collaborate to implement and maintain a dockerized web project.

This is **not** a single autonomous coding agent.

Instead, the system is composed of multiple agents with **isolated responsibilities, tools, permissions, and skills**, coordinated by an **Orchestrator** and ultimately guided by a human through an **Agent Partner**.

The main principle is:

> Each agent should have a clearly defined responsibility and should not unnecessarily perform tasks belonging to another agent.

The architecture should allow new agents and skills to be added without redesigning the whole system.

---

## 2. High-Level Architecture

```text
                         ┌─────────────────────┐
                         │   🤝 Agent Partner  │
                         │ Product / Strategy  │
                         │ Ideas / Decisions   │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │  Agent Architect    │
                         │  - System Design    │
                         │  - Tech Stack & DAG │
                         │  - Service & Data   │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │   Agent Orchestrator│
                         │                     │
                         │ Plans work          │
                         │ Delegates tasks     │
                         │ Tracks state        │
                         │ Resolves conflicts  │
                         └──────────┬──────────┘
                                    │
          ┌─────────────┬───────────┼───────────┬─────────────┬─────────────┐
          │             │           │           │             │             │
          ▼             ▼           ▼           ▼             ▼             ▼
     ┌─────────┐   ┌─────────┐ ┌─────────┐ ┌─────────┐   ┌─────────┐   ┌─────────┐
     │ UX/UI   │   │Frontend │ │ Backend │ │Backend  │   │  SRE    │   │  Data   │
     │ Agent   │   │ Agent   │ │ JS      │ │ PHP     │   │  Agent  │   │  Agent  │
     └────┬────┘   └────┬────┘ └────┬────┘ └────┬────┘   └────┬────┘   └────┬────┘
          │             │           │           │             │             │
          └─────────────┴───────────┴───────────┴─────────────┴─────────────┘
                                    │
                                    ▼
                              ┌────────────┐
                              │  QA Agent  │
                              │ Browser /  │
                              │ E2E / Test │
                              └────────────┘
```

A refined architecture is:

```text
                    ┌───────────────┐
                    │      YOU      │
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
      UX         DATA     ENGINEERING                 QA
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

## 3. Agents

### 3.1 Agent Partner

The **Agent Partner** is the primary human-facing agent.

It does **not** primarily code or perform SRE tasks.

### Responsibilities

* Understand the product
* Understand business goals
* Brainstorm ideas
* Explore requirements
* Discuss trade-offs
* Help make decisions
* Maintain conceptual understanding of the project
* Discuss architecture at a conceptual level
* Help define roadmap
* Determine what needs to happen next

### Example

User:

> "I want to build a SaaS platform where users can create projects."

Partner:

> "We could structure the product around organizations, projects, members, and roles. A first MVP could include authentication, project creation, dashboard, and invitations."

The Partner can recommend technologies:

> "Laravel could be a good backend choice because..."

But it does not necessarily implement Laravel itself.

Its role is essentially:

> **What should we build, and why?**

The Partner is the **main human-facing interface**.

---

### 3.2. Architect Agent

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

---

### 3.3. Orchestrator Agent

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

### 3.4 SRE / DevOps Agent

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

### 3.5 Data / Database Agent

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

### 3.6. UX Agent

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

### 3.7. Backend JS Agent

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

### 3.8. Backend PHP Agent

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

### 3.9. Frontend Agent

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

### 3.10. QA Agent

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

### 3.11. Security Agent

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

### 3.12. Documentation Agent

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

## 4. Agent vs. Skill

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

## 5. Shared Project Knowledge

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

## 6. Versioned Artifacts and State Consistency

Because artifacts are the primary communication channel, keep them consistent:

* **One artifact = one owner.** Each artifact has a designated owning agent; concurrent writers route through that owner or the Orchestrator.
* **Version artifacts.** Give important artifacts (plans, specs, decisions) a revision history so changes are reviewable.
* **Orchestrator context rebuild.** The Orchestrator should be able to reconstruct its working context from (a) per-agent summaries and (b) the artifact index — without replaying full conversations. This makes restart cheap and state auditable.

---

## 7. Agent-Specific Constitutions and Skills

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

## 8. The Orchestrator

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

## 9. Project State

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

## 10. Agent Communication

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

## 11. Separation of Responsibilities

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

## 12. QA Feedback Loop

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

## 13. Docker / SRE Feedback Loop

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

## 14. Git as a Safety Boundary

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

## 15. One Important Architectural Principle

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

## 16. Meta-Observability & Learning Loop

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

## 17. Anti-Patterns

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

## 18. Example Agent Ecosystem

A possible final ecosystem:

```text
                    ┌─────────────────┐
                    │       YOU       │
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

## 19. Final Concept

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
