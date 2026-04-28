# Prompt Generator - Claude Code Autonomous Milestones

```text
Create an autonomous Claude Code implementation prompt from the supplied milestone or roadmap document.

Purpose:

Convert the supplied roadmap/milestone/backlog document into a complete Claude Code-ready implementation prompt using the Project443-DigitalTwin delivery pattern:

- work one milestone at a time
- preserve existing security controls
- run focused tests
- run full test suite
- commit and push after each milestone
- continue automatically unless a defined stop condition is met
- include mandatory security review gates where appropriate
- include exact milestone-specific requirements from the supplied document
- do not treat a summary as the end of the task

Input document:

Use the supplied milestone or roadmap document as the source of truth.

Do not invent milestones.
Do not omit milestones.
Do not merge milestones.
Do not weaken security, testing, documentation, or acceptance criteria.
Do not ask follow-up questions unless the document is too ambiguous to produce a safe implementation prompt.

Output required:

Produce one complete copy/paste-ready prompt for Claude Code.

The generated prompt must include these sections:

1. Opening instruction

Use this style:

Continue Project443-DigitalTwin <roadmap theme> milestone delivery autonomously.

2. Working directory

Use this unless the input document specifies otherwise:

C:\dev\Project443-DigitalTwin\digital-twin-starter

3. Scope boundary

Include:

This is Project443-DigitalTwin work.

Do not make changes in:

C:\dev\Project443-DigitalTwin\Transcripty

Do all work only in:

C:\dev\Project443-DigitalTwin\digital-twin-starter

4. Primary objective

Summarise the purpose of the supplied milestone set.

5. Source of truth

Name the supplied roadmap/milestone document.

6. Milestone order

Extract every milestone exactly as written.

For each milestone include:

- milestone number
- milestone title
- backlog/source ID if present

7. Claude-specific continuation instruction

Include this exact block:

Important Claude Code behaviour instruction:

Do not stop after completing, summarising, committing, or pushing a milestone.

A completion summary is not the end of the task. A completion summary is only a checkpoint before immediately starting the next milestone.

A security review summary is not the end of the task. A security review summary is only a checkpoint before immediately starting the next milestone, provided continuation is approved.

After each successful `git push`, immediately continue with the next milestone or mandatory security review gate without waiting for user input.

Do not wait for user confirmation unless a stop condition is met.

8. Stop conditions

Include:

Stop only if:

1. all milestones in the supplied roadmap are complete
2. a full test suite failure cannot be fixed safely without clarification
3. a requirement is missing or ambiguous enough that implementation would be guesswork
4. git push fails due to remote conflicts or authentication
5. a change would require a major architecture decision outside the roadmap
6. a proposed implementation would weaken completed security controls
7. a security review identifies a Critical or High finding that cannot be fixed safely without clarification

9. Non-stop conditions

Include:

Do not stop merely because:

- one milestone is finished
- two or three milestones are finished
- five milestones are finished
- a security review was completed
- a full test suite passed
- a commit was created
- a push succeeded
- a completion note was written
- the next milestone was selected

Those are continue conditions, not stop conditions.

10. Pre-flight instructions

Include:

- run `git status`
- confirm current working directory
- confirm configured remote
- read the supplied roadmap
- identify the last completed milestone
- identify the next incomplete milestone
- check whether previous committed milestone had a passing full test suite
- run baseline only if previous full-suite status cannot be confirmed

11. No repeated baseline rule

Include:

Do not run another full baseline `python -m pytest` before starting the next milestone if the previous milestone has just completed with a passing full `python -m pytest`.

The passing full suite at the end of one milestone is the baseline for the next milestone.

Only rerun a pre-milestone baseline if:

- the repo was changed externally
- the branch changed
- a pull/merge occurred
- Claude Code restarted and cannot confirm the previous full test result
- the previous milestone did not finish with a passing full suite

12. Operating loop

Include a numbered loop:

1. identify current milestone
2. read full milestone definition
3. implement only that milestone
4. preserve traceability to backlog/source ID
5. add/update code, schemas, services, migrations, routes, UI links, scripts, config, docs, tests as applicable
6. preserve security controls
7. run focused tests
8. fix and retest
9. run full suite once
10. update docs
11. commit and push
12. record checkpoint note
13. immediately continue to next milestone or security review gate

13. Security controls

Include baseline Project443 controls:

- explicit auth on every new non-health route
- mutating routes reject viewer-only users
- admin-only routes reject viewer/operator users
- workspace-scoped data enforces workspace_id
- no secrets, tokens, API keys, webhook URLs, raw payloads, filesystem paths, connector secrets, model internals, note content, or sensitive operational internals are exposed
- no sensitive material is persisted in logs, audit records, connector items, notification records, status responses, health responses, or test output unless redacted
- startup/config validation fails safely
- connector/provider health payloads are redacted
- production-capable settings must not fail open
- AI review, confidence, provenance, and writeback controls remain intact

Add any additional security controls from the supplied document.

14. Focused test guidance

Extract specific tests from the supplied document.

Also include generic tests where relevant:

- regression test for the backlog finding
- happy path
- validation failures
- unauthorized request rejected
- wrong-role request rejected
- correct-role request allowed
- workspace isolation
- migration compatibility
- fresh database bootstrap
- redaction
- error handling
- backwards compatibility

15. Security review gates

If the document specifies review gates, reproduce them exactly.

If the document does not specify review gates, add:

Perform a mandatory security review after every 5 completed milestones and at the final milestone.

Security review output path:

docs/security/security_review_after_milestone_<N>_<YYYY-MM-DD>.md

Include the standard security review structure:

- Scope
- Standards Reference
- Executive Summary
- Findings
- Regression Review
- Route and Operation Security Matrix
- Workspace Isolation Review
- Connector / Provider / AI Review where applicable
- Supply Chain / Deployment Review
- Test Evidence
- Recommendations
- Assumptions

16. Milestone-specific requirements

For each milestone in the source document, include a subsection:

Milestone <N> - <Title>

Backlog/source ID: <ID if present>

Implement and verify:

- all deliverables from the source document

Acceptance criteria:

- all acceptance criteria from the source document

Security controls:

- all milestone-specific controls from the source document

Dependencies or out-of-scope items:

- include if present

17. Commit pattern

Include:

git status
git add .
git commit -m "Add Milestone <N> <short milestone name>" -m "<Detailed summary of what was added, including backlog/source ID, code changes, tests, workspace_id handling, security controls, compatibility fixes, and documentation updates.>"
git push

18. General rules

Include:

- work strictly one milestone at a time
- do not batch multiple milestones into one commit
- do not batch a security review into a feature milestone commit
- do not skip focused tests
- do not skip full suite
- do not rewrite old tests to hide broken implementation
- keep repo green and pushed after every milestone
- include the git commit/push command after every build milestone response

19. Specific first task

Start with the first incomplete milestone from the supplied document.

Include that milestone’s deliverables explicitly.

20. Begin now

End with:

Begin now with Milestone <N>.

Output format:

- Output only the final generated Claude Code prompt.
- Use a single fenced text block.
- Make it copy/paste ready.
- Preserve exact milestone numbering and names.
- Include all acceptance criteria and security controls from the source document.
```
