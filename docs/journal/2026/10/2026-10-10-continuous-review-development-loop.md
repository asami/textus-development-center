# Continuous review -> GitHub -> Development Center -> Codex

Date: 2026-10-10
Status: key product use case

A major expected use of Textus Development Center is to make inexpensive, persistent AI review operationally useful.

If a Dot or comparable reviewer can run continuously within a subscription allowance or at a low per-project monthly cost, use it as a 24-hour semantic quality sensor. Let it search for review findings and improvement candidates, publish selected actionable work as GitHub Issues or Pull Requests, and let Development Center become the human inbox for deciding what to do next.

Do not default to autonomous source modification. Discovery and resolution are separate stages.

The initial resolution path can be intentionally simple: Development Center generates a structured handoff from an Issue/PR, and a developer copies it into Codex Console to start the project's normal sm-workflow-guided development process.

This gives a useful path before direct agent/session integration exists:

    cheap persistent discovery
      -> durable GitHub work
      -> human selection
      -> expensive/strong implementation only where useful

Later automation can dispatch the same Development Work Request through Textus Orchestrator without changing the product model.

This use case is considered strategically important because it can turn otherwise idle/low-marginal-cost AI capacity into continuous software-quality improvement while retaining Human-in-the-Loop control.
