<img width="1600" height="900" alt="sumi-css-tutorial-hero" src="https://github.com/user-attachments/assets/2e2e6956-1132-4617-8143-e0fb2b0d4ed2" />

# Sumi.css

A minimalist, classless-first CSS framework. Write plain, semantic HTML and it looks finished. Add a class only when you want something specific.

- **One file, no build step.** 6.7 KB minified and gzipped, with no JavaScript and no dependencies.
- **Classless by default.** Headings, forms, tables, cards, accordions, modals and navigation are styled from the HTML element alone.
- **Light and dark mode.** It follows the visitor's system setting automatically, and `data-theme` lets you force either mode.
- **Easy to theme.** Every color, font, size and radius is a CSS custom property.
- **Easy to override.** Element styles have zero specificity, so your own CSS always wins without `!important`.
- **Accessible.** Visible focus rings, ARIA-driven states (`aria-invalid`, `aria-busy`, `aria-current`) and support for reduced motion.


**[Components](docs.html)** · **[Tutorial](tutorial.html)** · **[Cheat sheet](tutorial.html#cheatsheet)** **[Blog Post](https://www.designinspiration.info/sumi-css-tutorial-build-a-clean-website-with-plain-html/)**

---

## Contents

- [Install](#install)
- [Quick start](#quick-start)
- [What gets styled](#what-gets-styled)
- [Classes and attributes](#classes-and-attributes)
- [Layout](#layout)
- [Typography](#typography)
- [Theming](#theming)
- [Dark mode](#dark-mode)
- [Overriding styles](#overriding-styles)
- [Browser support](#browser-support)
- [Files](#files)
- [License](#license)

## Install

**Download.** Copy `sumi.min.css` into your project and link it:

```html
<link rel="stylesheet" href="sumi.min.css">
```

**CDN.** Load it from this repository through jsDelivr. 

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/vladocar/Sumi.css/sumi.min.css">
```

Use `sumi.css` (unminified) while you develop. Its comments explain every section.

## Quick start

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>My page</title>
  <link rel="stylesheet" href="sumi.min.css">
</head>
<body>
  <header>
    <nav>
      <ul><li><strong>My site</strong></li></ul>
      <ul>
        <li><a href="/" aria-current="page">Home</a></li>
        <li><a href="/about">About</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <hgroup>
      <h6>Welcome</h6>
      <h1>Hello, ink.</h1>
    </hgroup>
    <p class="lead">This page is styled by Sumi with almost no classes.</p>
    <a href="#start" data-style="button">Get started</a>
  </main>

  <footer>
    <p>© 2026 My site</p>
  </footer>
</body>
</html>
```

`<header>`, `<main>` and `<footer>` center themselves when they are direct children of `<body>`. Keep the `viewport` meta tag for phones, and set `lang` so the browser can hyphenate long-form text correctly.

## What gets styled

| Element | Result |
| --- | --- |
| `h1`–`h6`, `p`, lists, `blockquote`, `code`, `kbd`, `pre`, `mark` | Fluid type scale and consistent vertical spacing |
| `<nav>` with two `<ul>` | Navigation bar, left and right groups. Vertical inside `<aside>` |
| `<button>`, `[type=submit]`, `<a data-style="button">` | Buttons |
| `<input>`, `<select>`, `<textarea>`, `<label>`, `<fieldset>` | Full-width fields with focus rings and helper text |
| `type="checkbox"`, `type="radio"`, `type="range"`, `type="file"`, `type="color"` | Custom controls that match the theme |
| `<table>` | Clean rules and tabular numbers |
| `<article>` | Card. A direct `<header>` and `<footer>` become shaded bands |
| `<details>` / `<summary>` | Accordion with an animated chevron |
| `<dialog>` | Modal with a blurred backdrop |
| `<progress>`, `<meter>` | Determinate and indeterminate bars |

## Classes and attributes

Everything Sumi responds to beyond plain HTML:

| Class or attribute | Goes on | Effect |
| --- | --- | --- |
| `.container` `.container-fluid` `.narrow` | any block | Centered page width (72rem), full width, reading width (44rem) |
| `.grid` | wrapper | Auto-fitting columns, each at least `--s-grid-min` (14rem) wide |
| `.cols-2` `.cols-3` `.cols-4` `.cols-6` `.cols-12` | `.grid` | Fixed columns from 48rem up, one column below |
| `.span-2` … `.span-9`, `.span-full` | grid child | Spans several columns |
| `.row` `.spread` `.stack` | wrapper | Wrapping flex row, row with space between, vertical stack |
| `.display` `.lead` | heading, paragraph | Hero headline, larger intro paragraph |
| `.prose` `.serif` | text wrapper | Long-form reading column, serif typeface |
| `.secondary` `.contrast` `.outline` | button | Button colors and outline style |
| `.small` `.large` `.full` | button | Sizes, full width |
| `data-style="button"` | `<a>` | Link styled as a button |
| `data-style="group"` | wrapper | Joins buttons, or an input and a button |
| `role="switch"` | checkbox | Toggle switch |
| `aria-invalid="true"` / `"false"` | field | Red or green validation state |
| `aria-busy="true"` | any element | Loading spinner |
| `aria-current="page"` | nav link | Highlights the current page |
| `data-tooltip="…"` `data-placement="bottom"` | any element | Tooltip, above or below |
| `data-theme="light"` / `"dark"` | `<html>` or any element | Forces a color mode |
| `.dropdown` `.right` | `<details>` | Dropdown menu, right-aligned |
| `.callout` + `.success` `.warning` `.danger` | block | Message box |
| `.striped` | `<table>` | Zebra rows |
| `.muted` `.small` `.center` `.sr-only` `.overflow-auto` | any element | Utilities |

### A few examples

```html
<!-- Buttons -->
<button>Save</button>
<button class="secondary outline">Cancel</button>
<button aria-busy="true">Saving</button>

<!-- Field with helper text and validation -->
<label>Email
  <input type="email" name="email" aria-invalid="true" aria-describedby="email-help">
  <small id="email-help">Enter a valid email address.</small>
</label>

<!-- Switch -->
<label><input type="checkbox" role="switch" checked> Email reminders</label>

<!-- Card -->
<article>
  <header><strong>Six-week course</strong></header>
  <p>From first strokes to a finished hanging scroll.</p>
  <footer><a href="#book" data-style="button" class="full">€180</a></footer>
</article>

<!-- Dropdown -->
<details class="dropdown">
  <summary>Export as…</summary>
  <ul>
    <li><a href="#">PNG</a></li>
    <li><a href="#">SVG</a></li>
  </ul>
</details>

<!-- Modal: open with dialog.showModal(); the form closes it -->
<dialog id="confirm">
  <article>
    <header><h3>Delete this file?</h3></header>
    <p>This can't be undone.</p>
    <footer>
      <form method="dialog" class="row">
        <button class="secondary outline">Keep</button>
        <button class="contrast">Delete</button>
      </form>
    </footer>
  </article>
</dialog>
```

## Layout

```html
<!-- As many columns as fit; stacks on phones -->
<div class="grid">
  <div>One</div>
  <div>Two</div>
  <div>Three</div>
</div>

<!-- 12-column layout from tablet width up -->
<div class="grid cols-12">
  <div class="span-8">Main</div>
  <div class="span-4">Sidebar</div>
</div>

<!-- Change the minimum column width for one grid -->
<div class="grid" style="--s-grid-min: 10rem">…</div>
```

Cards inside a `.grid` stretch to equal heights and keep their footers aligned at the bottom.

## Typography

Headings follow a fluid scale. The ratio grows from 1.2 on phones to 1.28 on desktop, and the base size eases from 16px to 17px. No media queries are needed on your side. Line height and letter spacing tighten as headings get larger.

- `<hgroup>` pairs a heading with an eyebrow (`<h6>` before it) and a subtitle (`<p>` after it).
- `.lead` enlarges an intro paragraph. `.display` makes a hero headline.
- `.prose` sets a reading column of about 68 characters with hyphenation. An `<article class="prose">` stays plain text instead of becoming a card.
- `.serif` switches an element, or the whole `<body>`, to a system serif stack.

## Theming

Every design decision is a custom property starting with `--s-`. Override them in a stylesheet that loads after Sumi:

```css
:root {
  --s-primary: #0f766e;
  --s-radius: .25rem;
  --s-font-body: "Inter", system-ui, sans-serif;
  --s-font-heading: "Fraunces", Georgia, serif;
  --s-container: 64rem;
}
```

Tokens also work on a single element:

```html
<div class="row" style="--s-primary: #b4235a; --s-radius: 999px">
  <button>Book now</button>
  <button class="outline">Gift card</button>
</div>
```

### Main tokens

| Token | Controls |
| --- | --- |
| `--s-primary`, `--s-on-primary` | Buttons, links, focus rings, checked controls, and text on them |
| `--s-secondary`, `--s-contrast` | Secondary and contrast button colors |
| `--s-bg`, `--s-surface`, `--s-card` | Page, shaded areas, cards |
| `--s-text`, `--s-muted` | Body text, secondary text |
| `--s-border`, `--s-border-strong` | Rules, card edges, field borders |
| `--s-success`, `--s-warning`, `--s-danger` | Validation and callouts |
| `--s-font-body`, `--s-font-heading`, `--s-font-mono`, `--s-font-serif` | Typefaces |
| `--s-font-size`, `--s-line-height`, `--s-heading-weight` | Base size, leading, heading weight |
| `--s-text-display`, `--s-text-h1` … `--s-text-h4`, `--s-text-lead` | Type scale steps |
| `--s-flow`, `--s-space` | Space after text blocks, space after forms and components |
| `--s-container`, `--s-narrow`, `--s-measure`, `--s-gutter` | Page width, reading width, line length, side padding |
| `--s-radius`, `--s-shadow`, `--s-shadow-lg` | Corners and elevation |

The full list is at the top of `sumi.css`.

## Dark mode

Sumi follows the visitor's system setting with no extra code. To force a mode, set `data-theme` on `<html>`:

```html
<html lang="en" data-theme="dark">
```

`data-theme` also works on any element, so one section can be dark inside a light page. A theme switch that remembers the visitor's choice:

```js
const root = document.documentElement;
const saved = localStorage.getItem('theme');
if (saved) root.dataset.theme = saved;

document.querySelector('#theme-toggle').addEventListener('click', () => {
  const dark = matchMedia('(prefers-color-scheme: dark)').matches;
  const current = root.dataset.theme || (dark ? 'dark' : 'light');
  const next = current === 'dark' ? 'light' : 'dark';
  root.dataset.theme = next;
  localStorage.setItem('theme', next);
});
```

The dark palette appears twice in `sumi.css`: once for the system setting and once for `data-theme="dark"`. If you change dark colors, change both blocks.

## Overriding styles

Element styles are wrapped in `:where()`, which has zero specificity, so a plain selector is enough to override them:

```css
/* Sumi: :where(blockquote) { border-left: 3px solid … } */
blockquote { border-left-color: var(--s-warning); }
```

Build your own components from Sumi's tokens and they follow your theme and dark mode automatically:

```css
.badge {
  padding: .1em .55em;
  border: 1px solid var(--s-border);
  border-radius: 999px;
  background: var(--s-surface);
  color: var(--s-muted);
  font-size: .8rem;
}
```

## Browser support

Current versions of Chrome, Edge, Firefox and Safari. Sumi uses `:where()`, `:has()` and `color-mix()`, which are available from Chrome and Edge 111, Firefox 121 and Safari 16.2. Older browsers still show readable pages, with plainer hover and focus colors.

## Files

| File | Purpose |
| --- | --- |
| `sumi.css` | Source with comments, for development |
| `sumi.min.css` | Minified build, for production |
| `docs.html` | Every component with its HTML, a light/dark switch and a live token editor |
| `tutorial.html` | Step-by-step guide to building a page with Sumi |

To rebuild the minified file after editing the source:

```sh
npx lightningcss-cli --minify sumi.css -o sumi.min.css
```

## License

[MIT](LICENSE) © 2026 Vladimir Carrer
