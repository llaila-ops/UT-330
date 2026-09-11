# UT330 semester site

A working example. Everything on it is real HTML you can copy. There is no
build step, nothing to install, and no framework. You edit a file, you push it,
it is live.

Fork this, or download it and start your own repository.

## What is in here

| File | What it is |
|---|---|
| `index.html` | Home page |
| `about.html` | About you and how the site is built |
| `project.html` | Final project, empty until later |
| `kitchen-sink.html` | Every element you can use, rendered. Copy from here. |
| `entries/index.html` | List of all log entries |
| `entries/_TEMPLATE.html` | Blank entry. Duplicate this each week. |
| `entries/2026-09-11-...html` | A fully written example entry |
| `css/custom.css` | Your styling |
| `images/` | Your images |

## Publish it

1. New repository on GitHub. If you name it `yourusername.github.io` it lives at that address. Any other name puts it at `yourusername.github.io/reponame`.
2. Upload these files, or drag the folder into the browser on the repo page.
3. Settings, then Pages. Source: Deploy from a branch. Branch: `main`, folder `/ (root)`. Save.
4. Wait a minute, then load your address.
5. Every push updates the live site.

If you already use Vercel, connect the repo there instead. Same result.

## Two stylesheets

Look at the `<head>` of any page:

```html
<link rel="stylesheet" href="https://cdn.simplecss.org/simple.min.css">
<link rel="stylesheet" href="css/custom.css">
```

The first is [simple.css](https://simplecss.org), loaded from someone else's
server. It styles plain HTML. No classes anywhere. Write a `<table>` and it
looks like a table.

The second is yours, and it loads second, so it wins where the two disagree.
That ordering is the cascade. Swap the two lines and your styling stops working.

Simple.css is one of many. The same HTML under a dozen different stylesheets:
[classless-css-demo.deno.dev](https://classless-css-demo.deno.dev/). Swap the
first link for a different one and watch the site change without touching a
single line of HTML. That is the whole point of separating structure from
presentation.

## Make it yours

Open `css/custom.css`. Two sections matter.

**Fonts.** The `@import` at the top pulls Instrument Serif and Inter from Google
Fonts. Replace it with something from [fonts.google.com](https://fonts.google.com)
or [fontshare.com](https://www.fontshare.com), then set the font name in
`--sans-font` and `--heading-font`. The `@import` must be the first line in the
file or it silently does nothing.

**Colors.** The variables under `:root`. Their names come from simple.css.
Change a value and it changes everywhere. Try [coolors.co](https://coolors.co),
or pull hex codes out of a photo you like.

Then write whatever you want in section 4 at the bottom.

## Add an entry each week

1. Duplicate `entries/_TEMPLATE.html`
2. Rename it `2026-09-24-short-title.html`. Date first so the files sort themselves.
3. Write it.
4. Add a link at the top of the list in `entries/index.html`.
5. Add a link on `index.html` too.

## Paths

Files inside `entries/` are one folder down, so they reach back out with `../`:

```
entries/whatever.html   →   ../css/custom.css
entries/whatever.html   →   ../images/photo.png
entries/whatever.html   →   ../index.html
```

Files at the root do not need the `../`. This is the single most common reason a
page loads with no styling.

## Things not to skip

Every image needs `alt` text. Describe what is in it.

Every form input needs a `<label>`. Placeholder text is not a label.

Headings go in order. Do not jump from `h2` to `h4` because you like the size.
Change the size in CSS.

## When it breaks

Right click, Inspect, Console tab. Red text tells you what failed.

Check that the CSS link is the right path, that every tag you opened is closed,
and that every `{` in CSS has a `}`.
