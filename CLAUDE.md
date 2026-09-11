# CLAUDE.md — conventions for Claude Code sessions working in this repo

This is a **plain static HTML site** on GitHub Pages. No Jekyll, no build
tooling, no frameworks, no package managers. Publish source is
`main` / root, with `.nojekyll` so GitHub serves the files as-is. The
design goal is "push to main → live" with as few moving parts as possible.

## Non-negotiable rules

1. **Never push directly to main.** Always open a PR. The adult merge click
   is the site's safety gate.
2. **Youth protection:** if photos are ever added — parental permission on
   file, first names only, no identifying details (addresses, plates,
   school names). Flag violations instead of publishing.
3. **Design tokens:** all colors live at the top of `assets/css/style.css`.
   Purple-only palette — no green, ever. Gold (`--gold`) is reserved for the
   fleur-de-lis mark and thin accent rules.
4. **Flat design:** no rounded corners, no drop shadows, no gradients.
   `border-radius: 0` is enforced globally — don't reintroduce any of these.
5. **Fonts:** Georgia (serif) for display/body, system sans for labels and
   nav. No webfonts.
6. **JavaScript:** `assets/js/main.js` (scroll fade-in) is the only script.
   The site must fully work with JS disabled. Don't add more.
7. **Shared chrome:** the header and footer are duplicated across all HTML
   pages (no templating). When changing nav or footer, update every page.
8. **Placeholders:** visible TODOs use `<span class="todo">TODO(dad):
   …</span>`. When Dad provides real info, remove the placeholder entirely
   and update the checklist in README.md.
9. **Calendar:** the Google Calendar embed lives in `index.html` and
   `schedule.html` with `CALENDAR_ID_PLACEHOLDER`. Replace it in both; never
   hardcode a different ID in one place only.
10. **Landing photo:** the home page hero shows `Home.png` when a file of
    that exact name exists at the repo root, and hides automatically when it
    doesn't (see `index.html`, `.hero-photo`). Don't add a different photo
    mechanism.
11. **No eyebrows:** there are no small-caps micro-labels above headings
    anywhere (the `.label` / `.facts` styles are deleted). Don't add them
    back.

## Maintenance guide

All task recipes live in `README.md` — point the human there. Do the task,
open a PR, reference the recipe number in the PR description.
