# CLAUDE.md — conventions for Claude Code sessions working in this repo

This is a GitHub Pages site built with **native Jekyll** (no npm, no build
tooling, no CI workflows). Publish source is `main /root`. Do not introduce
package.json, node_modules, or GitHub Actions deploy workflows — the design
goal is "push to main → live," with as few moving parts as possible.

## Non-negotiable rules

1. **Never push directly to main.** Always open a PR. The adult merge click
   is the site's safety gate.
2. **Youth protection on photos:** verify before opening any photo PR —
   parental permission is on file, captions use first names only, no
   identifying details (addresses, plates, school names). Flag violations
   instead of publishing.
3. **Announcements:** copy `_announcements/_TEMPLATE.md`, rename to
   `YYYY-MM-DD-slug.md` in `_announcements/`, complete the front matter,
   run the checklist inside the template. `_TEMPLATE.md` itself must never
   appear on the site (the underscore prefix is what hides it — don't
   remove it).
4. **Galleries:** a folder under `images/` IS a gallery. No page edits
   needed. Never edit `photos.md` to add one.
5. **Design tokens:** all colors live at the top of `assets/css/troop.css`
   (`--purple`, `--gold`, etc.). Change those, not per-element hex codes.
6. **Calendar:** the single source of truth is `_includes/gcal.html`.
   Replace `CALENDAR_ID_PLACEHOLDER` there once; never hardcode the ID in
   pages.
7. **Placeholders:** visible TODOs use `<span class="todo-inline">TODO(dad):
   …</span>`. When Dad provides real info, remove the placeholder entirely
   and update the checklist in README.md.
8. **Keep it boring:** no JavaScript unless something genuinely requires it;
   no third-party trackers or analytics; no new dependencies.

## Maintenance guide

All task recipes live in `README.md` — point the human there. Do the task,
open a PR, reference the recipe number in the PR description.
