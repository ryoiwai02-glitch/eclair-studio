# AI Agent Readiness Checklist

A practical checklist for making software repositories easier to hand off to AI coding agents.

Works with workflows around Codex, Cursor, Claude Code, GitHub Copilot coding agent, and similar tools.

This is an independent resource. It is not affiliated with or endorsed by OpenAI, Anthropic, Cursor, GitHub, or any other tool vendor.

## Why This Exists

AI coding agents are more useful when the repository gives them clear context, commands, boundaries, and verification paths.

Many failed agent sessions are not caused by the model alone. They come from missing setup instructions, vague issue descriptions, unknown test commands, unclear ownership boundaries, and weak completion reporting.

This checklist helps you fix those handoff problems before asking an agent to change code.

## Quick Checklist

### Repository Context

- [ ] The repository has a one-paragraph description.
- [ ] The main language, framework, and package manager are obvious.
- [ ] The app entry point is documented.
- [ ] Generated, build, vendor, or asset folders are named.
- [ ] The agent knows what not to touch.

### Commands

- [ ] Install command is documented.
- [ ] Dev server command is documented.
- [ ] Test command is documented.
- [ ] Lint/format commands are documented.
- [ ] Required environment variables are listed without secrets.

### Task Boundaries

- [ ] The request describes the desired outcome.
- [ ] Relevant files, routes, commands, or endpoints are named when known.
- [ ] Acceptance criteria are included.
- [ ] Out-of-scope changes are named.
- [ ] Existing behavior that must be preserved is named.

### Verification

- [ ] There is at least one command the agent can run.
- [ ] UI work includes a route and viewport to inspect.
- [ ] API work includes a sample request or fixture.
- [ ] Bug reports include reproduction steps.
- [ ] Data changes include a rollback or backup note.

### Completion Report

- [ ] The agent reports changed files.
- [ ] The agent reports tests run.
- [ ] The agent reports tests not run and why.
- [ ] The agent reports remaining risks.
- [ ] The agent avoids unrelated refactors.

## Scoring

- 21 to 25: Strong handoff readiness
- 16 to 20: Good, but sessions may still drift
- 10 to 15: Expect repeated clarification and rework
- 0 to 9: Prepare the repo before assigning agent work

## Copy/Paste Agent Request

```text
Please inspect this repository and complete the requested task with a minimal, well-scoped change.

Project context:
- Purpose:
- Stack:
- Relevant folders:
- Do not touch:

Task:
- Desired outcome:
- Relevant files/routes/commands:
- Acceptance criteria:

Verification:
- Install command:
- Test command:
- Manual check:

Report back with:
- Files changed
- Tests run
- Tests not run and why
- Remaining risks
```

## Mini-Audit

If you want a repo-specific version of this checklist, the paid Mini-Audit delivers:

- Readiness score
- Top blockers
- Repo-specific `AGENTS.md` draft
- Command map
- Agent-ready issue/request templates
- Completion-report template

V1 is public-repository-only. Do not send secrets, API keys, passwords, production credentials, customer data, private identity documents, private repositories, private ZIPs, or unreleased proprietary material.

If sensitive information was sent by mistake, rotate or revoke active secrets on your side and resend only the public repository URL and non-sensitive context.
