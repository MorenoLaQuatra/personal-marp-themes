# academic-conferences theme: agent instructions

Context for a coding agent generating Marp slide decks with the
`academic-conferences` theme.
Read this before writing or editing any `.md` deck that uses it.

## What this theme is for

Use this theme for academic conference talks: paper presentations, invited talks, and workshop talks.

## Setup

Front matter for any deck using this theme:

```markdown
---
marp: true
paginate: true
header: 'Talk title or short label'
footer: 'Speaker name | Venue or event'
theme: academic-conferences
math: mathjax
---
```

`math: mathjax` is optional, only needed if the deck has formulas.

## Hard design rules

These are deliberate constraints.
Do not reintroduce what was removed.

1. **No borders on a single side, anywhere.**
   No `border-left`, `border-top`-only, or `border-bottom`-only decoration on boxes, cards, or quotes.
   The only borders in the theme are symmetric, all four sides, for example `.stat` or `pre`.
   The booktabs table rules are a deliberate, named exception, not a decoration.
2. **No badges, chips, dots, or icons.**
   Components are identified by a tinted background and, where relevant, a color-matched heading.
   Do not add label pills, uppercase tags, or marker dots back in.
3. **Minimal HTML.**
   Prefer native Markdown (`#`/`##`, `**bold**`, `> quote`, tables, lists) over hand-written `<div>`s.
   Reach for a single wrapping `<div class="...">` only when a component must be scoped to part of a slide, for example two boxes side by side.
   Never nest divs more than one level deep for styling purposes.
4. **Never use an em dash or en dash** (`—`, `–`) **in slide content.**
   Use a period, comma, or colon instead.
5. **Colorblind-safe palette only.**
   If a new component needs a color, pick one of the five existing category colors (see below) rather than adding a new hue.

## Component reference

### Title slide

```markdown
<!-- _class: lead -->

# Talk Title

<p class="subtitle">One-line subtitle or tagline</p>

<p class="authors">Speaker Name · Affiliation</p>
```

Centers everything vertically and horizontally.
Use once, as the first slide.

### Section divider

Full-bleed color slide to separate parts of a talk.

```markdown
<!-- _class: section -->

# Part Title
```

Default color is blue.
Add a modifier class for variety across a long deck: `section teal`, `section plum`, or `section amber`.
Modifiers are space-separated in the same `_class` comment, for example `<!-- _class: section teal -->`.

### Semantic boxes

Five categories, color-coded by convention:

| Class        | Color  | Use for                              |
|--------------|--------|---------------------------------------|
| `definition` | blue   | concepts, terminology, formal statements |
| `example`    | teal   | worked examples, illustrations        |
| `important`  | amber  | key takeaways, things to remember     |
| `warning`    | brick  | caveats, limitations, common mistakes |
| `note`       | plum   | asides, pointers to related work      |

Two ways to apply them:

**Whole slide (preferred, zero HTML):**

```markdown
<!-- _class: definition -->

## Term

Body text, lists, formulas, whatever the slide needs.
```

**Inline, next to other content (one wrapper div, use only when a box must sit beside something else on the same slide):**

```markdown
<div class="important">

### Heading
Body text.

</div>
```

Do not nest anything inside the box beyond normal Markdown.
Do not add a label, icon, or border to a box manually, the class already handles it.

### Native elements (no class needed)

These are themed automatically, just write plain Markdown:

- `**bold**` renders in blue.
- `> quote text` renders as a centered, softly tinted pull-quote card with a large quotation mark.
  Good for citations or memorable lines.
  Put the attribution on a second line inside the same blockquote.
- Tables render **booktabs-style**: a heavy rule above the header, a hairline under the header, a heavy rule at the bottom, no vertical lines, no row shading.
  Column alignment is controlled the normal Markdown way (`:---:`, `---:`).
  Do not add classes to plain tables, the styling is automatic.
- Fenced code blocks and inline `` `code` `` get a neutral background.
- `[link](url)` is underlined, in blue.

### Layout utilities

