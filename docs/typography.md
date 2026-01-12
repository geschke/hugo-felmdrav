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


## Typography

Felmdrav allows fine-grained font configuration for different parts of the site.
All typography-related options are grouped under the `[params.fonts]` section.

Fonts can be defined independently for the following areas:

* header title
* header subtitle
* navigation bar
* body text
* headlines (h1–h6)

Both system fonts and Google Fonts are supported.

### Header Title

* `header_title`
  Font family used for the site title in the header.
  Any valid CSS `font-family` value can be used.

* `header_title_googlefont`
  Set to `true` if the selected font is a Google Font.
  If enabled, the font will be loaded automatically.

* `header_title_variant`
  Font weight or variant (for example `regular`, `600`, `800`).
  Availability depends on the selected font.


### Header Subtitle

* `header_subtitle`
  Font family used for the subtitle.

* `header_subtitle_googlefont`
  Enable Google Font loading for the subtitle font.

* `header_subtitle_variant`
  Font weight or variant for the subtitle.


### Navigation Bar

* `navbar`
  Font family used for navigation items.

* `navbar_googlefont`
  Enable Google Font loading for the navigation font.

* `navbar_variant`
  Font weight or variant for the navigation font.

* `navbar_size`
  Font size for navigation items.

### Body Text

* `body`
  Font family used for main content text.

* `body_googlefont`
  Enable Google Font loading for the body font.

* `body_variant`
  Font weight or variant for body text.

* `body_size`
  Font size for body text.

### Headlines (h1–h6)

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

--- 

← Previous: [Content Lists](content-lists.md)
Next: [Image Processing](images.md) →
