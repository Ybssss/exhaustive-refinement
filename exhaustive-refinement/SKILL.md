---
name: exhaustive-refinement
description: Run a complete walk -> record -> fix -> re-walk loop on any target (software system, document set, process, dataset, study, physical procedure) until two consecutive full passes find nothing. Use when the user asks for an exhaustive or very detailed walkthrough, "loop until nothing found", fuzz/security/reverse-flow/cross-part testing, or a pre-release sweep. Maintains PROGRESS.md and never publishes until the loop ends.
---

# Exhaustive Refinement

A loop: **walk everything -> record findings -> fix in batches -> walk everything again**, until a
complete, fully reported pass finds nothing. The walk is the product. Fixing is a separate phase.

"Target" below means whatever is being refined: an application, a set of documents, a procedure, a
dataset, a study, a physical process. "Walk" means using or reading it the way its real users would,
through every function, path and state. Domain wording for each lens is in `lenses.md` (same folder);
read it when you build the matrix.

## Step 0 - Orient (always, first)

1. Read `PROGRESS.md` (Latest state, section 0, 0.1, 1, newest section 5 entries). Obey its rules; they
   override this skill. If it does not exist, create it from the template first.
2. Set section 8 (Loop state): loop number, build/version under test, matrix location.
3. Confirm the **safe place to walk**: a copy, test or staging environment, sample or seeded data. Never
   walk on the real/production target, never enter real credentials or personal data, never send
   anything outward. If no safe place exists, stop and ask.

## Hard rules

1. **No fixing mid-walk.** Record findings (id, lens, where, steps, expected, actual, severity,
   evidence). Fix afterwards. Interrupting a walk breaks its coverage.
2. **No publishing during the loop**: no push, release, deploy, send, or reseed of shared environments.
   Apply fixes locally. Publish once, after the loop is declared done, and only with the owner's
   approval. Then the next loop starts on the published build.
3. **Any finding in a pass starts another loop**, however many fixes the previous loop made.
4. **Done = two consecutive clean full passes**, each with a complete coverage report.
5. **Walk like a real user, through the real interface** (browser, the document as read/printed, the
   form as filled, the equipment as operated), not only through back doors. Back doors (API, database,
   files) are for setup, probing and invariant checks.
6. **Decide small things, ask about big ones.** Small reversible choices: decide, note, continue.
   Policy, irreversible or outward-facing choices: collect in `PROGRESS.md` section 4 and ask at the
   end of the loop.

## Step 1 - Build the coverage matrix (once per target, extend every loop)

- List every **part** (module, chapter, stage, screen, document, table, step, role) and under it every
  **action or state** (create, change, submit, approve, reject, cancel, undo, print, export, search,
  scan, read, cite, hand over...). One row each, with an id. Owner-requested items get their own rows.
- Write the **spine**: the main end-to-end path of the target, crossing its parts.
- Prepare **data**: a normal seeded set and a deliberately messy set (lens 4).
- Source the list from the target itself, not from memory: menus, routes, table of contents, permission
  lists, schema, the procedure's own steps, the requirements, and the previous loop's findings.
- Store it as files under a scratch folder; record the path in section 8.

## Step 2 - The pass: eight lenses, all of them every pass

1. **Forward flow.** The spine start to end, using every function once.
2. **Reverse flows and reverse chain.** For each forward action: how is it taken back, and what state
   does everything downstream end in? Then walk the whole chain backwards, last step to first, checking
   that quantities, statuses and records agree at each step. Include privileged retreat paths (can an
   administrator or owner reverse it, with a reason, and is that recorded).
3. **Cross-part consistency.** Change something in part A, look at B. Facts shown in two places must
   agree. Hand-offs between parts (units, names, counts, states) must survive.
4. **Awkward and fuzzy input.** Empty, zero, negative, huge, fractional, very long, unusual characters
   and scripts, markup and quotes, leading/trailing spaces, duplicates, wrong order, impossible dates,
   numbers that do not add up, things that do not exist. Entered **and confirmed**, not just typed.
5. **Mistake-proofing.** Wrong number, wrong batch, wrong item, wrong order of steps, double submit,
   going back, interruption half-way, two people at once. Each must be refused with a clear message or
   be reversible with a reason.
6. **Machine and sensor behaviour.** Anything that feeds the target automatically: scanners, imports,
   integrations, sensors, scripts, copy-paste. Rapid input, trailing control characters, unknown,
   used, withdrawn or wrong-state codes, same input twice, right input in the wrong place.
7. **Security, permission and abuse.** Each role in the interface and by direct access; guessing
   identifiers; skipping steps; editing locked things; reading others' data; actions that require a
   reason done without one; unauthenticated access; leaked sensitive data in outputs and logs.
8. **Hidden problems and ease of use.**
   - Hidden: logs, console, failed requests, silent errors, audit completeness, invariants (totals
     agree, nothing orphaned, nothing negative, status matches parts), stale or contradictory content.
   - Ease of use: where would a newcomer be stuck (unclear label or term, tiny list, exact typing
     needed, no way back, jargon, no visible next step)? Log as findings of type usability.

Finish every pass with the **gap hunt**: compare the matrix against the target's real surface (menus,
routes, contents, schema, permission list, requirements) and against what other lenses suggest ("what
else could go wrong that no row covers?"). Add rows. Anything still unwalked is reported as
**not tested + reason**, never skipped silently.

## Running a pass

- Large targets: split by part group into parallel walkers (subagents), each with an id prefix (W1-,
  W2-...) and the same report format; then a cross-part walker and a reverse-chain walker.
- Findings format: `id | lens | build | where | steps | expected | actual | severity (blocker / major /
  minor / usability) | evidence`.
- Coverage report: every matrix row marked **pass / finding / not tested (reason)**, with counts at the
  top. A pass with unexplained blanks is incomplete and cannot count as clean.
- If a blocker stops the walk, note it, work around it, continue. Do not fix it now.

## Step 3 - Fix phase

- Group findings into slices by area. For each: reproduce first (a failing test, a recorded example,
  a before-state), then fix at the narrowest layer that addresses the cause, then show it passes.
- When a rule changes, search every place that depends on it. No fix may create a new contradiction.
- Check each slice with the project's own checks (section 7 of `PROGRESS.md`), including a secret/
  sensitive-data sweep. Record the slice in section 5 with its decision numbers.
- Integrate slices locally. Never publish (rule 2).

## Step 4 - Re-walk

1. Re-run the previous findings' reproductions (regression).
2. Run a **full new pass** (all lenses, new gap hunt). Not a partial one.
3. Anything found -> Step 3 -> another full pass.
4. Two consecutive clean full passes with complete coverage -> run the full health checks, update
   section 7, ask the owner to approve publishing, publish once, confirm the published build is the one
   that was walked.

## Keeping PROGRESS.md (during the whole loop)

- Section 8 is updated at the start and end of every pass (rows pass/finding/not tested, open
  findings, decisions pending).
- Each fix slice and each completed pass gets a section 5 entry, newest first, numbered at insert time.
- Decisions go to section 2, owner questions to section 4, discovered stale claims to section 6.
- At loop end: clear section 8 back to "none", refresh "Latest state".

## Report at the end of each loop

Build tested; rows pass / finding / not tested; findings by severity and what was fixed; what is open
and why; owner decisions needed; new rows from the gap hunt; whether another loop starts (it does,
unless two clean passes were reached).
