# Weekly Movie Rental - https://claude.ai/public/artifacts/5ea039b9-c556-4f73-8c1a-7099b2d98a0d

A tiny two-person "movie rental drawer," styled like a retro card-catalog / file-folder system. Each week, eight films are pulled onto a shared shelf. Both people privately mark which ones they'd rent — when you both pick the same title, it's a **match**.

Runs as a single self-contained HTML file (Claude artifact) — no backend to host, no database to manage.

---

## How it works

**1. Set up the drawer**
The first time it's opened, it asks for two accounts — a name and a private passcode each. These are shared to whoever has the link; anyone who knows a passcode can sign in as that person.

**2. Sign in**
Pick your account, enter your passcode.

**3. Browse this week's eight files**
Movies load as a stack of accordion "files" styled like folders in a cabinet. Tap a title to expand it and see the director, year, genre, runtime, and a short synopsis.

**4. Rent**
Each file has a RENT button. Renting is private — the other person can't see your picks until you both rent the same movie.

**5. Match**
Once both accounts have rented the same title, it flips to **MATCHED** — visible to both of you, with a distinct border so matched and merely-rented files are easy to tell apart at a glance. Matched titles can still be un-rented (which un-matches them).

**6. The drawer footer**
Shows the current set ID, who's signed in, your rental count, and total matches. From there you can:
- **SYNC** — manually pull the latest rentals (in case the other person just rented something)
- **MATCHES** — open a modal listing every matched film, with a button to download a PDF of "match invites"
- **NEW SET** — retire the current eight and pull a fresh batch (warns first if either account has active rentals, since it clears them)
- **SIGN OUT**

---

## Where the movies come from

Each new set asks Claude to pick eight real, existing films — spanning different decades and genres, favoring mainstream/widely-recognized titles over obscure arthouse picks — and write one original-sentence synopsis per film (never lifted from marketing copy). Movies are cached per set, so everyone sees the same eight until someone pulls a new set.

If the live pull fails for any reason, it falls back to a small built-in pool of well-known films so the app never breaks.

---

## Persistence

Uses Claude artifacts' shared key-value storage, so:
- Profiles, the current set, and rentals persist across sessions
- Both accounts see the same shared data (this is a **shared storage** artifact — data is visible to anyone who signs into it, not just you)

No accounts, database, or server setup required beyond publishing the artifact.

---

## Design

Monospace, cream-and-ink, dot-matrix "case file" aesthetic (IBM Plex Mono) — movies presented like folders in a records drawer, matches marked like an approved stamp.

---

## Requirements to use

- A Claude account (Pro, Max, Team, or Enterprise — needed for persistent/shared storage)
- The artifact must be **published** (not just downloaded) for both people to see synced data — see [Publish and share artifacts](https://support.claude.com/en/articles/9547008-publish-and-share-artifacts)
