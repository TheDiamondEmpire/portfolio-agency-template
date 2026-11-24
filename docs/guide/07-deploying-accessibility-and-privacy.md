# 7. Deploying, accessibility and privacy

Portfolio & Agency Site Template by The Diamond Empire, https://thedempire.shop/

## Deploying

`npm run build` makes the finished site in the `out/` folder: plain HTML, CSS, JavaScript, SVG and PNG files. Upload the contents of `out/` to any place that serves static files over HTTPS. No particular provider is required, and the template contains no code for any one of them.

Things a host should do:

- Serve `index.html` for a folder address, so `/work/` shows `work/index.html`. Almost every static host does this.
- Answer an unknown address with `404.html` and the status 404.
- Use HTTPS.

Check the real output before you upload: `npm run build`, then `npm run serve`, and open http://127.0.0.1:3000.

Before you publish, replace every sample name, price, quote, address, phone number and picture, set your `siteUrl` (guide 6) and connect the contact form (guide 5).

## Accessibility

What is built in: landmarks and a skip link, a main heading on every page, links and buttons that work with the keyboard and show where the focus is, focus moved to the main area after a page change, a work filter whose links are ordinary links, text alternatives required for every case study picture, native disclosure elements for questions, motion that stops when the visitor asks for less of it, and colours that follow the light or dark setting of the device.

What that does not mean: automated tools and scripts find only part of the problems that affect people, so nothing here is a statement that your finished site meets any accessibility standard. After you change the content and the colours, you still need to:

- read every page and every picture description aloud and ask whether it makes sense;
- tab through every page without a mouse;
- zoom to 200 percent and look at the pages on a phone;
- check the contrast of any colour you add, in both themes;
- try a screen reader if you can, or ask someone who uses one.

## Privacy

The template makes no request to any other site: no fonts, scripts, analytics, maps or videos are loaded from elsewhere, and it sets no cookie. The theme button remembers the visitor's choice in the browser's local storage on their device only.

If you add analytics, a map, a video or a form service, you change this: tell your visitors in a privacy notice and ask for consent where the law requires it.

## Keeping it up to date

The tools that build the site (Next.js, React and their dependencies) come from npm. Run `npm audit` and `npm outdated` now and then, update, and run `npm run check` and `npm run build` again.
