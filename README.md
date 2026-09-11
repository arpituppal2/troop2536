# Troop 2536 Website — Maintenance Guide

This is a plain **static HTML site** on GitHub Pages. No Jekyll, no build
step, no npm — just `.html` files, one stylesheet, and one tiny script.
Push to `main` → live in about a minute.

**The one rule:** nothing publishes directly. Edits go on a side branch, an
adult clicks **Merge** on the pull request, and the site updates.

```
Say it to Claude Code  →  it opens a Pull Request  →  adult clicks Merge  →  live
```

## How it's organized

| File | What it is |
|------|-----------|
| `index.html` | Home page |
| `about.html` | About / leadership / join |
| `schedule.html` | Calendar page |
| `announcements.html` | News list |
| `documents.html` | Forms & Drive link |
| `contact.html` | Contact page |
| `404.html` | Not-found page |
| `assets/css/style.css` | All styling (colors at the top) |
| `assets/js/main.js` | One tiny script: gentle fade-in on scroll |

There is no Photos page.

## Recipe 1 — Post an announcement

Tell Claude Code: *"Open a PR adding an announcement titled TITLE, dated
DATE, with this text: …"* It will add a `<article class="post">` block at
the top of the list in `announcements.html` (and mirror it on the home page).

## Recipe 2 — Update the schedule

You don't edit the site at all. Add or change the event **in Google
Calendar** and the website updates itself.

## Recipe 3 — Fix or change any text

Say what's wrong and what it should say:

```
Open a PR that changes the About page: the troop meets Tuesday nights at
7:00 at Wicklund Elementary MPR, and the Scoutmaster is Jane Smith.
```

This same recipe covers every yellow `TODO(dad)` highlight on the site.

## Recipe 3b — Set the landing photo

Drop a photo named **`Home.png`** next to `index.html` (repo root). It
becomes the home page's primary photo automatically — nothing else to
edit. Remove the file and it disappears.

## Recipe 4 — One-time setups (do these first)

| Setup | Say to Claude Code |
|-------|--------------------|
| Connect the Google Calendar | *"The public troop calendar ID is XXXX@group.calendar.google.com — open a PR connecting it."* (There are two embeds to update: `index.html` and `schedule.html`.) The calendar must be set to "Make available to public" in Google Calendar settings. |
| Replace all TODO(dad) items | *"Open a PR filling in the meeting details and leaders. Here's the info: …"* |
| Point Documents at the real Drive folder | *"Open a PR setting the Drive folder URL to …"* (folder shared "Anyone with the link") |

## Recipe 5 — When the troop2536.org domain is bought

1. At the registrar's DNS page, add four `A` records for `@` pointing to
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
   `185.199.111.153`, plus a `CNAME` record for `www` pointing to
   `troop2536-mh.github.io`.
2. Rename `CNAME.example` to `CNAME` — tell Claude Code: *"Open a PR
   enabling the custom domain."*
3. Wait for DNS (up to an hour), then enable "Enforce HTTPS" in repo
   Settings → Pages.

## Recipe 6 — Undo anything

In the GitHub repo, open the PR that made the change and click **Revert**.
The site goes back about a minute later. Every version is kept in history.

## The TODO(dad) list

Every yellow highlight on the live site is tracked here. Clear them with
Recipe 3:

- [ ] Meeting night, time, and location (Home, About, Schedule, Contact)
- [ ] Scoutmaster name + preferred contact (About, Contact)
- [ ] Committee Chair name (About)
- [ ] Chartered organization (footer, every page)
- [ ] Google Calendar ID (Recipe 4)
- [ ] Drive folder URL (Documents — Recipe 4)
