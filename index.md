---
layout: default
---

> Have you ever tried to find a lightweight yet nice theme for the R Markdown
documents, like [this page](cayman.html)?

## Themes for R Markdown

With the powerful [rmarkdown](https://rmarkdown.rstudio.com/index.html)
package, we could easily create nice HTML document
by adding some meta information in the header, for example

```yaml
---
title: Nineteen Years Later
author: Harry Potter
date: July 31, 2016
output:
  rmarkdown::html_document:
    theme: lumen
---
```

The [html_document](https://bookdown.org/yihui/rmarkdown/html-document.html)
engine uses the [Bootswatch](https://bootswatch.com/)
theme library to support different styles of the document.
This is a quick and easy way to tune the appearance of your document, yet with
the price of a large file size (> 700KB) since the whole
[Bootstrap](https://getbootstrap.com/) library needs to be packed in.

For package vignettes, we can use the
[html_vignette](https://bookdown.org/yihui/rmarkdown/r-package-vignette.html)
engine to generate a more lightweight HTML file that is meant to minimize the
package size, but the output HTML is less stylish than the `html_document` ones.

So can we do **BOTH**, a lightweight yet nice-looking theme for R Markdown?

## The prettydoc Engine

The answer is YES! (At least towards that direction)

The **prettydoc** package provides an alternative engine, `html_pretty`,
to knit your R Markdown document into pretty HTML pages.
Its usage is extremely easy: simply replace the
`rmarkdown::html_document` or `rmarkdown::html_vignette` output engine by
`prettydoc::html_pretty` in your R Markdown header, and use one of the built-in
themes and syntax highlighters. For example

```yaml
---
title: Nineteen Years Later
author: Harry Potter
date: July 31, 2016
output:
  prettydoc::html_pretty:
    theme: cayman
    highlight: github
---
```

You can also create documents from **prettydoc** templates in RStudio.

**Step 1:** Click the "New File" button and choose "R Markdown".

<div class="gallery">
  <img src="images/step1.png" alt="Step 1" />
</div>

**Step 2:** In the "From Template" tab, choose one of the built-in templates.

<div class="gallery">
  <img src="images/step2.png" alt="Step 2" />
</div>

## Options and Themes

The options for the `html_pretty` engine are mostly compatible with the default
`html_document`
(see the [documentation](https://bookdown.org/yihui/rmarkdown/html-document.html))
with a few exceptions:

1. Currently the `theme` option can take the following values. More themes will
be added in the future.
    - `cayman`: Modified from the [Cayman](https://github.com/jasonlong/cayman-theme) theme.
    - `tactile`: Modified from the [Tactile](https://github.com/jasonlong/tactile-theme) theme.
    - `architect`: Modified from the [Architect](https://github.com/jasonlong/architect-theme) theme.
    - `leonids`: Modified from the [Leonids](https://github.com/renyuanz/leonids) theme.
    - `hpstr`: Modified from the [HPSTR](https://github.com/mmistakes/hpstr-jekyll-theme) theme.
2. The `highlight` option takes value from `github` and `vignette`.
3. A new `math` parameter to choose between `mathjax` and `katex` for rendering math expressions.
   The `katex` option supports offline display when there is no internet connection.
4. Options `code_folding`, `code_download` and `toc_float` are not applicable.

See the [Themes](themes.html) page for an overview of the available themes in
**prettydoc**.
