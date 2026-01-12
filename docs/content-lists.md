← [Main README](../README.md) ·
[Configuration](configuration.md) ·
[Layout & Sidebars](layout-and-sidebars.md) ·
[Footer & Subfooter](footer-and-subfooter.md) ·
[Content Blocks](blocks/README.md) ·
[Content Lists](content-lists.md) ·
[Typography](typography.md) ·
[Image Processing](images.md) ·
[Analytics](analytics.md) ·
[Menus & Taxonomies](menus-and-taxonomies.md) ·
[Migration](migration-from-tikva.md)



## Content Lists & Section Listings

Felmdrav provides a flexible, declarative system for presenting content lists, keeping **content structure and presentation logic clearly separated** while avoiding the need for custom layout files.

The list system adapts automatically to its context (section pages, aggregated lists, nested content) and can be fine-tuned through explicit front matter configuration when needed.


### Default Behavior

Felmdrav automatically determines how a list should behave:

* On section pages (e.g. `/posts/`, `/press/`), all pages within that section are listed
* Nested content (e.g. `/posts/2026/01/...`) is included by default
* On non-section list pages, Felmdrav falls back to the site’s `mainSections` configuration

This makes the system suitable for WordPress-style blogs as well as multi-section corporate websites.


### List Configuration (`list`)

List behavior is controlled via the `list` object in a page’s front matter.

```yaml
list:
  recursive: true
  sort_by: date
```

All options are **optional**. When omitted, Felmdrav applies sensible defaults.


#### Available Options:

`recursive`: Controls whether subdirectories are included.
  - `true` (default): include all nested content
  - `false`: list only direct children

Example:

```yaml
list:
  recursive: false
```

`sections`: Builds a list from **multiple sections**.
  - Useful for aggregated news or update pages
  - Overrides section-based listing

Example:

```yaml
list:
  sections: ["posts", "presse"]
```

`mode`: Overrides automatic context detection.

  - `main_sections`: use `.Site.MainSections`
  - default behavior is context-aware and usually sufficient

Example:

```yaml
list:
  mode: main_sections
```


#### Sorting Options

Sorting can be customized per list.

`sort_by`: Defines the primary sort field.

Supported values:

* `date` (default)
* `weight`
* `title`

Example (alphabetical listing):

```yaml
list:
  sort_by: title
```

`sort_order`: Controls sort direction.

Supported values:

* `desc` (default)
* `asc`

Example (explicit ascending order):

```yaml
list:
  sort_by: title
  sort_order: asc
```

Note: Since `desc` is the default, it does not need to be specified explicitly.



### Examples

#### Corporate Blog

Lists all blog posts recursively, sorted by date descending (defaults applied).

```yaml
---
title: Corporate Blog
list:
  recursive: true
---
```

#### Support Products

Alphabetical listing of product documentation pages.

```yaml
---
title: Support Products
list:
  sort_by: title
  sort_order: asc
---
```

#### Aggregated News Page

Combines blog posts and press releases into a single feed.

```yaml
---
title: News
list:
  sections: ["posts", "presse"]
---
```

### Implementation Notes (for Developers)

Felmdrav implements content listings using a custom template setup built on top of Hugo’s list rendering mechanism.

* `layouts/list.html`
  This is the primary Hugo list template used by Felmdrav.

* `layouts/_partials/pages/list-content.html`
  This is a Felmdrav-specific partial containing the core list logic (page selection, recursion, sorting, pagination).

Hugo itself only invokes `list.html` automatically.
The `list-content.html` partial is explicitly included by Felmdrav to provide a reusable and extensible listing implementation.

Developers who want to customize or extend list behavior should start with `list-content.html`, as it encapsulates all list-related logic without requiring changes to content structure or additional layout files.


← Previous: [Content Blocks](blocks/README.md)
Next: [Typography](typography.md) →
