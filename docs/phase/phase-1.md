# Phase 1: GitHub Projects Development Dashboard

Status: planned
Date: 2026-10-10

## Goal

Establish Textus Development Center as a development-management subsystem using GitHub Projects/Issues/Pull Requests as the initial system of record.

Deliver a useful read-oriented Human-in-the-Loop dashboard without introducing a parallel issue database or coupling the product to live AI execution.

## Scope

1. Define GitHub Project/Issue/PR adapter boundaries and stable internal projection types.
2. Read one or more configured GitHub Projects and related Issue/PR state.
3. Present repository/project summaries and development status.
4. Present a Needs Human Attention view from explicit Project fields/statuses and admitted finding metadata.
5. Present Issue/PR detail links back to GitHub as the authoritative editing surface.
6. Keep the initial dashboard read-oriented; mutations remain GitHub-owned unless a later phase defines a bounded action contract.
7. Define stable reference points for later composition with sm-workflow and Textus Orchestrator execution state.

## Non-goals

- replacing GitHub Projects;
- creating a second Issue/PR/work database;
- embedding GitHub-specific concepts in Textus Control Center;
- making Textus Orchestrator the Issue tracker;
- copying all sm-workflow execution state into GitHub;
- autonomous AI triage/repair;
- broad KPI/observability analytics better suited to observability tooling.

## Acceptance direction

Phase 1 is useful when a developer can open Development Center and quickly answer:

- what development work is open;
- what needs human attention;
- what Issues/PRs are ready, blocked, or under review;
- which repository/project owns the work;
- where to open the authoritative GitHub item.

Live AI/sm-workflow execution composition is deferred to a later phase.
