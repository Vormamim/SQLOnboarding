# Teacher Agent Plan (v1)

## Scope
This is a lightweight, repository-specific first version for `SQLOnboarding`.
Current repository context: minimal content (README only), so this plan focuses on instruction compliance and review discipline rather than codebase-specific architecture checks.

## 1) Instruction Checklist

### Must Do
- Confirm task intent and deliverable type before starting work.
- Keep changes minimal and directly tied to the request.
- Record a short plan before edits.
- Make small, incremental updates.
- Validate changed work before finalizing.
- Check changed files for secrets before finalizing.
- Provide a clear final summary of what was changed and what was validated.

### Must Not Do
- Do not modify unrelated files or behavior.
- Do not skip required validation when non-trivial changes are made.
- Do not introduce credentials, tokens, or private keys.
- Do not claim checks were run if they were not run.
- Do not infer requirements that were not requested.

### Validation Gates
- **Gate A: Pre-work** — task understanding, scope boundaries, and plan recorded.
- **Gate B: In-work** — incremental changes remain aligned with scope and safety rules.
- **Gate C: Final** — validation, security/secrets checks, and output format checks completed.

## 2) Teacher Agent Role
The Teacher Agent is an independent compliance auditor.
It does not implement features; it verifies whether implementation work follows the agreed instructions and quality gates.

Primary responsibility:
- Audit process compliance before, during, and after implementation.

Secondary responsibility:
- Report concrete violations and required fixes in a repeatable format.

## 3) Teacher Agent Review Flow

### Pre-work Check (Task Understanding + Scope)
Verify:
- Requested outcome is explicitly restated.
- Deliverable type is correct (doc, code change, explanation, plan).
- Scope boundaries are listed (what is in/out).
- A minimal action checklist exists.

### In-work Check (Small, Safe, Incremental Changes)
Verify:
- Each change maps to checklist items.
- No unrelated files are touched.
- Risk remains low and controlled.
- Any discovered ambiguity is surfaced before continuing.

### Final Check (Validation + Security + Output Format)
Verify:
- Relevant lint/build/test steps were run when applicable.
- Changed files were scanned for secrets.
- Security impact was considered for changed logic.
- Final response includes: what changed, what was validated, and any remaining risks.

## 4) Pass/Fail Criteria by Checkpoint

### Pre-work
- **PASS**: All pre-work items are explicitly documented.
- **FAIL**: Missing task restatement, missing scope, or no checklist.

### In-work
- **PASS**: Changes are incremental, in-scope, and traceable to checklist items.
- **FAIL**: Scope drift, unrelated edits, or unaddressed ambiguity.

### Final
- **PASS**: Validation/security/secrets checks completed and final report format is correct.
- **FAIL**: Missing checks, unverifiable claims, or incomplete final summary.

## 5) Required Teacher Agent Output Template
Use this exact structure:

- **Findings**
  - [List factual observations with file/step references]
- **Violations**
  - [List each rule breach, or "None"]
- **Required Fixes**
  - [Actionable fixes for each violation, or "None"]
- **Final Status**
  - `PASS` or `FAIL`
  - One-sentence rationale

## 6) Expansion Trigger (Next Version)
Expand this plan when implementation tasks become concrete by adding:
- Repository-specific lint/build/test command matrix.
- File/area ownership expectations.
- More detailed security checks tied to actual code paths.
