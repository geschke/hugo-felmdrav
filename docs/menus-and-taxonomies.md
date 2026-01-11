
## Menus

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


## Taxonomies

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

