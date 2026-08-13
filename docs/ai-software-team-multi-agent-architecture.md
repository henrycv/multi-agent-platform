# AI Agent Team for Dockerized Web Projects

## 1. Vision

The goal is to build a **team of specialized AI agents** that collaborate to implement and maintain a dockerized web project.

This is **not** a single autonomous coding agent.

Instead, the system is composed of multiple agents with **isolated responsibilities, tools, permissions, and skills**, coordinated by an **Orchestrator** and ultimately guided by a human through an **Agent Partner**.

The main principle is:

> Each agent should have a clearly defined responsibility and should not unnecessarily perform tasks belonging to another agent.

The architecture should allow new agents and skills to be added without redesigning the whole system.

---

# 2. High-Level Architecture

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
          ┌───────────────┬─────────┼─────────┬───────────────┐
          │               │         │         │               │
          ▼               ▼         ▼         ▼               ▼
     ┌─────────┐     ┌─────────┐ ┌───────┐ ┌─────────┐ ┌─────────┐
     │ UX/UI   │     │Frontend │ │Backend│ │Backend  │ │  SRE    │
     │ Agent   │     │ Agent   │ │ JS    │ │ PHP     │ │  Agent  │
     └────┬────┘     └────┬────┘ └───┬───┘ └────┬────┘ └────┬────┘
          │               │           │           │           │
          └───────────────┴───────────┴───────────┴───────────┘
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
        ┌───────────────────┼────────────────────┐
        │                   │                    │
        ▼                   ▼                    ▼
       UX                ENGINEERING            QA
        │                   │                    │
        │          ┌────────┼─────────┐          │
        │          │        │         │          │
        │          ▼        ▼         ▼          │
        │       Frontend   Backend    SRE         │
        │                    │                    │
        │               ┌────┴────┐               │
        │               ▼         ▼               │
        │              JS        PHP              │
        │                                          │
        └──────────────────┬───────────────────────┘
                           ▼
                       PRODUCT
```

---

# 3. Agents

## 3.1 Agent Partner

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

# 4. Architect Agent

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

---

# 5. SRE / DevOps Agent

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

---

# 6. Backend JS Agent

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

# 7. Backend PHP Agent

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

---

# 8. Frontend Agent

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

# 9. UX/UI Agent

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

# 10. QA Agent

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

# 11. Security Agent

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

# 12. Documentation Agent

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

# 13. Agent vs. Skill

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

# 14. Shared Project Knowledge

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

---

# 15. Agent-Specific Constitutions and Skills

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
├── sre/
│   ├── AGENT.md
│   └── skills/
│       ├── docker/
│       ├── github-actions/
│       ├── nginx/
│       └── deployment/
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

# 16. The Orchestrator

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
       ┌───────────────┬────────────┼───────────────┐
       │               │            │               │
       ▼               ▼            ▼               ▼
      UX          Frontend      Backend JS      Backend PHP
       │               │            │               │
       └───────────────┴────────────┴───────────────┘
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

---

# 17. Project State

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

---

# 18. Agent Communication

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

# 19. Separation of Responsibilities

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

# 20. QA Feedback Loop

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

# 21. Docker / SRE Feedback Loop

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

# 22. Git as a Safety Boundary

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

---

# 23. One Important Architectural Principle

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

This gives the system a clean set of abstractions.

---

# 24. Example Agent Ecosystem

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
          ┌──────────────────┼───────────────────┐
          │                  │                   │
          ▼                  ▼                   ▼
      ┌───────┐         ┌──────────┐         ┌─────┐
      │  UX   │         │Frontend  │         │ SRE │
      └───┬───┘         └────┬─────┘         └──┬──┘
          │                  │                   │
          │                  │                   ▼
          │                  │                Docker
          │                  │                   │
          │             ┌────┴─────┐             │
          │             ▼          ▼             │
          │        Backend JS   Backend PHP      │
          │             │          │             │
          └─────────────┴──────────┴─────────────┘
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

# 25. Final Concept

The overall idea can be summarized as:

```text
You
 ↓
Agent Partner
 ↓
Orchestrator
 ↓
Specialized Agents
 ├── Architect
 ├── UX/UI
 ├── Frontend
 ├── Backend JS
 ├── Backend PHP
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
* The Orchestrator coordinates the whole system.
