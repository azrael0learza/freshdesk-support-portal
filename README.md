# Freshdesk Support Portal - homepage template

**[Live Preview Demo](https://azrael0learza.github.io/freshdesk-support-portal/freshdesk-support-portal/preview/)**

Custom homepage template for a production Freshdesk support portal: a self-serve hub where customers search
the knowledge base, read FAQs, browse solution categories and community forums, see popular articles and
trending discussions, and fall through to a ticket form when self-service does not solve the problem.

Built and maintained by me for Autism Parenting Magazine. The live portal is at
[APM freshdesk](https://autismparenting.freshdesk.com/support/home) - that is
the running result; this repository holds the homepage template behind it.

## What is in here

```text
freshdesk-support-portal/
├── README.md
├── preview/
│   └── index.html          standalone demo - open this in a browser
└── templates/
    └── home.html           the Liquid template that actually runs inside Freshdesk
```

Two files, and they are **not** two versions of one thing:

| File | What it is | Why it exists |
|---|---|---|
| `preview/index.html` | Complete standalone page: `<!DOCTYPE html>`, `<head>`, a 305-line custom stylesheet, 4 inline SVG icons, and a small demo script. No Liquid. | Lets anyone open the design in a browser without a Freshdesk account, and lets the look be reviewed independently of the platform. |
| `templates/home.html` | The production template body: 62 Liquid constructs - 38 tags and 24 output expressions - no `<head>`, no stylesheet. | This is what Freshdesk renders. Layout and dynamic content only - the platform supplies the head, search and ticket forms. |

## Layout sections

| Section | What it does |
|---|---|
| Search banner | Single input that hands off to Freshdesk's own knowledge-base search |
| Frequently asked questions | Direct links to the most common questions |
| Submit a ticket | Fall-through path to the ticket form |
| Solutions | Entry point to the knowledge base |
| View all articles | Full article index |
| Forums | Community discussion areas |
| Popular articles | Frequently read articles, pulled by the platform |
| Trending topics | Active community discussions, pulled by the platform |

## Technology

- **HTML5** - semantic structure, `lang` set, responsive `viewport`
- **Freshdesk Liquid** - dynamic content and conditionals: `portal.current_tab`, `category.url`,
  `topic.topic_url`, `page_message`, translation keys (`portal_translations.home.forums`), the `| t`
  translation filter, the `| escape_once` filter on rendered titles and descriptions, and Freshdesk's
  `search_element` filter for the search result block
- **Bootstrap grid and card components** - 14 grid and card classes in the production template
  (`col-md-4`, `col-lg-6`, `col-xl-3`, `card`, `card-body`, `card-title`), plus custom utilities such as
  `line-clamp-2` for truncating article titles
- **Custom CSS** - 305 lines in the preview, with 7 design tokens declared as custom properties (`--primary`,
  `--primary-dark`, `--border`, `--light-bg`, `--muted`, `--text`, `--white`), 2 media queries, and
  hover/focus states on interactive elements
- **Inline SVG** - 4 icons in the preview, 3 in the template; no icon font and no external image requests
- **Accessibility** - `lang` and `viewport` set; `aria-*` attributes on interactive elements (9 in the
  preview, 7 in the template body)

## Known limitations, stated plainly

- **The client-side search in `preview/index.html` is a demo.** It filters sample items in the browser so
  the interaction can be seen without a portal. In production, search is handled by Freshdesk; the template
  hands the query to the platform and does not implement search itself.
- **No `<nav>` landmark and a loose heading hierarchy** - one `h1` and section headings below it that could
  be tightened. `<main>` is supplied by Freshdesk's own page wrapper, so it is deliberately not duplicated in
  the template body.
- **Icons are inline SVG without `alt` attributes** - decorative by design, labelled through the surrounding
  link text rather than through alt text.
- **Single page.** This is the homepage template only; solution, article and forum page templates are
  separate and are not included here.

## Notes

- All customer-facing strings go through Freshdesk translation keys rather than being hard-coded, so the
  portal can be localised without touching the template.
- Titles and descriptions from the platform are passed through `escape_once` before rendering.
