# Felmdrav Theme for Hugo


Felmdrav is a clean and minimalistic theme for Hugo, built on the
[Bootstrap v5](https://getbootstrap.com/) CSS framework.

Felmdrav originates from **Tikva**, a theme originally developed by the author for **Grav CMS** and later ported to **Hugo**.
The Hugo version of Tikva was based on **Bootstrap 4** and selectively incorporated concepts from a parallel Bootstrap-based **WordPress** implementation of the same theme.

The Tikva theme for Hugo remains available but is now considered **deprecated**.

When migrating the Hugo theme from Bootstrap 4 to **Bootstrap 5**, it became clear that the required changes would not be backward-compatible. In addition to the framework upgrade, several structural improvements were introduced, including a more flexible grid system, configurable sidebars, updated icon handling, and additional content blocks.

To clearly distinguish this modernized Hugo theme from its predecessor, the project was renamed to **Felmdrav**, which is now the **Bootstrap 5–based successor of Tikva for Hugo**.

## Evolution and Design Goals

While Felmdrav retains the minimalist design principles of Tikva, it introduces several structural and technical improvements tailored specifically for Hugo:

* Migration to **Bootstrap 5** with a clean, modern markup
* A **flexible grid system** based on Bootstrap’s 12-column layout
* **Configurable sidebars** with global defaults and per-page overrides
* Replacement of Font Awesome with **Bootstrap Icons**
* A small set of reusable **content blocks**, such as hero sections and feature/icon blocks
* Integration of multiple **Bootswatch** styles with additional custom refinements
* Optional color and style adjustments via configuration

The focus is on **clarity, predictability, and extensibility**, rather than feature overload or heavy abstraction.

---

## Philosophy

Felmdrav aims to stay:

* minimal in structure
* explicit in configuration
* easy to reason about
* flexible without becoming complex

Most layout behavior is controlled through clear configuration options, avoiding hidden defaults or implicit logic wherever possible.




## Features

* Responsive, mobile-first design based on **Bootstrap 5**
* Flexible **grid system** using Bootstrap’s 12-column layout
* Configurable **sidebars** with global defaults and per-page overrides
* Support for **one-, two- and three-column layouts**
* Integration of **Bootstrap Icons** (no Font Awesome dependency)
* Multiple built-in visual styles, including selected **Bootswatch** themes
* Reusable **content blocks** (e.g. hero sections, feature/icon blocks)
* Customizable typography settings, including **Google Fonts** support
* Flexible footer and optional subfooter areas
* Optional analytics integration (Google Analytics, Matomo)
* Support for custom CSS and JavaScript via placeholder partials


## Demo

You can find a demo [here](https://themes.gohugo.io/theme/hugo-felmdrav/).

## Screenshots

Some examples of different designs:

* "header" style, header image and "darkly" theme:

![preview](https://raw.githubusercontent.com/geschke/hugo-felmdrav/master/images/screenshot.png)

* "fixed-top" style, with "flatly" theme and customized footer colors:

![preview](https://raw.githubusercontent.com/geschke/hugo-felmdrav/master/images/screenshot01.png)

* "header" style, header image, title above header image, "signa" theme:

![preview](https://raw.githubusercontent.com/geschke/hugo-felmdrav/master/images/screenshot02.png)

* "header" style, header image, title and subtitle as overlay, "materia" theme:

![preview](https://raw.githubusercontent.com/geschke/hugo-felmdrav/master/images/screenshot03.png)

## Installation

Inside the folder of your Hugo site run:

```bash
    cd themes
    git clone https://github.com/geschke/hugo-felmdrav.git
```

As a second option you can use the submodule feature of Git:

```bash
    git submodule add -f https://github.com/geschke/hugo-felmdrav themes/hugo-felmdrav
```

For more information read the official [setup guide](//gohugo.io/overview/installing/) of Hugo.

## Configuration

Check out `exampleSite/config.toml` for theme configuration options and the contents of `exampleSite` folder.

I've tried to comment as much as possible in the configuration file, but the theme and documentation are far away from being complete. It is still work in progress and currently some features of Hugo aren't supported.


---

## Sidebar & Grid Layout Configuration

This theme provides a flexible but simple layout system based on **sidebars** and a **Bootstrap-style grid**.
Both can be configured globally (site-wide) and overridden per page.

The guiding principle is:

> **Page configuration always overrides site defaults.**

---

### 1. Global Sidebar Configuration (Site Defaults)

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

  → renders content from `content/sections/sidebar-main/`.

If a side is set to an empty string (`""`), no sidebar is rendered on that side.

---

### 2. Global Grid Configuration

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

---

### 3. Page-Level Sidebar Overrides (Front Matter)

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

---

### 4. Page-Level Grid Overrides

A page can also override the grid independently:

```yaml
grid:
  left: 0
  main: 8
  right: 4
```

This only affects column widths.
Sidebar visibility is still controlled by `sidebar`.

---

### 5. Priority Rules (Important)

The effective layout is determined in this order:

1. **Page front matter (`sidebar`, `grid`)**
2. **Site defaults (`params.sidebar`, `params.grid`)**
3. Fallback to full width (`12`) if configuration is invalid

In short:

* Page settings **always win**
* Grid and sidebar are **independent**
* Invalid grid values automatically fall back to a safe layout

---

### 6. Sidebar Content Structure

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

---

### 7. Design Philosophy

This system is intentionally:

* **explicit** (no magic booleans)
* **predictable**
* **easy to reason about**
* **easy to override per page**

There is no legacy behavior and no implicit sidebar positioning logic.



--- 

### Sections (Sidebars, Footer, Subfooter)

As you can see in the screenshots this theme supports three content sections which aren't shown in the demo site, because in the demo only the default content is used. To enable the sections, create a folder `sections` into your content folder. Then create one or more content folders in the `sections` folder with their special names `footer`, `sidebar` and `subfooter`. In every of these folders you can place any page content you want, make the page bundle "headless" and enable the section (footer, subfooter, sidebars) in the site config file.

For a complete example please have a look at the `exampleSite` folder. The directory structure is at follows:

```
content/
        [...]
        sections/
                 footer/
                        column01.md
                        column02.md
                        column03.md
                        index.md
                        [...]
                 sidebar/
                         content01.md
                         content02.html
                         index.md
                 subfooter/
                          content.md
                          index.md
                [...]
```

To activate the content sections, enable them in your config file:

```
[params.theme.footer]
    enabled = true # Show the footer part
    #numberColumns = 3 # Set number of columns available in footer of a page. Use the "footer" folder in the page structure to add content. If nothing is set, the default number is 3. Currently.i.e. since v0.2 not used, the number of columns is identical to the number of files in footer directory.
 
[...]

[params.theme.subfooter]
    enabled = true # Show the content below the footer
[...]


[params.sidebar]
    enabled = true # default false; set to true to enable sidebar
    style = 'right' # options: 'left', 'right'. Left means sidebar on the left side, right displays the sidebar on the right side


```

## Menu

The navbar displays the `main` menus by default. You can find more details about how to configure it [here](https://gohugo.io/templates/menu-templates/), as well as in the `exampleSite`.

## License

Open sourced under the [MIT license](./LICENSE.md).

## Contributing

If you find a bug or have an idea for a feature, feel free to use the [issue tracker](https://github.com/geschke/hugo-felmdrav/issues) to let me know.

## Thanks to / Used third-party components

* The [Bootstrap](https://getbootstrap.com) project, which is licensed under the MIT license
* [Bootstrap Icons](https://icons.getbootstrap.com/)
* Thomas Park and the contributors of the [Bootswatch](https://bootswatch.com/) project
* Image render hook from [hugo-theme-bootstrap](https://github.com/razonyang/hugo-theme-bootstrap) by Razon Yang
