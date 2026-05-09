# Sample Audit Report

This is a fictional sample. It demonstrates the delivery format, not a real customer project.

Project: TaskLite
Date: 2026-05-10
Reviewer: Eclair Studio / Codex-assisted review

## Summary

Readiness score: 14 / 25

TaskLite is understandable after reading the repository, but an AI coding agent would likely waste time discovering setup commands and may edit too broadly because the repo lacks agent-specific boundaries. The highest-impact fixes are a short `AGENTS.md`, a reliable command map, and issue templates with acceptance criteria.

## Top Findings

| Priority | Finding | Why It Matters | Recommended Fix |
| --- | --- | --- | --- |
| P1 | No documented test command | Agents cannot verify changes and may overstate confidence. | Add `npm test` or the correct test command to README and `AGENTS.md`. |
| P1 | No do-not-touch guidance | Agents may refactor generated files or unrelated modules. | Add protected folders and out-of-scope rules. |
| P2 | Issue descriptions are outcome-light | Agents receive symptoms without acceptance criteria. | Use a structured issue template. |
| P2 | UI verification route is missing | UI changes cannot be visually checked. | Document target route and viewport. |
| P3 | Completion reports are inconsistent | Reviewers cannot quickly see what changed. | Require files changed, tests run, and residual risks. |

## Command Map

| Purpose | Command | Confidence | Notes |
| --- | --- | --- | --- |
| Install | `npm install` | Medium | Inferred from `package-lock.json`. |
| Run | `npm run dev` | Medium | Inferred from package scripts. |
| Test | Unknown | Low | No obvious test script found in sample. |
| Lint | `npm run lint` | Medium | Inferred from package scripts. |
| Format | Unknown | Low | No formatter script documented. |

## Recommended AGENTS.md

```md
# Repository Instructions

## Project Overview

TaskLite is a small task management web app. Prefer small, focused changes and follow existing component patterns.

## Setup

Run `npm install` before local development.

## Common Commands

- Start dev server: `npm run dev`
- Lint: `npm run lint`
- Tests: not documented yet; if no test command exists, say so in the final report.

## Code Style

- Keep UI changes scoped to the relevant component.
- Do not rename public routes unless explicitly requested.
- Avoid broad refactors while fixing a single bug.

## Files And Folders To Avoid

- Do not edit generated build output.
- Do not change lockfiles unless dependencies are intentionally updated.

## Completion Report Requirements

Report changed files, tests run, tests not run and why, and remaining risks.
```

## Agent-Ready Request Template

```text
Please fix the task creation form so the submit button stays disabled when the title is empty.

Context:
- Project: TaskLite, a task management web app.
- Relevant route: /tasks/new
- Relevant files: form components under src/components or src/app/tasks.
- Do not change: routing, database schema, package dependencies.

Acceptance criteria:
- Empty or whitespace-only title cannot be submitted.
- Non-empty title can still be submitted.
- Existing styling remains consistent.

Verification:
- Run lint if available.
- Manually inspect /tasks/new in a desktop viewport.

Report:
- Files changed
- Tests run
- Tests not run and why
- Remaining risks
```

## Suggested Next Task

Add a repository-level `AGENTS.md` and a GitHub issue template before assigning larger implementation work to an AI coding agent.
