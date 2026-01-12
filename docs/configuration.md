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


#### Header Backdrop (Optional Text Background)

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


#### Header Text Shadow (Optional)

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


#### Header Colors (Optional Overrides)

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


#### Header Typography (Hero Title and Subtitle)

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


#### Page-level header overrides

 By default, the header displays the site title and subtitle as defined in the global configuration.

 Individual pages may override this behavior using the `header` section in front matter:

 * `header.title` and `header.subtitle` override the global values
 * setting a value to an empty string disables it explicitly
 * `header.show: false` hides the header text (title and subtitle) while keeping the header layout intact


---

Next: [Layout & Sidebars](layout-and-sidebars.md) →
