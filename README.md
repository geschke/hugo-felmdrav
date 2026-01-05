# Felmdrav - A Hugo Theme

Felmdrav is a clean and minimalistic Hugo theme, built on the
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

A live demo of the theme, based on the included `exampleSite`, is available here:

[https://geschke.github.io/hugo-felmdrav/](https://geschke.github.io/hugo-felmdrav/).


## Quick Start

### Install the theme

Inside the `themes` directory of your Hugo site, clone the repository:

```bash
cd themes
git clone https://github.com/geschke/hugo-felmdrav.git
```

Alternatively, you can add the theme as a Git submodule:

```bash
git submodule add https://github.com/geschke/hugo-felmdrav themes/hugo-felmdrav
```

Then reference the theme in your site configuration:

```toml
theme = "hugo-felmdrav"
```

### Run the example site

The repository includes a fully configured `exampleSite` which demonstrates
the available features of the theme.

From the repository root, run:

```bash
hugo server \
  --source exampleSite \
  --themesDir .. \
  --theme hugo-felmdrav
```

Then open:

```
http://localhost:1313/
```

## Configuration

Felmdrav is configured entirely via Hugo's standard `config.toml`.
The included `exampleSite` demonstrates all supported options
and serves as the primary reference configuration.

This section gives an overview of the most important configuration
areas. Detailed examples can be found directly in the `exampleSite/config.toml`.


### General Site Settings

Felmdrav relies on Hugo’s standard site configuration and does not introduce
custom behavior for core settings such as `baseURL`, `languageCode`, `title`
or taxonomies.

Pagination, multilingual configuration and content organization work exactly
as described in the Hugo documentation.

The theme supports multilingual sites using Hugo’s built-in language features.
Only a small number of theme-specific strings are translated. Additional
languages can be added by extending the theme’s language files.

Note: The `exampleSite` uses a very small pagination size to demonstrate
pagination behavior. In real projects, you will typically use a higher value.

### Theme Parameters

Felmdrav groups most theme-specific options under the `[params]` section.
These parameters control global behavior and a few presentation defaults that
apply site-wide.

The following options are commonly used:

- `subtitle`  
  Optional subtitle displayed below the site title.

- `append_site_title`  
  If enabled, the site title is appended to the HTML `<title>` tag of every page.

- `favicon`  
  Path to a favicon file located in the site’s `static` directory (e.g. `img/favicon.ico`).
  Leave empty to use no custom favicon.

- `date_format`  
  Controls how dates are rendered. The value uses Go’s time formatting syntax.

- `show_date`  
  Enables or disables the date on content summaries.  
  If enabled, content files should explicitly define a `date` in their front matter.

- `show_number_of_words`  
  Displays the word count on single content pages.

- `hide_meta`  
  Hides meta information (date, author, word count) on summaries and single pages.


### Navigation Bar

Felmdrav provides a configurable navigation bar based on Bootstrap utilities.
Navigation settings are defined under `[params.navbar]`.

- `style`  
  Navigation bar style. Supported values are `fixed-top` and `header`.  
  The theme default is `fixed-top`.

- `color_scheme`  
  Bootstrap navbar color scheme: `navbar-light` or `navbar-dark`.

- `bg_scheme`  
  Bootstrap background utility class (e.g. `bg-primary`).  
  See Bootstrap documentation for available `bg-*` utilities.

- `background_color`  
  Optional custom background color as a hex value (`#rrggbb`).  
  If set, this value is used for the background and overrides `bg_scheme`.

- `adjust_header`  
  Adds vertical spacing (in pixels) between navigation and content.  
  Some header/layout combinations require extra space; use an integer pixel value.

- `text_alignment`  
  Controls horizontal alignment of navigation items.  
  Leave empty for the default (left aligned), or use Bootstrap flex utilities
  such as `justify-content-end` or `justify-content-center`.

- `brand_image`  
  Optional brand icon shown next to the site title **in `fixed-top` mode**.
  The file must be located in the site’s `static` directory (e.g. `img/logo.png`).
  (Currently marked as TODO in the example configuration.)


### Meta Tags

Felmdrav allows defining custom meta tags that are injected into the HTML
`<head>` section of the site.

Meta tags are configured under the `[params.meta]` section. Each entry defines
a meta tag using the following structure:

```html
<meta name="key" content="value">
```

This mechanism can be used for standard meta information such as description
and keywords, as well as for custom or namespaced meta tags.

Example configuration:

```toml
[params.meta]
description = "Example meta description"
keywords = "example, site, theme, felmdrav"
author = "John Doe"
"DC.Copyright" = "Your Name"
```

All entries are rendered exactly as defined. The theme does not enforce or
validate specific meta keys.


### Theme Appearance

Visual appearance and global styling options are grouped under the
`[params.theme]` section. These settings control the overall look of the site,
including the Bootstrap color scheme and optional background styling.

#### Bootstrap Theme

Felmdrav supports multiple predefined Bootstrap color themes.

- `bootstrap_theme`  
  Selects the Bootstrap color theme used by the site.  
  Set an empty value to use the default Bootstrap styling.

The available themes correspond to predefined Bootstrap theme variants
included with Felmdrav.

#### Background Settings

- `background_color`  
  Sets a global background color using a hex value (`#rrggbb`).  
  Leave empty to use the theme default.

- `background_image`  
  Defines a background image located in the site’s `static` directory
  (e.g. `img/background.jpg`).

- `background_image_repeat`  
  Controls how the background image is repeated.  
  This value maps directly to the CSS `background-repeat` property
  (e.g. `no-repeat`, `repeat`, `repeat-x`, `repeat-y`).


### Header (Hero) Configuration

This section controls the global header / hero area at the top of the site.
The header is fully optional and can be enabled or disabled as a whole.

The header (hero) area is intentionally Bootstrap-first.
If no custom colors or styles are defined, all typography and colors are inherited from Bootstrap or the selected Bootswatch theme.
Header-specific options are designed to extend the default behavior, not to replace it.

- **`enabled`**
Enables or disables the complete header/hero area.
If set to `false`, the theme renders only the navigation bar without any hero section.

- **`image`**
Optional hero image displayed at the top of the page.
If an image is set and `text_on_image` is enabled, the site title and subtitle can be rendered as an overlay on top of this image.
If left empty, the header falls back to a text-only layout.

- **`alt_text`**
Alt text for the hero image.
This improves accessibility and should briefly describe the image content.
If left empty, no alt text is rendered.


#### Header Text Display

- **`show_text`**
Controls whether the site title and subtitle are rendered at all.
If set to `false`, the header image (if present) is shown without any text.

- **`text_on_image`**
Controls whether the title and subtitle are rendered as an overlay on top of the hero image.
If set to `false`, the text is rendered below the image instead.
If no image is configured, this option is ignored and the text is rendered normally.


#### Overlay Alignment

- **`overlay_alignment`**
Defines the position of the title and subtitle when they are rendered on top of the hero image.

  Available values:

  * `lt` – left / top
  * `mt` – center / top
  * `rt` – right / top
  * `lb` – left / bottom
  * `mb` – center / bottom
  * `rb` – right / bottom

  This option only applies when `text_on_image = true`.


#### Overlay Padding

- **`overlay_padding`**
Defines the inner padding of the hero text container when rendered on top of the image.
Use CSS units (recommended: `rem`) to control spacing around the title and subtitle.

This option helps improve readability and fine-tune the visual balance of the hero text against the background image.


### Header Backdrop (Optional Text Background)

This section controls an optional backdrop box behind the hero title and subtitle.
The backdrop is designed to improve text readability on complex or high-contrast images.

By default, the backdrop is disabled to keep the header clean and minimal.

- **`enabled`**
Enables or disables the backdrop box behind the header title and subtitle.
If set to `false`, no background box is rendered and the text is displayed directly on top of the image.

- **`color`**
Defines the background color of the backdrop box.
The value must be a hex color in `#rrggbb` format.
If left empty, the backdrop automatically falls back to the header title color.

- **`opacity`**
Controls the transparency of the backdrop box.
Valid values range from `0.0` (fully transparent) to `1.0` (fully opaque).
Lower values create a subtle background, higher values increase contrast and readability.

- **`radius`**
Defines the border radius of the backdrop box.
Use CSS units (for example `rem`) to control how rounded the box corners appear.

- **`padding`**
Defines the inner padding of the backdrop box.
This controls the spacing between the text and the edges of the backdrop background.


### Header Text Shadow (Optional)

This section controls an optional text shadow for the hero title and subtitle.
The text shadow can be used to improve readability on bright or high-contrast background images or to create stylistic effects.

By default, the text shadow is disabled to keep the header typography clean and modern.

- **`enabled`**
Enables or disables the text shadow for the header title and subtitle.
If set to `false`, no shadow is applied.

- **`color`**
Defines the color of the text shadow.
The value must be a hex color in `#rrggbb` format.
If left empty, the shadow color falls back to the header title color.

- **`opacity`**
Controls the opacity of the text shadow.
Valid values range from `0.0` (fully transparent) to `1.0` (fully opaque).
Higher values result in a stronger, more visible shadow effect.


### Header Colors (Optional Overrides)

This section allows optional color overrides for the header text and background.
If no values are set, the theme uses the default colors provided by Bootstrap or the selected Bootswatch theme.

- **`title`**
Defines the text color of the header title.
The value must be a hex color in `#rrggbb` format.
If left empty, the default Bootstrap text or link color is used.

- **`subtitle`**
Defines the text color of the header subtitle.
The value must be a hex color in `#rrggbb` format.
If left empty, the default Bootstrap text color is used.

- **`background_color`**
Defines the background color of the entire header area.
This color is applied behind the hero image or text-only header.
If left empty, the background color is inherited from Bootstrap defaults or the page background.


### Header Typography (Hero Title and Subtitle)

This section controls the typography of the hero title and subtitle.
The theme uses modern, fluid typography based on CSS `clamp()` to adapt smoothly across different screen sizes without relying on media queries.

**Font weights**

- **`title_weight`**
Defines the font weight of the hero title.
If not set, the default font weight defined by the theme or Bootstrap is used.

- **`subtitle_weight`**
Defines the font weight of the hero subtitle.
If not set, the default font weight defined by the theme or Bootstrap is used.


**Responsive font sizes**

- **`title_min`**
Defines the minimum font size of the hero title.
This size is used on very small screens.

- **`title_max`**
Defines the maximum font size of the hero title.
This size is used on large screens.

- **`subtitle_min`**
Defines the minimum font size of the hero subtitle.

- **`subtitle_max`**
Defines the maximum font size of the hero subtitle.

All size values should use CSS units, with `rem` being the recommended choice.


**Text layout and wrapping**

- **`text_max_width`**
Limits the maximum line length of the hero text container.
This helps maintain readability on very wide screens.

- **`title_nowrap`**
Prevents the hero title from wrapping onto multiple lines on large screens.
This is useful for short titles that should remain on a single line for visual impact.


All color values must be provided as hex colors (`#rrggbb`).
Other color formats are not supported.

Advanced customization can always be done by overriding the theme CSS.
The configuration options are designed to cover common use cases without adding unnecessary complexity.


### Footer and Subfooter

Felmdrav renders footer and subfooter content using **headless page bundles**.
Both sections are content-driven and are only rendered if the corresponding
content structure exists and the section is enabled in the configuration.

#### Footer

The footer is a multi-column content area rendered at the bottom of each page.

Footer content is loaded from:

```
content/sections/footer/
```

The directory must contain an `index.md` file with the front matter option
`headless: true`. Without this setting, the footer will not be rendered.

Each additional Markdown or HTML file inside the directory is rendered as a
single footer column.

A typical structure looks like this:

```
content/sections/footer/
                       ├── index.md
                       ├── col1.md
                       ├── col2.md
                       └── col3.md
```

The required `index.md` file must contain at least:

```md
---
title: "Footer"
headless: true
---
```


Each footer column is defined by a single content file inside the footer
directory. These files may contain a small front matter header.

A typical footer content file looks like this:

```md
---
title: "About"
weight: 10
---

Some footer text or links.
```

The following front matter options are supported:

- `title`
Optional title of the footer column.
If set, it is typically rendered as the column heading.

- `weight`
Optional numeric value used to control column ordering.
Lower values are rendered first.

If no `weight` is defined, footer columns are ordered by filename or title.
Using `weight` is recommended to ensure a predictable and stable layout.


Footer appearance is controlled via:

```toml
[params.theme.footer]
enabled = true
font_color = ""
link_color = ""
background_color = ""
background_class = ""
```

To customize how individual footer columns are rendered, override the following
partial in your site project:

```
layouts/partials/footer_column.html
```


#### Subfooter

The subfooter is rendered below the footer and is typically used for small
meta information such as copyright notices or legal links.

Subfooter content is loaded from:

```
content/sections/subfooter/
```

As with the footer, the directory must contain an `index.md` file with
`headless: true`. Without this setting, the subfooter will not be rendered.

Each additional Markdown or HTML file inside the directory is rendered as a
single subfooter item.

Subfooter content files use the **same front matter structure and ordering
rules as footer content files**.
This includes support for optional `title` and `weight` fields to control
display and ordering. See the **Footer** section above for details.

Subfooter appearance is controlled via:

```toml
[params.theme.subfooter]
enabled = true
font_color = ""
link_color = ""
background_color = ""
background_class = ""
```

To customize how individual subfooter items are rendered, override:

```
layouts/partials/subfooter_item.html
```

### Typography

Felmdrav allows fine-grained font configuration for different parts of the site.
All typography-related options are grouped under the `[params.fonts]` section.

Fonts can be defined independently for the following areas:

* header title
* header subtitle
* navigation bar
* body text
* headlines (h1–h6)

Both system fonts and Google Fonts are supported.

#### Header Title

* `header_title`
  Font family used for the site title in the header.
  Any valid CSS `font-family` value can be used.

* `header_title_googlefont`
  Set to `true` if the selected font is a Google Font.
  If enabled, the font will be loaded automatically.

* `header_title_variant`
  Font weight or variant (for example `regular`, `600`, `800`).
  Availability depends on the selected font.


#### Header Subtitle

* `header_subtitle`
  Font family used for the subtitle.

* `header_subtitle_googlefont`
  Enable Google Font loading for the subtitle font.

* `header_subtitle_variant`
  Font weight or variant for the subtitle.


#### Navigation Bar

* `navbar`
  Font family used for navigation items.

* `navbar_googlefont`
  Enable Google Font loading for the navigation font.

* `navbar_variant`
  Font weight or variant for the navigation font.

* `navbar_size`
  Font size for navigation items.

#### Body Text

* `body`
  Font family used for main content text.

* `body_googlefont`
  Enable Google Font loading for the body font.

* `body_variant`
  Font weight or variant for body text.

* `body_size`
  Font size for body text.

#### Headlines (h1–h6)

* `headline`
  Font family used for headlines.

* `headline_googlefont`
  Enable Google Font loading for the headline font.

* `headline_variant`
  Font weight or variant for headlines.

* `headline_base_size`
  Base font size used to calculate the sizes of h1–h6.
  The actual sizes are derived using the same scaling factors as the CSS
  framework.
  Set this value to `0` to use the theme default.



### Sidebar & Grid Layout Configuration

This theme provides a flexible but simple layout system based on **sidebars** and a **Bootstrap-style grid**.
Both can be configured globally (site-wide) and overridden per page.

The guiding principle is:

> **Page configuration always overrides site defaults.**


#### 1. Global Sidebar Configuration (Site Defaults)

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


#### 2. Global Grid Configuration

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


#### 3. Page-Level Sidebar Overrides (Front Matter)

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

##### Disable all sidebars for a page

```yaml
sidebar: false
```

If `sidebar` is defined on the page, **global sidebar defaults are ignored**.


#### 4. Page-Level Grid Overrides

A page can also override the grid independently:

```yaml
grid:
  left: 0
  main: 8
  right: 4
```

This only affects column widths.
Sidebar visibility is still controlled by `sidebar`.



#### 5. Priority Rules (Important)

The effective layout is determined in this order:

1. **Page front matter (`sidebar`, `grid`)**
2. **Site defaults (`params.sidebar`, `params.grid`)**
3. Fallback to full width (`12`) if configuration is invalid

In short:

* Page settings **always win**
* Grid and sidebar are **independent**
* Invalid grid values automatically fall back to a safe layout



#### 6. Sidebar Content Structure

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



#### 7. Design Philosophy

This system is intentionally:

* **explicit** (no magic booleans)
* **predictable**
* **easy to reason about**
* **easy to override per page**

There is no legacy behavior and no implicit sidebar positioning logic.

### Analytics

Felmdrav supports web analytics using Hugo’s built-in features and optional
theme-specific integrations.

#### Google Analytics

Google Analytics is handled via Hugo’s internal templates.
To enable it, set the `googleAnalytics` option at the **top level** of your
`config.toml` (not inside `[params]`).

Example:

```toml
googleAnalytics = "UA-123-45"
```

Felmdrav does not modify or wrap Hugo’s Google Analytics integration.
Behavior is identical to the standard Hugo implementation.

#### Matomo

Felmdrav includes built-in support for Matomo analytics.

Matomo settings are configured under the following section:

```toml
[params.analytics.matomo]
enabled = false
url = "https://analytics.example.com"
site_id = 0
```

* `enabled`
  Enables or disables Matomo tracking.

* `url`
  Base URL of the Matomo instance.

* `site_id`
  Numeric site ID as defined in Matomo.

#### Custom Analytics Snippets

If you require a custom Matomo setup or want to use a different analytics
solution, you can override the analytics partials provided by the theme.

Custom snippets can be added by placing your own files in:

```
layouts/partials/analytics/
```

Hugo’s lookup order ensures that your custom partials are used instead of the
theme defaults.


### Image Processing

Felmdrav can optionally use image processing features from the upstream project
*hugo-theme-bootstrap* (HBS). This allows extended rendering behavior for images
embedded in Markdown content.

Image processing settings are configured under:

```toml
[params.images]
extended_rendering = false
```

* `extended_rendering`
  Enables extended image rendering.
  The backward-compatible default is `false`. Set to `true` to activate the
  extended rendering functions.

If enabled, images may be rendered with additional processing behavior as
documented by HBS. See the upstream documentation for details:

[https://hbs.razonyang.com/v1/en/docs/image-processing/](https://hbs.razonyang.com/v1/en/docs/image-processing/)


### Post Options

Post-related options are configured under:

```toml
[params.post]
image_title_as_caption = false
```

* `image_title_as_caption`
  If enabled, the image title is used as the caption.

Markdown example:

```md
![Image Caption](/image.jpg "This is my image title as caption")
```

When `image_title_as_caption` is set to `true`, the theme uses the image title
string (`"..."`) as the rendered caption.


### Menus

Felmdrav uses Hugo’s standard menu configuration. Menus can be defined in
`config.toml` (as shown in the `exampleSite`) or directly in content front
matter.

Example configuration:

```toml
[menu]

  [[menu.main]]
    identifier = "home"
    name = "Home"
    url = "/"
    weight = 10

  [[menu.main]]
    identifier = "posts"
    name = "Blog"
    url = "/posts/"
    weight = 20
```

For advanced menu features (nested menus, `pageRef`, multilingual menus, etc.),
refer to the Hugo documentation:

[https://gohugo.io/content-management/menus/](https://gohugo.io/content-management/menus/)


### Taxonomies

Felmdrav uses Hugo’s standard taxonomy configuration. Taxonomies are defined at
the top level of `config.toml`:

```toml
[taxonomies]
category = "categories"
tag = "tags"
series = "series"
```

For details on configuring and using taxonomies, refer to the Hugo
documentation:

[https://gohugo.io/content-management/taxonomies/](https://gohugo.io/content-management/taxonomies/)



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

---

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


## Content Blocks Reference

### Block: `hero-split`

Two-column hero block with text and optional buttons on the left and an optional image on the right.

#### Usage

* Home page: `type: hero-split`, `content: blocks/<name>`
* Markdown: `{{< block type="hero-split" content="blocks/<name>" >}}`

---

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


### Block: `hero-centered`

Centered hero block with optional buttons and an optional image displayed below the text.

#### Usage

* Home page: `type: hero-centered`, `content: blocks/<name>`
* Markdown: `{{< block type="hero-centered" content="blocks/<name>" >}}`


#### Block Content (`content/blocks/<name>/index.md`)

Configured via front matter only.

**Fields:**

* **title**
  Main heading of the hero block (page title). Rendered as centered `<h1>`. *(optional)*

* **lead**
  Short descriptive text displayed below the title. Rendered as a centered Bootstrap `lead` paragraph (muted). *(optional)*

* **buttons**
  Optional list of call-to-action buttons (centered).

  Each button defines:

  * `text` – button label
  * `ref` or `url` – internal reference or external link
  * `style` – Bootstrap button style (default: `primary`)

* **image**
  Optional image shown **below** the text/buttons (centered).

  Fields:

  * `src` – image filename, relative path, or URL
  * `alt` – alternative text used for accessibility and SEO *(optional)*

  If `src` matches a page resource of the block content page, that resource is used.
  Otherwise, the value is treated as a regular path or URL.

#### Example

```
---
title: "Felmdrav in a nutshell"
lead: "Centered hero layout with optional buttons and a framed image."
buttons:
  - text: "Documentation"
    ref: "posts"
    style: "primary"
  - text: "About"
    ref: "about"
    style: "outline-secondary"
image:
  src: "hero.png"
  alt: "Preview image"
---
```

#### Notes

* Layout is centered (`text-center`) with a constrained text width (`col-lg-8 col-md-10 mx-auto`).
* The image is rendered only if `image.src` is set; it is displayed below the content with rounded corners and a border.
* If the block content page cannot be resolved, nothing is rendered.


### Block: `features-icons`

Icon-based feature list displayed in a responsive grid layout. Each feature consists of an icon, title, text, and an optional link.

#### Usage

* Home page: `type: features-icons`, `content: blocks/<name>`
* Markdown: `{{< block type="features-icons" content="blocks/<name>" >}}`


#### Block Content (`content/blocks/<name>/index.md`)

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


#### Notes

* Icons use **Bootstrap Icons**.
* The grid adapts responsively using Bootstrap’s `row-cols-*` classes.
* If no link is defined for an item, it is rendered as plain content.
* If the block content page cannot be resolved, nothing is rendered.



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



### Block: `features-cards`

Card-based feature grid. Each item is rendered as a visual card with optional background image, optional tags, and an optional link (clickable whole card).

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

  * `title` – card title *(optional)*
  * `text` – short card text *(optional)*
  * `image` – background image filename/path/URL *(optional)*
  * `tags` – list of short labels rendered as badges *(optional)*
  * `link` – optional click target for the whole card (see below)

**Link fields (per item):**

* `ref` or `url` – internal reference or external link
  If defined, the entire card becomes clickable via a stretched link.

**Image behavior (per item):**

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


#### Example

```
---
title: "Custom cards"
items:
  - title: "Matrix-like visuals"
    text: "Abstract code fragments and digital noise as background."
    image: "card-1.png"
    tags: ["Design", "Visual"]
    link:
      ref: "posts"
  - title: "Readable layouts"
    text: "Cards stay structured even with longer text."
    tags: ["UX"]
  - title: "Theme building blocks"
    text: "Compose pages from reusable content blocks."
    image: "card-2.png"
    link:
      url: "https://example.com"
---
```


#### Notes

* If no `link` is defined, the card is rendered as a non-clickable element.
* If no `image` is defined, the card is rendered without a background image.
* Tags are rendered as Bootstrap badges at the bottom of the card.
* If the block content page cannot be resolved, nothing is rendered.


## Migration from Tikva

Felmdrav evolved from the earlier Tikva theme, but it is **not** a drop-in
replacement. A migration usually means: keep your content, then adapt
configuration, layout, icons and any template overrides.

### Breaking changes and key differences

**Icons: Font Awesome → Bootstrap Icons**
Felmdrav uses **Bootstrap Icons** instead of Font Awesome. If your Tikva-based
site includes Font Awesome assets or uses FA class names, you will need to
replace them with Bootstrap Icons equivalents.

**Bootstrap version: Bootstrap 5**
Felmdrav is built around **Bootstrap 5**. Utility class names, layout helpers
and component markup follow Bootstrap 5 conventions. If your site relied on
Bootstrap 4 behavior or custom CSS targeting older Bootstrap markup, review and
adjust accordingly.

**Sidebars and layout: one sidebar → two sidebars + grid**
Tikva used a simpler sidebar approach. Felmdrav supports **two sidebars**
(left/right) and a configurable **grid layout**.

Sidebar content is loaded from headless bundles under `content/sections/`, but
the **directory names depend on the configured sidebar identifiers**.
If your configuration defines a sidebar name like `sidebar-main`, then the
corresponding content directory must be named exactly the same, otherwise the
sidebar will not render.

**Configuration keys renamed (snake_case)**
Felmdrav uses a consistent naming convention: all theme configuration keys are
lowercase and use **snake_case**. Do not expect Tikva parameter names to work.
Use the `exampleSite/config.toml` as the authoritative reference and transfer
settings manually.

**New content blocks (e.g. Hero / Features)**
Felmdrav introduces additional optional layout blocks (for example Hero and
Features). If you want to use them, you will need to add the corresponding
content and configuration as described in the Felmdrav documentation/examples.

**Template structure and overrides**
Felmdrav’s template/partial structure differs from Tikva. If you previously
overrode theme templates (partials, list/single templates, shortcodes, etc.),
those overrides may no longer apply because:

* file names may have changed
* partial paths may have changed
* template context or expected parameters may have changed

Review your `layouts/` overrides and port them to Felmdrav’s structure.

### Recommended migration steps

1. Switch the theme and start from the reference config
   Use `exampleSite/config.toml` as a baseline and migrate your settings
   section by section.

2. Update icons
   Remove Font Awesome usage and replace icon markup with Bootstrap Icons.

3. Rebuild layout configuration
   Configure the grid and sidebars. Make sure your sidebar content directories
   match the sidebar identifiers from the configuration exactly.

4. Port template overrides (if you have any)
   Compare your overridden templates in `layouts/` with Felmdrav’s templates and
   re-apply changes to the new file structure.

5. Validate pages and styles
   Check header/navbar behavior, typography, and custom CSS/JS. Verify that any
   Bootstrap utility classes you use match Bootstrap 5.

### Notes

Felmdrav does not aim to preserve one-to-one compatibility with Tikva’s
configuration or template structure. The most reliable migration approach is:
keep your content, then re-apply your layout and design preferences using
Felmdrav’s configuration and templates.


## License

Open sourced under the [MIT license](./LICENSE.md).

## Contributing

If you find a bug or have an idea for a feature, feel free to use the [issue tracker](https://github.com/geschke/hugo-felmdrav/issues) to let me know.

## Thanks to / Used third-party components

* The [Bootstrap](https://getbootstrap.com) project, which is licensed under the MIT license
* [Bootstrap Icons](https://icons.getbootstrap.com/)
* Thomas Park and the contributors of the [Bootswatch](https://bootswatch.com/) project
* Image render hook from [hugo-theme-bootstrap](https://github.com/razonyang/hugo-theme-bootstrap) by Razon Yang
