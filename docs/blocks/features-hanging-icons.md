← [Docs Overview](../README.md) ·
[Featured Posts](featured-posts.md) ·
[Hero Split](hero-split.md) ·
[Hero Centered](hero-centered.md) ·
[Features Icons](features-icons.md) ·
[Features Hanging Icons](features-hanging-icons.md) ·
[Features Cards](features-cards.md)



### Block: `features-hanging-icons`

Feature list with “hanging” icons on the left and text on the right, displayed in a responsive grid.

#### Usage

* Home page: `type: features-hanging-icons`, `content: blocks/<name>`
* Markdown: `{{< block type="features-hanging-icons" content="blocks/<name>" >}}`


#### Block Content (`content/blocks/<name>/index.md`)

Configured via front matter only.

**Fields:**

* **title**
  Block heading rendered above the grid. *(optional)*

* **items**
  List of feature entries. *(required)*

  Each item defines:

  * `icon` – Bootstrap Icons class name (e.g. `bi bi-star`) *(optional)*
  * `title` – feature title *(optional)*
  * `text` – short descriptive text *(optional)*
  * `link` – optional button-style link (see below)

**Link fields (per item):**

* `text` – button label
* `ref` or `url` – internal reference or external link
* `style` – Bootstrap button style (default: `primary`)

Links are rendered as small Bootstrap buttons.


#### Section Parameters

* **columns**
  Number of columns for large screens.
  Section-level value overrides the block’s default.
  Defaults to `3`.

* **show_title**
  Controls whether the block title is rendered.
  Defaults to `true`.


#### Example

```
---
title: "Highlights"
items:
  - icon: "bi bi-lightning-charge"
    title: "Fast"
    text: "Minimal building blocks with clear responsibilities."
    link:
      text: "Learn more"
      ref: "posts"
      style: "primary"
  - icon: "bi bi-shield-check"
    title: "Robust"
    text: "Works well for both landing pages and documentation sites."
  - icon: "bi bi-brush"
    title: "Clean"
    text: "Focused on readability and structure."
---
```


#### Notes

* Icons use **Bootstrap Icons**.
* Item links are always rendered as buttons (no plain text-link variant in this block).
* If the block content page cannot be resolved, nothing is rendered.


--- 

← Previous: [Features Icons](features-icons.md)
Next: [Features Cards](features-cards.md) →

