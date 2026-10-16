---
Type:      text/vnd.ase.task
Id:        ase-start
Created:   2026-10-16 21:04
Modified:  2026-10-16 21:04
Group:     ase-rollout
After:     ase-scope
Status:    CLOSED
Kind:      CRAFTING
Tags:      rules, rollout
---

#   TASK: Session start reads ASE files, every task

##  SPECIFICATION (WHAT)

-   [ ] DOM: **Repo**: Work package of epic `ase-rollout` for *this repository*; the central change
    (`ase-scope`) is already on `dotfiles` `main`.

-   [ ] DOM: **Session start**: The agent rule file gets, right after the step that reads `knowledge/`
    (NEXT → plan → decisions → open-questions), a step: read `~/.claude/workflows/ase-workflow.md`,
    `ase-skills.md`, `ase-rezepte.md` (lead additionally `ase-orchestrierung.md`) before planning or
    working — for *every task*, research and other knowledge work included, and in *every delegated
    worker*.

-   [ ] DOM: **Code-only wording**: If the file's ASE section limits ASE to code ("code task", "when coding",
    "bei Code", "Code-Aufgabe"), widen that statement to every task.

-   [ ] IFC: **Rule file**: `AGENTS.md`; `CLAUDE.md` only if it is a real file, not a symlink to
    `AGENTS.md`. Without a session-start section, the step becomes the first bullet of the ASE section.

##  DESIGN (HOW)

-   [ ] IMP: **Edit**: Keep the file's language and structure; renumber following steps if numbered;
    pointer only, no copied procedure text; no other edits.

-   [ ] IMP: **Findings**: Anything outside this scope goes into the report, not into the change.

-   [ ] IMP: **Report**: `knowledge/reviews/<YYYY-MM-DD>-report-ase-start.md` if the repo has
    `knowledge/reviews/`, else the handoff path named in the briefing; the worker does not stage, commit or
    push.

##  VERIFICATION (WHEN)

-   [ ] REG: **Diff**: `git diff --check` exits 0; `git diff --name-only main` plus untracked files list only
    the rule file(s) and the report file.

-   [ ] REG: **Refs**: `python3 ~/.claude/workflows/bin/ase-refs-check.py --projects ~/coding` does not list
    this repository in ABWEICHUNG lines.

-   [ ] CON: **Step present**: `grep -n "ase-rezepte.md"` on the rule file hits inside the session-start
    section (or the ASE section if none exists).

-   [ ] CON: **Review**: Work-piece review by GPT-6-Astra (xhigh) passes.