```markdown
<div class="cols-2">

<div>Left content</div>
<div>Right content</div>

</div>
```

`cols-2`, `cols-3`, `cols-4` are CSS grids with even columns.
Put plain `<div>`s (or box classes) directly inside.
Also available: `.center` (text-align center), `.small` (smaller text), `.muted` (secondary gray text).

### Figures

```markdown
<figure>

![w:600](diagram.png)

<figcaption>Figure 1: caption text.</figcaption>

</figure>
```

Use native `<figure>`/`<figcaption>`, not a `div` with a custom class.

### Headline metrics

```markdown
<div class="stats">

<div class="stat">

### 90.4%
Accuracy

</div>

<div class="stat">

### 31M
Parameters

</div>

</div>
```

A row of big-number cards for a results slide.
Each `.stat` is a heading (the number) plus one line of label text underneath.

### Results tables with highlighted values

Wrap the best/worst figure in a span inside a normal Markdown table cell:

```markdown
| Model | Accuracy |
|-------|----------|
| Ours  | <span class="value-high">90.4%</span> |
| Base  | <span class="value-low">81.2%</span>  |
```

`value-high` is teal with an up-triangle, `value-low` is brick red with a down-triangle.
Use for the standout number in a comparison table, not for every cell.

### Closing slide: speaker and resource cards

Compose these on a plain (non-`lead`) slide titled something like `## Get in Touch`.

**Author cards** (name, affiliation, contact), one per author, inside `cols-2`/`cols-3`:

```markdown
<div class="cols-2">

<div class="author-card">

### Speaker Name
Affiliation
[email@domain.edu](mailto:email@domain.edu)

</div>

<div class="author-card">

### Co-author Name
Affiliation
[email@domain.edu](mailto:email@domain.edu)

</div>

</div>
```

**QR cards** (paper, code, slides links), inside a `qr-row`:

```markdown
<div class="qr-row">

<div class="qr-card">

![w:120](qr-paper.png)

Paper

</div>

<div class="qr-card">

![w:120](qr-code.png)

Code

</div>

</div>
```

For a simple text-only link line without cards, use `.contacts` instead:

```markdown
<div class="contacts">

[site.example](https://site.example)
[email@domain.edu](mailto:email@domain.edu)

</div>
```

### Text color utilities

`.text-blue`, `.text-teal`, `.text-amber`, `.text-plum`, `.text-brick` tint a span of inline text.
Use sparingly, and only to match one of the five category colors.
For example: `<span class="text-brick">not recommended</span>`.

## Color palette reference

| Token          | Hex       | Meaning              |
|----------------|-----------|-----------------------|
| `--ink`        | `#1c2024` | body text             |
| `--muted`      | `#5c6570` | secondary text        |
| `--surface`    | `#f7f8fa` | neutral card fill     |
| `--blue`       | `#2166ac` | definition / links / bold |
| `--teal`       | `#1b7a72` | example / high values |
| `--amber`      | `#a3690a` | important             |
| `--plum`       | `#7a5195` | note                  |
| `--brick`      | `#a13d3d` | warning / low values  |

Each color also has a `-bg` tint variant, for example `--blue-bg`, used for box backgrounds.
Do not hardcode hex values in slide content.
Use the existing classes so a future palette change stays centralized in the CSS.

## Reference deck

See `academic-conferences-demo.md` in this repo for a full 20-slide example exercising every component above.
Copy patterns from it rather than inventing new markup.

## Checklist before finishing a deck

- [ ] Front matter sets `theme: academic-conferences`
- [ ] No em dashes or en dashes anywhere in the content
- [ ] No one-sided borders, badges, chips, or dot markers added by hand
- [ ] HTML is limited to single wrapper `<div>`s, `<figure>`/`<figcaption>`,
      and `<span>` for inline color/value emphasis
- [ ] Box classes used match their semantic meaning (definition, example,
      important, warning, note)
- [ ] Closing slide uses `.author-card` / `.qr-row` rather than ad hoc markup
