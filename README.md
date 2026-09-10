# Troop 2536 Website — Maintenance Guide

This file is the troop website's "control panel." You never need to know how
to code. Every change is one of two things: **say a sentence to Claude Code**
(which edits the files), or **drop a file into a folder**. Then the change
goes through one quick approval before it's live.

**The one rule:** nothing publishes directly. Edits are made on a side
branch, an adult clicks **Merge** in GitHub, and the site updates ~60 seconds
later. That's it.

```
Say it to Claude Code  →  it opens a Pull Request  →  adult clicks Merge  →  live
```

---

## Recipe 1 — Post an announcement

Copy this into Claude Code and edit the parts in CAPS:

```
Open a PR that adds a new announcement titled "TITLE HERE" dated YYYY-MM-DD.
Body: TYPE THE ANNOUNCEMENT TEXT. [Pinned: yes/no].
Use the template in _announcements/_TEMPLATE.md. Check the checklist first.
```

Takes about 2 minutes from sentence to merge-ready.

## Recipe 2 — Update the schedule

You don't edit the schedule in the repo at all. The Schedule page shows the
troop Google Calendar. Add or change the event **in Google Calendar** (phone
app is fine) and the website updates itself. The only reason to touch the
repo for the schedule: changing the placeholder text under "Typical year"
(see Recipe 5).

One-time setup: the calendar embed uses a placeholder ID — see Recipe 7.

## Recipe 3 — Add photo galleries

1. Resize photos to web size (Claude Code does this if you're unsure — just say so).
2. Create a folder: `images/YYYY-MM-event-name/` (example: `images/2026-09-campout/`).
3. Drop the photos in, then tell Claude Code: *"Open a PR adding the photos I placed in images/2026-09-campout/."*

The gallery appears on the Photos page automatically — **no page editing**.
Folder names become gallery titles, newest at the top.

**Photo rules (youth protection — non-negotiable):**

- Parental permission on file before a scout appears on the public site.
- Captions use **first names only** — never full names.
- No identifying details: no home addresses, license plates, school names.
- Claude Code is instructed to check these rules on every photo PR (see CLAUDE.md).
- The full photo archive stays in the families-only Drive. This site gets a
  curated selection only.

## Recipe 4 — Add a document

Two options:

- **Link out (preferred for most):** put the file in the troop Drive folder
  and tell Claude Code: *"Open a PR linking the new packing list PDF from
  the Documents page."*
- **In the repo:** drop the PDF in the repo and say: *"Open a PR adding this
  PDF to the Documents page."* Keep repo PDFs small (a few MB max).

## Recipe 5 — Fix or change anything written on a page

Say what's wrong and what it should say:

```
Open a PR that changes the About page: the troop meets Tuesday nights at 7:00
at Wicklund Elementary MPR, and the Scoutmaster is Jane Smith, 555-123-4567.
```

This same recipe handles: meeting info, leader names, joining instructions,
homepage cards, anything with a yellow `TODO(dad)` highlight.

## Recipe 6 — Add or remove a page

```
Open a PR adding a new page called "Eagle Scouts" with: TEXT YOU WANT.
Add it to the navigation menu.
```

or

```
Open a PR removing the [PAGE NAME] page and its navigation link.
```

## Recipe 7 — One-time setups (do these first!)

| Setup | Say to Claude Code |
|-------|--------------------|
| Connect the Google Calendar | *"The public troop calendar ID is XXXX@group.calendar.google.com — open a PR connecting it."* (Calendar must be set "Make available to public" in Google Calendar settings) |
| Replace all TODO(dad) items | *"Open a PR filling in the meeting details and leaders. Here's the info: …"* |
| Point Documents at the real Drive folder | *"Open a PR setting the Drive folder URL to …"* (folder must be shared "Anyone with the link") |

## Recipe 8 — When the troop2536.org domain is bought

1. At the registrar's DNS page, add: four `A` records for `@` pointing to
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`,
   plus a `CNAME` record for `www` pointing to `troop2536-mh.github.io`.
2. Rename `CNAME.example` (in the repo root) to `CNAME` — Claude Code: *"Open
   a PR enabling the custom domain."*
3. Wait for DNS (up to an hour), then enable "Enforce HTTPS" in repo Settings → Pages.

## Recipe 9 — Undo anything

In the GitHub repo, open the PR that made the change and click **Revert**.
The site goes back ~60 seconds later. Nothing is ever lost — every version
of every page is kept in the history.

---

## The TODO(dad) list

Every yellow `TODO(dad)` highlight on the live site is tracked here. Clear
them with Recipe 5:

- [ ] Meeting night, time, and location (Home, About, Schedule, Contact pages)
- [ ] Scoutmaster name + preferred contact (About, Contact)
- [ ] Committee Chair name (About)
- [ ] Chartered organization (footer)
- [ ] Google Calendar ID (invisible until set — Recipe 7)
- [ ] Drive folder URL (Documents page — Recipe 7)

## How the site works (for the curious)

It's plain text files in a GitHub repo; GitHub builds the web pages itself
(Jekyll). No servers, no monthly fees, nothing to break. Two folders matter:
`_announcements/` (each file = one announcement) and `images/` (each folder =
one gallery). Everything else you can safely ask Claude Code to change.
