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



## Analytics

Felmdrav supports web analytics using Hugo’s built-in features and optional
theme-specific integrations.

### Google Analytics

Google Analytics is handled via Hugo’s internal templates.
To enable it, set the `googleAnalytics` option at the **top level** of your
`config.toml` (not inside `[params]`).

Example:

```toml
googleAnalytics = "UA-123-45"
```

Felmdrav does not modify or wrap Hugo’s Google Analytics integration.
Behavior is identical to the standard Hugo implementation.

### Matomo

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

### Custom Analytics Snippets

If you require a custom Matomo setup or want to use a different analytics
solution, you can override the analytics partials provided by the theme.

Custom snippets can be added by placing your own files in:

```
layouts/partials/analytics/
```

Hugo’s lookup order ensures that your custom partials are used instead of the
theme defaults.

--- 

← Previous: [Image Processing](images.md)
Next: [Menus & Taxonomies](menus-and-taxonomies.md) →
