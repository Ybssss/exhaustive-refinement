# Global Instructions

## Git Commits

- NEVER add `Co-Authored-By: Claude` or any `Co-Authored-By` trailer to commit messages.
- NEVER add `Generated with Claude Code` or `🤖` footers to commits or PR bodies.
- Commit messages should contain only the user's content — no attribution to Claude.

Before ANY work started, including questions, reviews and small edits:

1. Read `PROGRESS.md`: the "Latest state" block, section 0 (standing rules) and 0.1, section 1
   (snapshot), then the newest entries of section 5. Search the rest for the topic you will touch.
2. Verify any claim you rely on at its source. Section 6 lists claims known to be stale.
3. Do the work. Stay in scope; put unrelated findings in section 4 of `PROGRESS.md`.
4. Before you report done: add a section 5 entry (newest first), refresh "Latest state", add decisions
   to section 2, and say in your reply what is verified and what is not.
5. Never commit, push, publish, deploy or touch a real/shared environment without the owner's explicit
   approval for that specific action.

If `PROGRESS.md` is missing, copy it from the template and fill sections 1 and 0.1 first.

For an exhaustive walk-through / fix loop on any target, use the `exhaustive-refinement` skill.
