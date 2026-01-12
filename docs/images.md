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



## Image Processing

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


## Post Options

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

--- 

← Previous: [Typography](typography.md)
Next: [Analytics](analytics.md) →
