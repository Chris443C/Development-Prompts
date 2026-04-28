# Project443 Prompt Generators

This pack contains reusable prompt-generator templates for turning a roadmap, backlog, or milestone document into a full autonomous implementation prompt for coding agents.

The templates are tuned for the Project443-DigitalTwin delivery pattern:

- one milestone at a time
- focused tests before full tests
- full `python -m pytest` before commit
- commit and push after every milestone
- mandatory security review gates
- strict continuation rules so the agent does not stop after one or two milestones
- preservation of security controls, workspace isolation, redaction, and production-safe behaviour

## Included Files

| File | Purpose |
|---|---|
| `prompt-generator-codex-autonomous-milestones.md` | Generates Codex-ready implementation prompts from milestone/roadmap documents. |
| `prompt-generator-claude-autonomous-milestones.md` | Generates Claude Code-ready implementation prompts with stronger continuation wording. |
| `prompt-generator-gemini-autonomous-milestones.md` | Generates Gemini CLI-ready implementation prompts with stricter traceability and exact extraction rules. |
| `README.md` | This file. |
| `README-prompt-generator-usage.md` | Short usage examples for each coding agent. |

## Recommended Location

Copy this folder to:

```text
C:\dev\Project443-DigitalTwin\prompt-library
```

Suggested final structure:

```text
C:\dev\Project443-DigitalTwin\prompt-library\
  README.md
  README-prompt-generator-usage.md
  prompt-generator-codex-autonomous-milestones.md
  prompt-generator-claude-autonomous-milestones.md
  prompt-generator-gemini-autonomous-milestones.md
```

## When to Use These

Use these prompt generators when you have a document such as:

- a milestone roadmap
- a backlog converted into milestones
- a security remediation plan
- a connector implementation plan
- a semantic retrieval or embedding roadmap
- a production-hardening plan

The prompt generator will convert that document into a complete implementation prompt for Codex, Claude Code, or Gemini CLI.

## Basic Workflow

1. Prepare a roadmap or milestone document.
2. Open the relevant prompt-generator file.
3. Paste the roadmap and the prompt-generator into ChatGPT, Claude, Gemini, or your preferred assistant.
4. Ask it to generate the final implementation prompt.
5. Copy the generated implementation prompt into Codex, Claude Code, or Gemini CLI.

## Codex Usage

```text
Using the attached roadmap document, create an autonomous Codex implementation prompt.

Follow this prompt-generator format:

<paste contents of prompt-generator-codex-autonomous-milestones.md here>
```

## Claude Code Usage

```text
Using the attached roadmap document, create an autonomous Claude Code implementation prompt.

Follow this prompt-generator format:

<paste contents of prompt-generator-claude-autonomous-milestones.md here>
```

## Gemini CLI Usage

```text
Using the attached roadmap document, create an autonomous Gemini CLI implementation prompt.

Follow this prompt-generator format:

<paste contents of prompt-generator-gemini-autonomous-milestones.md here>
```

## Output Expectations

The generated implementation prompt should:

- preserve exact milestone numbers and names
- preserve backlog/source IDs
- preserve dependencies and out-of-scope statements
- include all deliverables and acceptance criteria
- include security controls from the source document
- include focused test expectations
- include full-suite test gates
- include commit and push requirements
- include mandatory security review gates
- tell the agent to continue automatically after each milestone unless a stop condition is met

## Standard Project443-DigitalTwin Assumptions

Unless the roadmap says otherwise, generated prompts should assume:

```text
Working directory:
C:\dev\Project443-DigitalTwin\digital-twin-starter

Do not make changes in:
C:\dev\Project443-DigitalTwin\Transcripty
```

For Transcripty-specific work, override the working directory and repository boundary in the generated prompt.

## Security Baseline

Generated prompts should preserve these controls unless the source document explicitly requires stricter controls:

- explicit authentication and authorization on all new non-health routes
- workspace_id isolation for all workspace-scoped data
- no fail-open production auth
- no plaintext secrets in code, logs, test fixtures, audit records, status responses, or documentation examples
- redaction of API keys, tokens, webhook URLs, connector secrets, model gateway internals, filesystem paths, and sensitive operational data
- safe startup/config validation
- AI review, confidence, provenance, and writeback governance
- security review gates after milestone batches

## Notes

These files do not implement code directly. They generate the implementation prompts that are then given to Codex, Claude Code, or Gemini CLI.

Keep these templates under version control so changes to your delivery pattern can be tracked.
