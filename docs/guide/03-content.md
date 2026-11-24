# 3. Work, services, team and news

Portfolio & Agency Site Template by The Diamond Empire, https://thedempire.shop/

All the words on the site are in `content/`: JSON files for the fixed pages and MDX files for case studies and news. MDX is Markdown (headings, lists, links, tables) with a few extra components.

Every file is checked when the site is built. A mistake stops the build with a message that names the file and the field.

## The fixed pages

| File | Page |
|---|---|
| `content/home.json` | Home page: headline, selected-work heading, approach steps, quotes, call to action |
| `content/services.json` | Services page: each service, the process steps and the questions |
| `content/team.json` | Team page: people, how the studio works, values |
| `content/work.json` | Work page: the introduction and the list of categories |

The quotes in `home.json` are invented. Replace them with real ones, and only with permission.

## Categories

Categories are listed in `content/work.json`. Each has an `id` (lower-case letters, numbers and hyphens), a `label` and a `description`. The work page shows one filter link per category, and the site builds one page per category at `/work/category/<id>/`. The id `all` is reserved.

To add a category, add it to the list and use its `id` in at least one case study. To remove one, change the `category` of its case studies first: the build stops if a case study names a category that is not listed.

## Adding a case study

1. Create `content/work/your-project.mdx`. The file name becomes the address: `/work/your-project/`. Use lower-case letters, numbers and hyphens. The name `category` is reserved.
2. Start the file with the front matter, between two lines of three hyphens:

```text
---
title: "Client name: what you did"
description: "One or two sentences for search results, 50 to 180 characters."
summary: "One or two sentences shown on the project card."
client: "Client name"
year: 2026
category: branding
services: [Identity, Signage]
role: Lead studio
duration: 12 weeks
featured: true
tone: 2
images:
  - id: cover
    alt: "What the picture shows, for people who cannot see it"
    caption: "Optional caption."
    width: 1600
    height: 1000
results:
  - value: "-38%"
    label: What was measured
    note: How and when
---
```

3. Write the text under the front matter. Use `##` and `###` headings. Do not use a single `#`: the title is the page heading.
4. Add the pictures (guide 4).

Notes on the front matter:

- Put quotes around any text that contains a colon.
- `featured: true` puts the case study in the "Selected work" row on the home page (the first three are shown).
- `tone` (1 to 4) picks the colour of the share image of this case study.
- `results` is optional. Say what was measured and over what period. The page prints a note that the sample figures are invented; edit that sentence in `src/components/Results.tsx` when you replace them with real ones.
- The first image must have the id `cover`. It is used on the card, at the top of the page and nowhere else.
- Case studies are listed newest year first. The "previous" and "next" links at the bottom of each case study follow that order and wrap around.

### Components inside a case study

- `<Figure id="one" />`: one picture with its caption.
- `<Gallery ids="one,two,three" label="Phone screens" />`: several pictures in a grid. Wide pictures take a whole row.
- `<Pullquote by="Name, role">Words.</Pullquote>`: a highlighted quotation.
- `<Callout title="Note">Text.</Callout>`: a highlighted note.

The ids must be listed under `images` in the front matter. If one is not, the build stops and says which.

## Adding a news post

Create `content/news/your-post.mdx` with this front matter: `title`, `description`, `date` (written YYYY-MM-DD), `tags` (a list) and `author` (the `id` of a person in `content/team.json`). `updated` is optional. The post appears on the news page, in the sitemap and in the RSS feed.

## Services and team

Edit the lists in `content/services.json` and `content/team.json`. Every service and every person needs a unique `id`. A service's `icon` must be one of the names in `src/components/art/Icons.tsx`. Team members show a drawn stand-in for a portrait; the stand-in follows your colours. To use photographs you will need to add an image component that fits your needs (guide 4 explains the rules for pictures).

## Adding a page

1. Create the folder and file, for example `src/app/pricing/page.tsx`, copying the structure of `src/app/team/page.tsx` (it builds its metadata with `pageMetadata` and renders breadcrumbs).
2. Add the page to `STATIC_PAGES` in `src/lib/routes.ts` so it is listed in the sitemap.
3. Add it to `nav` and `footerNav` in `site.config.ts` if it should be in the menus.
4. Add an entry for its share image in `ogEntries()` in `src/lib/og.tsx`, using the same key rule as `ogKeyForPath` in `src/lib/og-key.ts`, or the page will point at an image that does not exist.
