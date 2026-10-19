# JOBS Workshop website

Source for the JOBS Workshop, a workshop for computer
architecture PhD students and postdocs going on the job market, co-located with
MICRO.

**Live site:** <https://comparchsa.github.io/jobs-workshop.github.io/>

A plain [Jekyll](https://jekyllrb.com/) site built by GitHub Pages. All site documentation lives in this file.

---

## Editing the site

**Almost every edit you will ever make is to a file in [`_data/`](_data/).**

The pages read from those YAML files and render whatever is in them. You should
rarely need to touch a `.html` or `.md` file to change content.

| Target change | Target file|
|---|---|
| Dates, times, venue, application link, deadlines | [`_data/workshop.yml`](_data/workshop.yml) |
| The schedule, its speakers and panelists | [`_data/schedule.yml`](_data/schedule.yml) |
| The organizing committee | [`_data/organizers.yml`](_data/organizers.yml) |
| The selected job candidates | [`_data/candidates.yml`](_data/candidates.yml) |
| The tabs in the top nav | [`_data/navigation.yml`](_data/navigation.yml) |
| The archive of previous years | [`_data/past_editions.yml`](_data/past_editions.yml) |
| Site title, description, URL | [`_config.yml`](_config.yml) |

Every one of those files opens with a comment block explaining its fields.

---

## Things to fill in before publishing

The site is complete but a few values are placeholders:

- **`contact_email`** in `_data/workshop.yml` is the literal string
  `<placeholder>`. Until it contains an `@`, the site prints it as plain text
  in a dashed box rather than a mailto link, so no dead address is published.
  Put the real address in and every occurrence becomes a working link on its
  own — see [`_includes/contact.html`](_includes/contact.html).
- **`submission.url`** is empty. Paste the HotCRP URL when the site is live.
- **`important_dates`** are all `TBD` except the workshop date itself.
- **Schedule speakers** are all `TBD`.
- **`venue_room`** is `TBD` until MICRO assigns it.

---

## Common tasks

### Turn on the job-candidate application

Applications run through HotCRP. In [`_data/workshop.yml`](_data/workshop.yml):

```yaml
submission:
  label: "Apply as a job candidate"
  url: "https://jobs2026.hotcrp.com/"
  hotcrp_name: "jobs2026.hotcrp.com"
```

While `url` is empty the button renders as a greyed-out "opens soon" chip
instead of a dead link, so it is always safe to ship the page before HotCRP
exists. Fill in the matching deadlines under `important_dates` at the same time.

### Publish the selected candidates

After selection, add a block per candidate to
[`_data/candidates.yml`](_data/candidates.yml):

```yaml
- name: Ada Lovelace
  affiliation: University of Virginia
  seeking: Academia          # free text; shown as a tag
  cv: https://example.org/ada-cv.pdf
  website: https://example.org/ada                     # optional
  research: Analytical engines and compiler design.    # optional, one line
```

Commit and push. The table on `/candidates/` picks it up automatically. While
the list is empty the page shows a "not published yet" panel rather than an
empty table.

### Confirm a speaker or panelist

In [`_data/schedule.yml`](_data/schedule.yml), replace the `TBD` entry:

```yaml
  people:
    - name: Jane Researcher
      affiliation: NVIDIA
      url: https://example.org/jane                 # optional
      role: Moderator                               # optional
      photo: /assets/img/speakers/jane-researcher.jpg   # optional
```

**Photos.** Drop square images (400×400 or larger is plenty) into
`assets/img/speakers/` and point `photo:` at them. Anyone without a photo gets
a circle with their initials, so a partly-confirmed panel still looks
deliberate — you can add photos one at a time as people send them.

### Change the schedule itself

Every field in `_data/schedule.yml` is optional except `title`, so the file
works at any stage of planning:

```yaml
# Times not settled yet — just list the sessions
- kind: panel
  title: "Panel: Research careers in industry and academia"

# Times settled
- start: "08:15"
  end: "09:00"
  kind: panel
  title: "Panel: Research careers in industry and academia"
```

A slot with no `start` renders without a time on `/schedule/` and shows "TBD" in
the home-page summary. `kind` is one of `panel`, `talk`, `break`, or `session`
and sets the card style (breaks are shaded). Reordering entries
reorders the page.

The note above the schedule comes from `schedule_note` in
[`_data/workshop.yml`](_data/workshop.yml); set it to `""` to hide it once the
program is final.

### Update the organizing committee

[`_data/organizers.yml`](_data/organizers.yml) — order in the file is order on
the page. Photos work the same way as for speakers, in
`assets/img/organizers/`. Two extra options exist for the awkward cases:

- `initials:` overrides the letters derived from the name, for entries that
  are not a person ("CASA" rather than the "CS" that would be derived).
- `photo_fit: contain` fits a **logo** whole inside the circle on a white disc,
  instead of cropping it to fill like a face. The CASA Steering Group uses it.

For faces, `photo_position` and `photo_zoom` control the framing — see the
comment block at the top of [`_includes/avatar.html`](_includes/avatar.html).

### Add a page

1. Create `newpage.md` at the repo root with front matter:

   ```yaml
   ---
   title: New Page
   subtitle: One line under the heading.   # optional
   permalink: /newpage/
   ---
   ```

   Note that front matter is not processed as Liquid — `{{ }}` in `title` or
   `subtitle` will render literally.

2. Add it to [`_data/navigation.yml`](_data/navigation.yml) with a `url` that
   matches the `permalink` exactly, slashes included.

The `page` layout is applied automatically (see `defaults` in `_config.yml`), so
you only write the body.

---

## Rolling the site over to the next edition

Ten minutes of work, in this order:

1. **Archive the edition that just ended.** Add an entry to the *top* of
   [`_data/past_editions.yml`](_data/past_editions.yml) — year, conference,
   date, location, a short summary, and the highlights.
2. **Update [`_data/workshop.yml`](_data/workshop.yml)** — edition, dates,
   venue, co-located conference and its URLs, important dates; reset
   `submission.url` to `""` and restore `schedule_note`.
3. **Reset [`_data/schedule.yml`](_data/schedule.yml)** to a skeleton with
   `TBD` speakers.
4. **Update [`_data/organizers.yml`](_data/organizers.yml)** for the new
   committee.
5. **Empty [`_data/candidates.yml`](_data/candidates.yml)** — keep the comment
   header, delete the entries.
6. **Update `title` in [`_config.yml`](_config.yml)** to the new year.
7. **Update the `calendar:` block** in `_data/workshop.yml` — the `.ics` times
   are UTC and do not derive themselves from the dates above.
8. **Regenerate `assets/img/social-card.png`** (1200x630) so link previews show
   the right year.

Nothing else needs to change. The prose on the pages reads years, venues, and
conference names out of `_data` rather than hard-coding them.

---

## Previewing locally

```bash
bundle install
bundle exec jekyll serve --livereload
# → http://127.0.0.1:4000/jobs-workshop.github.io/
```

Note the `/jobs-workshop.github.io/` suffix — that is the `baseurl`, and it is
part of the local URL too.

`_config.yml` is the only file Jekyll does not hot-reload; restart the server
after editing it.

If you would rather not install Ruby, editing YAML directly in the GitHub web UI
is perfectly fine — GitHub Pages builds it and emails you if something breaks.

---

## Deployment and URLs

Served from the `main` branch by GitHub Pages, under
**Settings → Pages → Source: Deploy from a branch**.

Because the repository lives under the `comparchsa` organization rather than a
user or org literally named `jobs-workshop`, the published URL is a project
page:

```
https://comparchsa.github.io/jobs-workshop.github.io/
```

which is why `_config.yml` sets:

```yaml
url:     https://comparchsa.github.io
baseurl: /jobs-workshop.github.io
```

**Moving to a custom domain later** (e.g. `jobsworkshop.org`):

1. Add a `CNAME` file at the repo root containing just the bare domain.
2. Set `url:` to `https://jobsworkshop.org` and `baseurl:` to `""`.
3. Point DNS at GitHub Pages and enable HTTPS in Settings → Pages.

All internal links go through Jekyll's `relative_url` filter, so they follow
`baseurl` automatically — you do not have to hunt through the templates.

---

## Layout of the repository

```
_config.yml            site-wide settings
_data/                 ← all the content you actually edit
_includes/
  nav.html             top navigation bar
  footer.html          footer
  cta.html             the job-candidate application buttons
  contact.html         the organizers' address, or the placeholder
  avatar.html          one person's photo, or their initials in a circle
  organizer-grid.html  the committee card grid (used on 2 pages)
_layouts/
  default.html         html skeleton: head, nav, main, footer
  page.html            default.html + the page title band
index.html             home page (hero + sections)
schedule.md            timeline rendered from _data/schedule.yml
candidates.md          how to apply + table from _data/candidates.yml
organizers.md          committee grid, panelist nominations, contact
past-editions.md       archive from _data/past_editions.yml (footer link only)
404.html               shown for any unknown URL
calendar.ics           generates /jobs-workshop-2026.ics from workshop.yml
assets/img/social-card.png   1200x630 link preview image
assets/css/style.css   every style on the site, one file, plain CSS
assets/js/site.js      the mobile nav toggle — the only JS on the site
```

### Restyling

The palette is [Tokyo Night Light](https://github.com/enkia/tokyo-night-vscode-theme),
the VS Code theme. Surfaces and text come from the theme's own JSON; `--brand`
and `--accent` are its link-blue and purple syntax colours.

**The site is light-only, on purpose.** There is no
`@media (prefers-color-scheme: dark)` block, and `html { color-scheme: light }`
stops dark-mode browsers from auto-darkening scrollbars and form controls. If
you add a dark block back, anyone whose OS is set to dark mode will stop seeing
the light palette entirely — which is exactly the trap this note exists to
prevent.

All colours are CSS custom properties in the single `:root` at the top of
[`assets/css/style.css`](assets/css/style.css). There are four surface levels:
`--surface` (cards, tables, header), `--bg` (page canvas), `--bg-soft` (banded
sections, page headers), and `--bg-sunken` (footer). `--text` and
`--text-muted` are the two text tones.

The palette is checked against WCAG 2.1 AA: every text/background pair is at
least 4.5:1, and control outlines are at least 3:1. **If you change
a colour, re-check it** — <https://webaim.org/resources/contrastchecker/> takes
about ten seconds per pair.

### Accessibility

The site is built to WCAG 2.1 AA. What is already in place:

- One `<h1>` per page and no skipped heading levels.
- `<header>`, `<nav>`, `<main>`, `<footer>` landmarks, a skip-to-content link,
  and `aria-current="page"` on the active tab.
- Visible focus outlines on every interactive element. The mobile menu is a
  real `<button>` with `aria-expanded`; <kbd>Esc</kbd> closes it and returns
  focus to the button rather than dropping focus to the top of the page.
- The candidate table sits in a `tabindex="0"` `role="region"` box, so it can
  be scrolled sideways with the keyboard on a narrow screen. **Keep those
  attributes on any scrollable box you add** — without them the content is
  unreachable without a mouse.
- Decorative images carry `alt=""`; the initials circles are `aria-hidden`, so
  names are announced once, not twice.
- Table headers use `scope`, and the candidate table has a caption.
- Dates and session times are wrapped in `<time datetime="...">`.
- Text sizes are in `rem`, so browser zoom and OS font-size settings work.
- Wide content scrolls inside its own box; the page body never scrolls
  sideways, down to a 320px-wide screen.
- Honours `prefers-reduced-motion` and `forced-colors` (Windows High Contrast).
- The site is fully readable with JavaScript disabled.

**When adding content, the three things that break this most often:** an image
without `alt`, a link whose text is "here" or "click here", and a heading level
skipped for visual reasons. Style headings with CSS instead of picking a
smaller tag.

---

## Credits

Organized by [CASA](https://www.comparchsa.org), the Computer Architecture
Student Association. All participants are expected to follow the
[SIGARCH CARES](https://www.sigarch.org/benefit/cares/) policies.

The original scaffolding came from the `pages-themes/minimal` Jekyll theme
(CC0), by way of [PLTea](https://github.com/pltea/pltea.github.io) and the CASA
ArchChat site — thanks to Rachit and everyone there. See [LICENSE](LICENSE).
