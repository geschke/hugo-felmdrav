
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


## Sidebar & Grid Layout Configuration

This theme provides a flexible but simple layout system based on **sidebars** and a **Bootstrap-style grid**.
Both can be configured globally (site-wide) and overridden per page.

The guiding principle is:

> **Page configuration always overrides site defaults.**


### Global Sidebar Configuration (Site Defaults)

Global defaults are defined in `config.toml`:

```toml
[params.sidebar]
  left  = ""
  right = "main"
```

* `left` / `right` define **which sidebar section** is rendered on each side.
* The value refers to a content section under:

  ```
  content/sections/sidebar-<name>/
  ```

  Example:

  ```toml
  right = "main"
  ```

  renders content from `content/sections/sidebar-main/`.

If a side is set to an empty string (`""`), no sidebar is rendered on that side.


### Global Grid Configuration

The grid controls the column widths (Bootstrap 12-column system):

```toml
[params.grid]
  left  = 3
  main  = 6
  right = 3
```

Rules:

* `main` must be greater than `0`
* `left` and `right` may be `0`
* The sum **must be exactly 12**

Valid examples:

* `3 / 6 / 3` (three columns)
* `0 / 9 / 3` (main + right sidebar)
* `4 / 8 / 0` (left sidebar + main)
* `0 / 12 / 0` (full width)


### Page-Level Sidebar Overrides (Front Matter)

A page can override the global sidebar configuration using `sidebar` in its front matter.

#### Enable or change sidebars

```yaml
sidebar:
  right: main
```

```yaml
sidebar:
  left: toc
  right: main
```

#### Disable all sidebars for a page

```yaml
sidebar: false
```

If `sidebar` is defined on the page, **global sidebar defaults are ignored**.


### Page-Level Grid Overrides

A page can also override the grid independently:

```yaml
grid:
  left: 0
  main: 8
  right: 4
```

This only affects column widths.
Sidebar visibility is still controlled by `sidebar`.



### Priority Rules (Important)

The effective layout is determined in this order:

1. **Page front matter (`sidebar`, `grid`)**
2. **Site defaults (`params.sidebar`, `params.grid`)**
3. Fallback to full width (`12`) if configuration is invalid

In short:

* Page settings **always win**
* Grid and sidebar are **independent**
* Invalid grid values automatically fall back to a safe layout



### Sidebar Content Structure

Sidebars are populated from content sections:

```
content/
└── sections/
    ├── sidebar-main/
    ├── sidebar-toc/
    └── sidebar-…
```

Each sidebar section can contain multiple content files, which are:

* sorted by `weight`
* then by filename



### Design Philosophy

This system is intentionally:

* **explicit** (no magic booleans)
* **predictable**
* **easy to reason about**
* **easy to override per page**

There is no legacy behavior and no implicit sidebar positioning logic.

--- 

← Previous: [Configuration](configuration.md)
Next: [Footer & Subfooter](footer-and-subfooter.md) →
