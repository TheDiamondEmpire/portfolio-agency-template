# 1. Start here

Portfolio & Agency Site Template by The Diamond Empire, https://thedempire.shop/

This guide explains what is in the folder and what each command does.

## Requirements

- Node.js 22 or later, which includes npm. Check with `node --version`.
- A terminal opened in the folder that contains `package.json`.

## Commands

| Command | What it does |
|---|---|
| `npm install` | Downloads the tools the project needs into `node_modules/`. Run it once. |
| `npm run dev` | Starts a local preview at http://localhost:3000 that updates as you edit. |
| `npm run build` | Makes the finished site in the `out/` folder. This is what you upload. It also draws one share image for every page. |
| `npm run serve` | Shows the `out/` folder at http://127.0.0.1:3000 so you can check the real output. |
| `npm run typecheck` | Checks the TypeScript code for mistakes. |
| `npm run lint` | Checks the code for common problems, including accessibility mistakes in the markup. |
| `npm test` | Runs the unit tests, including the checks on your case studies and their pictures. |
| `npm run check` | Runs the type check, the lint and the tests together. |

If `npm run build` or `npm test` stops with a message that names a file in `content/`, a value in that file is missing or mistyped. The message names the file and the field, for example `case study error in content/work/my-project.mdx: "year" must be a four-digit year such as 2026`.

## What is in the folder

```text
site.config.ts         name, address, contact details, navigation: the one place for site settings
src/styles/tokens.css  colours, type sizes, spacing and shape: the one place for the design
content/work/          one MDX file per case study
content/news/          one MDX file per news post
content/*.json         home page, services, team and the work categories
public/                files served as they are: favicon and the pictures of each case study
src/app/               the pages (one folder per address)
src/components/        reusable pieces: header, footer, cards, work grid, pictures, form
src/lib/               helpers: content loading, filtering, SEO, share images, structured data
tests/unit/            unit tests
docs/guide/            these guides
out/                   the finished site (created by npm run build; do not edit)
```

## Edit, then look

1. Run `npm run dev`.
2. Change something, for example the headline in `content/home.json`.
3. Save. The browser updates.

Next.js can collect anonymous usage statistics about the development tool. This does not affect your site and nothing is added to it. To switch it off on your computer, run `npx next telemetry disable`.

## Where to go next

Read the rebranding guide: [Rebranding](02-rebranding.md).
