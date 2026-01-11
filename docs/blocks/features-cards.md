

### Block: `features-cards`

Card-based feature grid. Each item is rendered as a visual card with an optional background image, optional tags, and an optional link. If a link is defined, the entire card becomes clickable.

#### Usage

* Home page: `type: features-cards`, `content: blocks/<name>`
* Markdown: `{{< block type="features-cards" content="blocks/<name>" >}}`



#### Block Content (`content/blocks/<name>/index.md`)

Configured via front matter only.

**Fields:**

* **title**
  Block heading rendered above the card grid. *(optional)*

* **items**
  List of card entries. *(required)*

  Each item defines:

  * **title** – card title *(optional)*
  * **text** – short descriptive text *(optional)*
  * **image** – background image filename, path, or URL *(optional)*
  * **tags** – list of short labels rendered as badges *(optional)*
  * **link** – optional click target for the whole card (see below)

  Items may additionally define styling overrides (see *Styling Options* below).

**Link fields (per item):**

* **ref** or **url** – internal reference or external link
  If defined, the entire card becomes clickable via a stretched link.



#### Styling Options

The appearance of cards can be customized using **Bootstrap classes**.
Styling can be defined globally for the block or overridden per card item.

**Block-level styling fields (optional):**

* **card_classes**
  Bootstrap classes applied to the outer card element.
  Default: dark card background.

* **content_classes**
  Bootstrap classes applied to the card content container (text).
  Default: white text.

* **badge_classes**
  Bootstrap classes applied to tag badges.
  Default: light badges.

**Item-level overrides:**

Each card item may define its own `card_classes`, `content_classes`, and `badge_classes`.
If present, these override the block-level defaults for that specific card.



#### Image Behavior (per item)

* If `image` matches a page resource of the block content page, that resource is used.
* Otherwise, `image` is treated as a regular path or URL.
* The resolved image is applied as a CSS `background-image` on the card.



#### Section Parameters

* **columns**
  Number of columns for large screens.
  Section-level value overrides the block’s default.
  Defaults to `3`.

* **show_title**
  Controls whether the block title is rendered.
  Defaults to `true`.



#### Notes

* If no `link` is defined, the card is rendered as a non-clickable element.
* If no `image` is defined, the card is rendered without a background image.
* Tags are rendered as Bootstrap badges at the bottom of the card.
* Styling defaults are optimized for dark images but can be overridden for light backgrounds.
* If the block content page cannot be resolved, nothing is rendered.

