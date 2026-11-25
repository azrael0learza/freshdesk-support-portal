# Re-upload notes — do these in order

This folder is the cleaned copy. The original download in `../APM-FD-Portal-main/` was left untouched, so
nothing here is irreversible.

## What was changed, and only this

1. **Files renamed and placed in a real structure:**
   - `Freshdesk Portal Converted.html` → `preview/index.html`
   - `Freshdesk Portal Mark-Up.html` → `templates/home.html`
   Byte-for-byte identical otherwise: **no code in either file was edited.** I did not add a `<main>` or
   `role="main"` to the template, because Freshdesk already supplies the page wrapper and a role added blind
   into a production template could conflict with the platform's own markup. The accessibility gaps are
   documented in the README instead of quietly patched.
2. **`README.md` rewritten.** The previous README described a `templates/home.html` structure that did not
   exist in the repo, said "Bootstrap-style classes" when the template uses 14 real Bootstrap classes, and
   did not say that the two files are different artefacts or that the preview's search is a demo.
3. **Every number in the new README was measured from the files**, per file, so it survives someone checking.

## Commit history — the honest way to do it

The download was a GitHub zip, so there is no `.git` and therefore no real history. Do **not** reconstruct a
backdated history of building this — that is the kind of thing that reads badly if anyone looks at author
dates, and it is not needed.

Three truthful commits are enough:

```
git init
git add templates/home.html preview/index.html
git commit -m "Initial import of the Freshdesk homepage template and standalone preview

Template and preview written during the Nov 2024 - Nov 2025 role and maintained there.
Imported from the previous private repository, which held the two files with
non-descriptive names."

git add README.md
git commit -m "docs: describe the two artefacts, the stack, and the known limitations

States plainly that the client-side search in the preview is a demo and that search in
production is handled by Freshdesk, and records the accessibility gaps rather than
leaving them to be found."

git push -u origin main
```

## Before you push — two things to settle

1. **Former-employer consent.** The preview hard-links to your previous employer's live portal, and the README
   names them. That is all public information, but publishing work product that names a company you left six
   weeks ago — with a manager from that company acting as your referee — is worth a one-line message rather
   than a surprise. Cheap to ask, awkward to undo after the CV has gone out with the link on it.
2. **Repository name.** `APM-FD-Portal` spells nothing to an outsider. `freshdesk-support-portal` (or
   `support-portal-homepage-template`) is searchable and self-explanatory, and the CV line can read:
   `github.com/<you>/freshdesk-support-portal — Freshdesk support-portal homepage (Liquid + Bootstrap)`.

## Suggested CV line

> Freshdesk support-portal homepage template — Liquid templating, Bootstrap grid, custom CSS with design
> tokens. Live portal: autismparenting.freshdesk.com/support/home
