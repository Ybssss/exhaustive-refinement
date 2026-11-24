# Lenses by kind of target

Use the column that fits; mix columns for mixed targets. Each cell is a prompt, not a checklist: turn
it into matrix rows for this target.

| Lens | Software / web app | Documents / content set | Process / procedure | Dataset / pipeline | Study / analysis | Physical / equipment |
| ---- | ------------------ | ----------------------- | ------------------- | ------------------ | ---------------- | -------------------- |
| 1 Forward flow | Every screen, button, tab, filter, print, export, status change along the main journey | Read start to end as the intended reader, follow every reference, link and figure | Do every step in order, as written, with the stated inputs | Run source to sink with a normal batch | Follow the method exactly as written | Operate through a full normal cycle |
| 2 Reverse and chain | Cancel, void, return, undo, step back, re-open; unwind last document to first, check stock/status | Remove or change a source; what else must change? Withdraw a version | Abort at each step; what state is left? Rework, re-do, rollback | Rerun, backfill, delete a batch, restore; are outputs consistent after | Retract a finding; do conclusions depending on it fall? | Stop mid-cycle, safe state, restart, reverse a setting |
| 3 Cross-part | Same fact on two screens; hand-offs between modules; totals and counts | Same term, number, name, date across chapters; contradicting statements | Hand-offs between roles/stations; who holds what | Joins, keys, units, time zones across tables and stages | Numbers in text, tables, figures and conclusions agree | Interlocks between machines, shared utilities, handovers |
| 4 Awkward input | Empty, zero, huge, unicode, markup, duplicates, impossible dates, nonexistent ids | Missing sections, broken links, odd characters, very long entries, wrong language | Out-of-range inputs, partial materials, wrong sequence of inputs | Nulls, duplicates, malformed rows, late or out-of-order data, huge volume, schema drift | Outliers, missing data, tiny samples, ties | Out-of-spec material, extreme settings, power loss |
| 5 Mistake-proofing | Wrong number/batch/item entered and confirmed, double submit, two tabs, interruption | Misread instructions, ambiguous wording that can be taken two ways | Skipped or swapped steps, wrong tool/material, unclear who acts | Wrong file, wrong period, rerun twice | Wrong parameter, wrong dataset version, uncontrolled change | Wrong part fitted, control confused, guard bypassed |
| 6 Machine input | Scanners, imports, integrations, copy-paste, offline queue | Pasted text, converted formats, automated generation | Barcode, label and reader behaviour at stations | Feeds, APIs, retries, duplicate delivery, partial delivery | Instrument exports, scripts, imports | Sensors, readers, controllers, noise, drift |
| 7 Security / permission | Roles in UI and direct API; id tampering; skipped steps; locked fields; leaks in outputs and logs | Confidential content in wrong audience, metadata, tracked changes, hidden text | Who may do/approve what; separation of duties; unauthorised shortcuts | Access to raw vs derived data, masking, retention | Data privacy, consent, independence | Physical access, lock-out/tag-out, authorisation to operate |
| 8 Hidden and ease of use | Logs, console, failed calls, audit completeness, invariants, newcomer stuck points | Stale content, duplicated or orphaned sections, unclear wording, missing definitions | Unwritten knowledge, tacit steps, unclear ownership, awkward ergonomics | Silent drops, skew, unmonitored failures, undocumented fields | Hidden assumptions, undocumented exclusions | Wear, ergonomics, unlabelled hazards, fragile settings |

## Always check, whatever the target

- Is every claim of "done / verified" backed by something that was actually run or observed?
- Is there anything the target promises (requirements, owner requests, documents) that no row covers?
- Is there anything the target does that nobody asked for and nobody has reviewed?
