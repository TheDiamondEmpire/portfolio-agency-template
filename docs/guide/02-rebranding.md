# 2. Rebranding

Portfolio & Agency Site Template by The Diamond Empire, https://thedempire.shop/

The sample studio is called "The Diamond Empire Studio". Everything about its look and its name is in two files, so rebranding is a few lines.

## Name and details: `site.config.ts`

Change these values:

- `name`, `shortName`, `legalName`, `tagline` and `description`: shown in the header, footer, page titles and structured data.
- `siteUrl`: the public address of your site, for example `https://www.your-studio.example`. See guide 6 for why it matters.
- `contact`: email, phone, address and opening hours. The sample values are on a reserved example domain.
- `contactTopics`: the topics in the contact form's drop-down list.
- `nav` and `footerNav`: the links in the header and footer. Every link must start and end with `/`.
- `social`: your social profile addresses (used only in structured data). Leave the list empty until you have real ones.
- `themeColor`: the colour of the browser bar on some phones. Keep it equal to `--bg` in `tokens.css` (a test checks this).

## Colours, type and spacing: `src/styles/tokens.css`

The file starts with the colour tokens for the light theme, then the type scale, spacing and shape, then the dark theme.

- Colours must be plain hex values such as `#b3005c`. The tests compute colour contrast from them.
- The dark theme is written twice (once for visitors whose device prefers dark, once for the theme button). CSS cannot share one block between the two, so the two copies must stay identical. A test fails if they differ.
- No other stylesheet may contain a colour, a font name or a file address. If you need a new colour, add a token here.
- Fonts are system font stacks, so there is nothing to download. To use your own font, add the font file to `public/` and a `@font-face` rule to `tokens.css`, and keep the licence with it.

After changing colours, check the contrast of every text and background pair yourself, in both themes, with a contrast checker. The sample colours were checked by a script that is part of the template's development repository, not of this package, so nothing in this package will warn you about a weak pair. Run `npm test` as well: it checks that your content and pictures are still valid.

## Logo and favicon

The logo is a small component, `src/components/art/Logo.tsx`: replace the shapes with your own mark. The favicon is `public/favicon.svg`.

## Artwork

The hero illustration (`src/components/art/HeroArt.tsx`) and the 404 illustration are drawn from shapes and coloured with tokens, so they follow your colours. Replace them with your own artwork if you prefer.

## Share images

Every page gets its own share image, drawn at build time from the page's title (see guide 6). You do not need to supply any. To change the colours of the share images, edit the `TONES` list in `src/lib/og.tsx`.
