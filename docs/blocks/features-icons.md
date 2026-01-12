
← [Docs Overview](../../README.md) ·
[Featured Posts](featured-posts.md) ·
[Hero Split](hero-split.md) ·
[Hero Centered](hero-centered.md) ·
[Features Icons](features-icons.md) ·
[Features Hanging Icons](features-hanging-icons.md) ·
[Features Cards](features-cards.md)


## Block: `features-icons`

Icon-based feature list displayed in a responsive grid layout. Each feature consists of an icon, title, text, and an optional link.

![Features Icons Example](images/screenshot_features_icons.png)


### Usage

* Home page: `type: features-icons`, `content: blocks/<name>`
* Markdown: `{{< block type="features-icons" content="blocks/<name>" >}}`


### Block Content (`content/blocks/<name>/index.md`)

Configured via front matter only.

**Fields:**

* **title**
  Block heading rendered above the feature grid. *(optional)*

* **items**
  List of feature entries. *(required)*

  Each item defines:

  * `icon` – Bootstrap Icons class name (e.g. `bi bi-lightning-charge`) *(optional)*
  * `title` – feature title *(optional)*
  * `text` – short descriptive text *(optional)*
  * `link` – optional link definition (see below)

**Link fields (per item):**

* `text` – link label
* `ref` or `url` – internal reference or external link
* `style` – Bootstrap button style *(optional)*

If `style` is set, the link is rendered as a small button.
Otherwise, it is rendered as a simple text link with a chevron icon.


### Section Parameters

* **columns**
  Number of columns for large screens.
  Section-level value overrides the block’s default.
  Defaults to `3`.

* **show_title**
  Controls whether the block title is rendered.
  Defaults to `true`.


### Example

```
---
title: "Key features"
items:
  - icon: "bi bi-lightning-charge"
    title: "Fast and minimal"
    text: "A small set of building blocks that stays understandable."
    link:
      text: "Learn more"
      ref: "posts"
  - icon: "bi bi-layers"
    title: "Composable"
    text: "Pages are built from reusable content blocks."
  - icon: "bi bi-brush"
    title: "Clean design"
    text: "Focused on readability and structure."
---
```


### Notes

* Icons use **Bootstrap Icons**.
* The grid adapts responsively using Bootstrap’s `row-cols-*` classes.
* If no link is defined for an item, it is rendered as plain content.
* If the block content page cannot be resolved, nothing is rendered.


--- 

← Previous: [Hero Centered](hero-centered.md)
Next: [Features Hanging Icons](features-hanging-icons.md) →
