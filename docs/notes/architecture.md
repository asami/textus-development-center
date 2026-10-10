# Textus Development Center Architecture

Status: initial architecture
Date: 2026-10-10

## Purpose

Textus Development Center is the Human-in-the-Loop management surface for AI-assisted software development.

It is deliberately separate from Textus Control Center. Control Center manages operational/runtime concerns for business and Textus Subsystems; Development Center manages software-development work.

The two products may share Textus/CNCF UI and application infrastructure, but they do not share one management domain merely because both present dashboards.

## System of record

GitHub is the initial development-work backend.

GitHub Projects, Issues, and Pull Requests remain authoritative for durable development work such as:

- repository/project work;
- issues and findings selected for tracking;
- pull requests;
- development status and priority;
- human triage/decision state.

Development Center MUST NOT create a parallel issue/work database merely to build its dashboard.

Conceptually:

~~~text
GitHub
  Repository
  Issue
  Pull Request
  Projects / fields
        |
        v
Textus Development Center
  Dashboard
  Human Attention
  AI Findings
  PR / Issue status
  Project / repository views
~~~

## Relationship to execution

Durable development work and live execution are different concerns.

GitHub Projects is not required to become an execution-state store. AI/Workflow execution may be supplied by Textus Orchestrator and owning development subsystems.

~~~text
GitHub Projects                    Textus Orchestrator
  Issue / PR / Work                  execution / routing
        |                                  |
        |                            sm-workflow / AI
        |                                  |
        +---------------+------------------+
                        |
                        v
             Textus Development Center
~~~

Development Center may compose these projections for a human, for example showing a GitHub Issue together with the currently running AI Review or sm-workflow execution. Projection composition does not transfer authority between the source systems.

## Relationship to Textus Orchestrator

Textus Orchestrator remains one shared orchestration infrastructure rather than being split into operational and development variants.

Its concern is participant/capability execution: routing, dispatch, continuation, escalation, provider execution and correlation. It must not become the development issue tracker merely because it can execute development work.

A Development Center action such as "review this issue", "start sm-workflow repair", or "escalate review" may request execution through Textus Orchestrator. The durable Issue/PR remains GitHub-owned and the development Workflow remains sm-workflow-owned.

## Relationship to Textus Control Center

The products have intentionally different domains.

Textus Control Center:
- Textus/business runtime operations;
- launcher-managed Subsystem inventory and lifecycle;
- runtime health and operational state;
- operational Human-in-the-Loop.

Textus Development Center:
- repositories, Projects, Issues and Pull Requests;
- development findings and review;
- development workflow progress;
- AI-assisted development Human-in-the-Loop;
- software-quality/development attention.

The architectural principle is:

> Shared platform and UI infrastructure do not imply a shared management domain.

Control Center may be used for business-system operation, so development-specific GitHub/PR/Issue concepts MUST NOT be pushed into its core model.

## Related development subsystems

- sm-workflow owns software-development Workflow semantics, Candidate progression, implementation/review/fix/admission and development execution history.
- cbd-support owns CAR lint and CAR Review, including AI-assisted semantic quality findings.
- Textus Orchestrator owns cross-provider participant/capability orchestration.
- Dots, Codex, local LLMs and other AI engines are execution/review participants, not the durable development-work authority.

## Initial dashboard

The first useful product slice should remain small and read-oriented:

- GitHub Project summary;
- repositories/projects in scope;
- open Issues and Pull Requests;
- status/priority/severity where defined by the Project;
- Needs Human Attention;
- AI/review findings represented by tracked GitHub work;
- blocked/escalated/ready-for-review views where those states are represented.

Later slices may compose live sm-workflow/Textus Orchestrator execution status and provide bounded actions.

## Development-operation model

A useful long-term separation is:

~~~text
Work plane
  GitHub Projects / Issues / PR

Execution plane
  Textus Orchestrator
  sm-workflow
  AI providers

Quality plane
  cbd-support CAR lint / Review

Human interaction plane
  Textus Development Center
~~~

These planes cooperate through typed identities/references and projections. They should not be collapsed into one database or one authority.
