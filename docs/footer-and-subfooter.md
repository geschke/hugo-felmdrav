
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
