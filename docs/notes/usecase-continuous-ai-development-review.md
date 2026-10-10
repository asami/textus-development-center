# Use Case: Continuous AI Development Review

Status: primary use case
Date: 2026-10-10

## Goal

Exploit low-cost or subscription-included long-running AI capacity as a continuous software-quality sensor.

A Dot or another admitted semantic-review provider may spend long periods reviewing repositories, specifications, phases, tests, architecture and recent changes. Its purpose is primarily to discover and explain development work, not to autonomously rewrite the codebase.

The value proposition becomes especially strong when the marginal cost of the review loop is effectively included in a subscription or is low enough to dedicate one reviewer per project/repository.

## Basic loop

~~~text
                 continuous / low-cost
                         |
                         v
                    AI reviewer
                  (Dot initially)
                 /       |       \
            review    discovery   proposal
                 \       |       /
                         v
                  GitHub Issue / PR
                         |
                         v
                   GitHub Projects
                 development work SoR
                         |
                         v
              Textus Development Center
                 Human Attention Inbox
                         |
                 human selects action
                  /              \
              dismiss/hold      develop/review
                                      |
                                      v
                              Codex / sm-workflow
                                      |
                                      v
                              test/review/admission
                                      |
                                      v
                               Issue / PR update
~~~

## Review subjects

Continuous review can rotate through concerns rather than repeatedly ask one generic question. Examples include:

- excessive defensive checks and overengineering;
- Failure Model / Execution Model mismatch;
- architecture and responsibility drift;
- implementation/specification/phase mismatch;
- test architecture and missing validation;
- duplicated or obsolete mechanisms;
- Component KPI anomalies;
- documentation drift;
- technical-debt and simplification candidates.

cbd-support Review should provide structured review concerns, evidence and component context where appropriate. The reviewer is a semantic sensor, not an alternate authority.

## Finding publication

A review result should not automatically mutate implementation.

A sufficiently actionable finding may be published as:

- GitHub Issue when work/problem is identified but implementation should be selected later;
- GitHub Pull Request when an explicitly admitted review mode is allowed to produce a bounded concrete proposal.

Both become normal GitHub Project work and enter the Development Center human-attention surface.

The system should avoid flooding GitHub with low-confidence or duplicate observations. Provider output may be consolidated/triaged before durable publication according to an explicit policy. Human judgment remains available before implementation work is accepted.

## Development Center action

Development Center presents each Issue/PR with enough context to decide what to do.

Initial actions may include:

- open authoritative GitHub item;
- dismiss/hold/triage through GitHub-managed state;
- generate a Codex development handoff;
- generate an independent-review handoff for an existing PR.

The first Codex integration can deliberately remain simple: generate a bounded handoff that the developer copies into Codex Console.

A handoff should identify at least:

- repository;
- GitHub Issue/PR identity;
- goal/problem statement;
- relevant finding/review evidence;
- acceptance criteria;
- related phase/specification/context references;
- instruction to use the project's normal sm-workflow development process when applicable.

This manual handoff preserves Human-in-the-Loop and avoids premature Codex API/session coupling.

Later, the same logical Development Work Request may be dispatched through Textus Orchestrator to sm-workflow/Codex without changing the Development Center user model.

## Role separation

The intended specialization is:

- continuous reviewer (Dot/local semantic reviewer): inexpensive discovery/review;
- GitHub Projects: durable development-work system of record;
- Development Center: human attention, triage and development actions;
- cbd-support: quality evidence, CAR lint and semantic Review concerns;
- sm-workflow: selected work implementation/review/fix/admission;
- Codex: implementation worker;
- Textus Orchestrator: provider-neutral execution/routing when automated dispatch is desired.

This use case must not turn the continuous reviewer into an autonomous source-code authority.

## Cost hypothesis

This architecture should explicitly measure whether long-running semantic review is economically useful.

Important observations include:

- useful findings per reviewer/project/time;
- human-accepted finding ratio;
- duplicate/noise rate;
- findings promoted to Issue/PR;
- findings eventually resolved;
- review-provider cost where observable;
- provider DECLINED/escalation behavior.

The hypothesis is that cheap persistent review can move expensive/high-capability execution toward selected actionable work instead of spending that capacity searching for work.

These are evaluation signals, not a single quality score.

## Relationship to local LLM experiments

Local LLMs may participate in the same semantic-sensor pool. The same review corpus can support provider comparison/A-B evaluation. Confirmed findings and rejected false positives are valuable corpus evidence for future provider selection and review-quality evaluation.
