
### Block: `featured-posts`

Displays a list of highlighted articles as responsive blog-style cards.
The block supports both **manually curated items** and **automatically selected content** from a section, with configurable sorting and fallback behavior.

The visual layout is fixed. The block controls **content selection only**, not presentation.

#### Usage

* Home page: `type: featured-posts`, `content: blocks/<name>`
* Markdown: `{{< block type="featured-posts" content="blocks/<name>" >}}`


#### Block Content (`content/blocks/<name>/index.md`)

The featured-posts block is configured via front matter only.

**Fields:**

* **title**
  Optional block heading rendered above the cards. *(optional)*

* **items**
  Optional list of manually defined featured items.

  Manual items are rendered **first**, in the order defined, and are never modified, filtered, or reordered.

* **section**
  Name of the content section used for automatic population (e.g. `posts`, `press`).
  If omitted, only manual `items` are rendered. *(optional)*

* **featured_key**
  Context key used to select featured content from articles.
  Matches values defined in `featured.in` in the article front matter.
  Default: `home`. *(optional)*

* **limit**
  Maximum number of cards rendered in total (manual items + auto-filled content).
  If omitted or set to `0`, all available items are rendered without limit. *(optional)*

* **fill_content**
  Controls whether the block may automatically fill remaining slots when fewer items than `limit` are available.
  Default: `true`. *(optional)*

* **fill_sort**
  Sorting mode used for automatically filled content only.
  Manual items are never affected.

  Supported values:

  * **`date_desc`** *(default)*
    Sorts posts by publication date, newest first.

  * **`date_asc`**
    Sorts posts by publication date, oldest first.

  * **`title_desc`**
    Sorts posts alphabetically by title, Z to A.

  * **`title_asc`**
    Sorts posts alphabetically by title, A to Z.

  * **`date_desc_title_desc`**
    Sorts posts by date (newest first).
    If multiple posts share the same date, they are additionally sorted by title, Z to A.

  * **`date_asc_title_asc`**
    Sorts posts by date (oldest first).
    If multiple posts share the same date, they are additionally sorted by title, A to Z.



#### Manual Items (`items`)

Manual items define their complete content and are independent of articles.

Each item defines:

* **title** – item title *(required)*
* **text** – teaser text *(required)*
* **date** – publication date *(optional)*
* **category** – category label *(optional)*
* **tags** – list of tags *(optional)*
* **image**

  * `src` – image path or URL
  * `alt` – alternative text *(optional)*
  * `position` – CSS `object-position` value *(optional)*
* **link**

  * `ref` – internal reference *(optional)*
  * `url` – external URL *(optional)*
  * `text` – custom link text *(optional)*



#### Article Front Matter (for Automatic Selection)

Articles may define a `featured` block in their front matter to participate in automatic selection.

Supported fields:

* **featured.in**
  List of context keys this article belongs to (e.g. `home`, `press`). *(optional)*

* **featured.weight**
  Numeric priority used to order explicitly featured articles.
  Higher values appear first. *(optional)*

* **featured.excerpt**
  Manually defined teaser text used in featured cards.
  Takes precedence over any automatically generated summary. *(optional)*

* **featured.image**

  * `src` – image path or page resource
  * `alt` – alternative text *(optional)*
  * `position` – CSS `object-position` *(optional)*

  If the image is a page resource, the article must be a page bundle.



#### Content Selection and Fallback Rules

The block resolves content in a strict and predictable order:

1. **Manual items** (`items`), if defined
2. **Explicit featured articles**
   Articles whose `featured.in` contains `featured_key`,
   sorted by `featured.weight` (descending), then by date (descending)
3. **Auto-filled articles** from `section`
   Only if `limit` is set and `fill_content` is enabled,
   sorted according to `fill_sort`

Articles are never rendered more than once.



#### Teaser Text Resolution

The teaser text displayed in each card is resolved as follows:

1. `featured.excerpt`, if defined
2. Article summary created via `<!--more-->`
3. Automatically generated summary, truncated to a fixed length

The full article content is never rendered inside the featured-posts block.


#### Category and Tag Resolution

The label shown above the title is resolved as follows:

1. Article `category`, if defined
2. First entry from `tags`, if no category is present
3. No label, if neither exists


#### Notes

* Manual items always take precedence over automatically selected content.
* Automatic filling only occurs when `limit` is greater than zero and `fill_content` is enabled.
* Images should be provided as page resources whenever possible.
* If no image is available, a block-defined fallback background is rendered.
* If no content is available, the block renders nothing.

#### Examples

##### Example 1: Manual Items Only (Fully Curated)

Renders only manually defined items. No automatic content selection.

```
---
title: "Highlights"

items:
  - title: "Minimal by Design"
    text: "A small, focused set of components that stays understandable."
    date: 2026-01-08
    category: "Design"
    tags: ["Theme"]
    image:
      src: "feature_02.png"
      alt: "Feature image"
    link:
      ref: "posts/minimal-by-design"
---
```

##### Example 2: Automatic Featured Posts Only

Automatically selects featured articles from a section.

```
---
title: "Featured Posts"
section: "posts"
featured_key: "home"
limit: 4
---
```

Articles must define `featured.in: ["home"]` to appear.

##### Example 3: Automatic with Fill (Latest Posts)

Explicitly featured articles are shown first.
Remaining slots are filled with the latest posts from the same section.

```
---
title: "From the Blog"
section: "posts"
featured_key: "home"
limit: 4
fill_content: true
fill_sort: "date_desc"
---
```

##### Example 4: Mixed Mode (Manual + Automatic)

Manual items are rendered first, followed by automatically selected posts.

```
---
title: "Editor’s Picks"
section: "posts"
featured_key: "home"
limit: 6

items:
  - title: "Felmdrav – First Public Release"
    text: "The Felmdrav Hugo theme is now officially released."
    date: 2026-01-10
    category: "Announcement"
    image:
      src: "release.png"
      alt: "Felmdrav release"
    link:
      ref: "posts/felmdrav-release"
---
```

##### Example 5: Strict Mode (No Auto-Fill)

Only explicitly featured articles are rendered.
No fallback filling occurs, even if fewer items than `limit` are available.

```
---
title: "Selected Articles"
section: "posts"
featured_key: "home"
limit: 4
fill_content: false
---
```

##### Example 6: Alphabetical Auto-Fill

Automatically filled posts are sorted alphabetically.

```
---
title: "All Announcements"
section: "press"
limit: 10
fill_sort: "title_asc"
---
```

