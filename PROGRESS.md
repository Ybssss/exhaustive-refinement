# PROGRESS — <Project name>

> **READ THIS FIRST, BEFORE ANY WORK.** Read the "Latest state" block and section 0 in full, then the
> newest entries in section 5, then search the rest for the topic you are about to touch. Before you
> rely on a claim, verify it at its source. When you finish, update this file (section 0, rule 3).

## Latest state (<YYYY-MM-DD>)

- **Now:** <what just changed, in one or two lines>
- **Blocked / waiting on owner:** <list, or "nothing">
- **Next:** <the next step, and which sections to read for it>
- **Loop:** <none | loop N, pass N, build/version under test, findings open — see section 8>

---

## 0. Standing rules

Owner instructions, not findings. They apply to every change, whatever the project is.

1. **Read first.** Read this file before any change, not after. A claim here can be stale; section 6
   lists known stale ones. Verify the claim you rely on at its source.
2. **One maintained document.** Do not create a second status/context/notes file. Decisions, glossary
   and progress live here. (Supporting artefacts such as test data or exports may exist; their status
   is recorded here.)
3. **Update it as part of the work.** A change is not complete until this file reflects it:
   a new entry in section 5 (newest first), the "Latest state" block refreshed, new decisions in
   section 2. **Never delete history.** When a claim is overtaken, add a superseding entry and mark the
   old one _superseded by N_.
4. **Ask before anything outward-facing or hard to reverse**: publishing, sending, deploying, deleting,
   spending, committing/pushing, touching a shared or real environment. Approval is per action and does
   not carry over. Decide small reversible things yourself, say what you chose, and keep going.
5. **Report outcomes faithfully.** Write _verified_ only for what you actually ran or observed, and say
   how ("42 tests passed", "opened the page and saw X", "read the source line"). Otherwise write
   _not verified_ and what would verify it. A pass proves only what was exercised.
6. **Stay in scope; list the rest.** Unrelated problems found on the way go to section 4 (Open
   questions / follow-ups), not into the current change.
7. **Keep it modular.** Grow by adding parts, not by growing existing ones. Shared things live in shared
   places; do not copy one into a second place, promote it. If a change needs another part's internals,
   stop and fix the boundary first.
8. **No secrets or personal data in this file** (keys, passwords, tokens, private identifiers). Describe
   them instead. Write "section N", not the section-sign glyph.
9. **Keep this file readable.** When section 5 passes about 400 lines, move the oldest entries to
   `PROGRESS-ARCHIVE.md` (an archive, not a second status file), leave a one-line index entry per
   moved item, and keep the numbering. Never renumber.

### 0.1 Project-specific rules

<Rules only this project has: required tools or skills, design references, language/style, environments
that must never be touched, branching, release steps. Delete this line when filled. Keep each rule one
sentence with its reason.>

---

## 1. Project snapshot

| Item | Value |
| ---- | ----- |
| What it is | <one sentence> |
| Target type | <software system / document set / process or procedure / dataset / research / physical / other> |
| Goal and "done" | <what success looks like, who accepts it> |
| Owner / decider | <who decides> |
| Where it lives | <repo, folder, environments, URLs — never real credentials> |
| How to run / open it | <commands or steps> |
| How to verify it | <commands or steps; see section 7> |
| Off-limits | <real/production environments, real data, anything that must not be touched> |

## 2. Decisions

Settled decisions, numbered. Reversing one means appending a new row, never rewriting. Mark ones the
owner delegated to the agent as _(delegated)_.

| #      | Date | Decision | Why / outcome |
| ------ | ---- | -------- | ------------- |
| **D1** |      |          |               |

## 3. Glossary

| Term | Meaning in this project |
| ---- | ----------------------- |
|      |                         |

## 4. Open questions and follow-ups

| #      | Question or follow-up | Needs | Raised |
| ------ | --------------------- | ----- | ------ |
| **Q1** |                       | owner / agent / external |  |

## 5. Progress log (newest first)

Status: ✅ complete · 🟡 partial · 🔴 blocked or defect · ⏳ planned. Insert new entries at the top, here.
Number at insert time (next free number); never renumber. Short form is fine for small changes.

```
### <status> N: <title> (<YYYY-MM-DD>)
Why: <requirement, finding, or owner instruction, and its source>
Changed: <files / documents / settings / steps, with paths>
Decisions: <D-numbers or none>
Verified: <what was run or observed, with counts - or "not verified" and what would verify it>
Open: <remaining work, owner questions, limits>
Supersedes: <earlier entries or claims, or none>
```

<entries go here>

---

## 6. Known drift and superseded claims

Claims in code comments, older documents or earlier entries that are known to be wrong. Anything
remembered from a superseded source is unverified until re-checked.

| Source | Claim | Reality | Disposition |
| ------ | ----- | ------- | ----------- |
|        |       |         |             |

## 7. Verification baseline

The checks that prove the project is healthy, with the last result. Refresh when you run them.

| Check | How to run | Last result | Date |
| ----- | ---------- | ----------- | ---- |
|       |            |             |      |

## 8. Loop state (only while an exhaustive-refinement loop is running)

| Item | Value |
| ---- | ----- |
| Loop / pass | |
| Build or version under test | |
| Coverage matrix location | |
| Rows: pass / finding / not tested | |
| Open findings (ids, severity) | |
| Owner decisions pending | |
| Push / release allowed? | no, until the loop is declared done |

---

## Appendix A — Lessons carried over

Generic failure modes that cost time before. Check each when matching work comes up. Add new ones.

- "Feature-complete" is not "done": security, deployment, records and handover belong in the definition
  of done, not at the tail.
- Record unverified inferences as inferences and check them before building on them.
- A config baked into a shared artefact points every environment at one place; keep per-environment
  config outside it.
- A health or readiness check shorter than the real start-up time fails on real deploys and passes on
  no-ops. Poll, with a timeout.
- A fix that changes a rule must be re-checked at every place that depends on the rule.
- A pass with unreported areas is not a clean pass; "not tested" must be written, with a reason.
