← [Docs Overview](../README.md) ·
[Featured Posts](featured-posts.md) ·
[Hero Split](hero-split.md) ·
[Hero Centered](hero-centered.md) ·
[Features Icons](features-icons.md) ·
[Features Hanging Icons](features-hanging-icons.md) ·
[Features Cards](features-cards.md)


### Block: `hero-split`

Two-column hero block with text and optional buttons on the left and an optional image on the right.

#### Usage

* Home page: `type: hero-split`, `content: blocks/<name>`
* Markdown: `{{< block type="hero-split" content="blocks/<name>" >}}`

#### Block Content (`content/blocks/<name>/index.md`)

The hero block is configured via front matter only.

**Fields:**

* **title**
  Main heading of the hero block (page title). Rendered as `<h1>`. *(optional)*

* **lead**
  Short descriptive text displayed below the title. Rendered as a Bootstrap `lead` paragraph. *(optional)*

* **buttons**
  Optional list of call-to-action buttons.

  Each button defines:

  * `text` – button label
  * `ref` or `url` – internal reference or external link
  * `style` – Bootstrap button style (default: `primary`)

* **image**
  Optional image shown in the right column.

  Fields:

  * `src` – image filename, relative path, or URL
  * `alt` – alternative text used for accessibility and SEO *(optional)*

  If `src` matches a page resource of the block content page, that resource is used.
  Otherwise, the value is treated as a regular path or URL.

#### Example

```
---
title: "Welcome to Felmdrav"
lead: "A minimal, block-based Hugo theme."
buttons:
  - text: "Get started"
    ref: "posts"
    style: "primary"
  - text: "GitHub"
    url: "https://github.com/geschke/hugo-felmdrav"
    style: "outline-secondary"
image:
  src: "hero.png"
  alt: "Abstract hero image"
---
```

#### Notes

* If no image is defined, the layout collapses to text-only.
* If the block content page cannot be resolved, nothing is rendered.

--- 

← Previous: [Featured Posts](featured-posts.md)
Next: [Hero Centered](hero-centered.md) →
