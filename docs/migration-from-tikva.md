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

**Sidebars and layout: one sidebar ->  two sidebars + grid**
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



--- 

← Previous: [Menus & Taxonomies](menus-and-taxonomies.md)
