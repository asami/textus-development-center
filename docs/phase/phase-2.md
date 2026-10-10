# Phase 2: Development Actions and Codex Handoff

Status: planned
Date: 2026-10-10
Depends on: Phase 1

## Goal

Turn the GitHub Projects dashboard into a Human-in-the-Loop development action surface.

A developer selects an Issue or Pull Request and can form a bounded development/review handoff suitable for starting work in Codex Console, while GitHub remains the development-work system of record.

## Scope

1. Issue/PR action view with authoritative GitHub identity and project context.
2. Generate Codex handoff for Issue implementation/fix work.
3. Generate Codex independent-review/review-fix handoff for Pull Requests.
4. Include repository, goal, evidence, acceptance criteria and relevant phase/spec references.
5. Provide a copy-oriented/manual-console workflow as the first integration boundary.
6. Preserve the GitHub Issue/PR identity through the handoff so later work can report back to the same durable work item.
7. Define a provider-neutral Development Work Request contract suitable for later Textus Orchestrator/sm-workflow dispatch.

## Non-goals

- direct Codex session automation in the first slice;
- autonomous acceptance or merge;
- replacing sm-workflow development semantics;
- copying complete repository content into handoffs;
- making Development Center the source-code editor.

## Future

A later phase may replace manual copy-to-Codex with:

    Development Center
      -> Textus Orchestrator
      -> sm-workflow
      -> Codex worker

without changing the GitHub work identity or the user-facing development action semantics.
