# 6. Search, sharing and the feed

Portfolio & Agency Site Template by The Diamond Empire, https://thedempire.shop/

## Your site address

Set `siteUrl` in `site.config.ts` to the public address of your site, without a trailing slash and without a path, for example `https://www.your-studio.example`. The build uses it for canonical links, Open Graph addresses, `sitemap.xml`, `robots.txt`, the RSS feed and structured data. If you do not change it, all of those point at `www.example.com`, an address that nobody owns.

You can also set it for one build without editing the file: set the `SITE_URL` environment variable, for example `SITE_URL=https://staging.your-studio.example npm run build`.

The template expects to be served from the root of a domain or sub-domain, not from a sub-folder.

## What every page gets

- A title, a description and a canonical link. Titles are limited to 70 characters and descriptions should be 50 to 180 characters: write them in the front matter of each case study and news post.
- Open Graph and Twitter card tags, which control how the page looks when it is shared.
- Structured data: the studio on every page, a breadcrumb trail on every inner page, a creative work for each case study and an article for each news post.
- An entry in `sitemap.xml`. The 404 page is not listed and is marked "noindex".

## Share images

When a page is posted on a social network, the network shows a picture. The build draws one for every page, 1200 by 630 pixels, from the page's title and its kind (for a case study, the client and year). They are written to `out/og/` as PNG files. You do not supply them, and the sample content does not use photographs.

To restyle them, edit `src/lib/og.tsx`: the colours are in the `TONES` list and the layout is the block of markup in `renderOg`. A case study's `tone` (1 to 4) in its front matter chooses its colours. The images are drawn by a tool that comes with Next.js and runs only while you build; none of its code or fonts is part of the finished site.

Social networks cache share images. If you change one, the network may show the old picture for a while.

## robots.txt

`robots.txt` allows every crawler and points to the sitemap. To keep a staging copy out of search results, change `allow: '/'` to `disallow: '/'` in `src/app/robots.ts` for that build only.

## The RSS feed

`/rss.xml` lists the news posts. Case studies are not in the feed. Change the feed title and description under `news` in `site.config.ts`.

## What the template does not do

It does not submit your site to search engines, check how it ranks or validate its structured data against a search engine's tool. Verify those yourself after you publish.
