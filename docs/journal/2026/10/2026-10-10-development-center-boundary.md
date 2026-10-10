# Development Center boundary

Date: 2026-10-10
Status: design decision

## Background

The initial discussion considered extending Textus Control Center with GitHub Projects and AI-development dashboards. This would mix two different management domains.

Control Center is intended for operational management, including business-system operation and Textus Subsystem lifecycle/health through textus-launcher/cncf-launcher integration. Software development has different actors, time scales, objects and actions: Repository, Issue, Pull Request, review, fix, merge and development-quality findings.

## Decision

Create Textus Development Center as a separate subsystem.

Use GitHub Projects/Issues/Pull Requests as the initial backend/system of record for durable development work.

Keep Textus Orchestrator unified across operational and development use. It provides generic participant/capability orchestration, while domain authority remains with the owning system.

The resulting separation is:

~~~text
Operations domain                   Development domain

textus-launcher                     GitHub Projects
CNCF/business Subsystems            Issues / PR
       |                                  |
       v                                  v
Textus Control Center           Textus Development Center

             \                    /
              Textus Orchestrator
          shared execution/orchestration
~~~

This diagram indicates shared orchestration capability, not shared domain ownership.

## First use case

A concrete first use case is continuous AI review (for example Dots or another provider) producing review findings that may become GitHub Issues or Pull Requests. Development Center makes the resulting development work and human-attention queue visible.

CAR lint remains cheap/deterministic. Semantic quality and overchecking detection belongs to cbd-support Review. sm-workflow owns implementation/review/fix/admission workflow. Development Center presents the development picture rather than absorbing those responsibilities.

## Future composition

Development Center may later combine:

- GitHub Project/Issue/PR state;
- sm-workflow development Workflow status;
- cbd-support Review findings;
- Textus Orchestrator execution/provider status.

The UI may show these together while retaining separate source-system authority.
