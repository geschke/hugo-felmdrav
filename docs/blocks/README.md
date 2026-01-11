← [Docs Overview](../README.md) ·
[Featured Posts](featured-posts.md) ·
[Hero Split](hero-split.md) ·
[Hero Centered](hero-centered.md) ·
[Features Icons](features-icons.md) ·
[Features Hanging Icons](features-hanging-icons.md) ·
[Features Cards](features-cards.md)



## Content Blocks (Page Composition)

Felmdrav uses **content blocks** to build pages from reusable sections. A block is a combination of:

* **content** (data and text), stored as a dedicated content page under `content/blocks/…`
* **structure and styling** (layout markup), implemented as an element template under `layouts/_partials/elements/…`

This separation keeps block content easy to edit (front matter in content files) while the visual layout stays inside the theme.

In practice, blocks are used in two ways:

* as an ordered list of sections in front matter (commonly on the home page)
* inline inside Markdown files via a shortcode (for flexible mixing of blocks and regular text)


### Using Blocks on the Home Page

The home page usually defines blocks in the front matter as a list of sections.
Each section entry selects a block **type** and points to a block **content** page.

Example:

```
home:
  sections:
    - type: hero-split
      content: blocks/hero-a
    - type: features-hanging-icons
      columns: 3
      content: blocks/features-a
    - type: features-cards
      columns: 3
      content: blocks/features-cards-a
```

The order of entries defines the order on the page.

Each section entry consists of:

* **type**
  The block type. This decides which element template is used for rendering.

* **content**
  A path relative to the `content/` directory, pointing to the block content file.

* **optional parameters**
  Additional settings used by certain block types (for example `columns`).


### Using Blocks Inside Markdown Pages

To place blocks between regular Markdown content, use the generic `block` shortcode.
This allows free composition like:

* block
* normal Markdown text
* another block

Example:

```
{{< block type="features-cards" content="blocks/features-cards-a" columns="3" >}}
```

All shortcode parameters (except `type` and `content`) are treated as **section parameters** and made available to the block templates the same way as on the home page.


### Where Block Content Lives

Block content is stored as dedicated content pages, typically under:

* `content/blocks/…`

These block pages usually contain **front matter only** (no body content).
They provide the data the element template renders, such as titles, lists of items, images, links, tags, and similar configuration.

### Where Block Layout Is Defined

Block layout and styling is defined by **element templates** inside the theme:

* `layouts/_partials/elements/<type>.html`

The `type` value selects the element template. For example:

* `type: hero-split`: `layouts/_partials/elements/hero-split.html`
* `type: features-cards`:`layouts/_partials/elements/features-cards.html`

Element templates receive three values:

* **root**: the page that embeds the block (used for navigation helpers like `relref`)
* **section**: the section configuration (type, columns, and other section parameters)
* **block**: the resolved block content page from `content/blocks/…` (including page resources)

This design keeps responsibilities clean:

* **content authors** edit block data under `content/blocks/…`
* **theme/layout authors** implement and style block templates under `layouts/_partials/elements/…`


## Blocks Reference

* **[`featured-posts`](featured-posts.md)**
  Displays highlighted articles with manual items and automatic content selection.

* **[`hero-split`](hero-split.md)**
  Two-column hero block with text and optional image.

* **[`hero-centered`](hero-centered.md)**
  Centered hero block with optional buttons and image.

* **[`features-icons`](features-icons.md)**
  Icon-based feature grid.

* **[`features-hanging-icons`](features-hanging-icons.md)**
  Feature list with hanging icons.

* **[`features-cards`](features-cards.md)**
  Card-based feature grid with optional images and links.


--- 



Next: [Featured Posts](featured-posts.md) →


--- 

Main Docs: 

← Previous: [Footer & Subfooter](../footer-and-subfooter.md)
Next: [Content Lists](../content-lists.md) →


