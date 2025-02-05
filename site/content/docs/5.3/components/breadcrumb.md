---
layout: docs
title: Breadcrumb
description: Indicate the current page's location within a navigational hierarchy that automatically adds separators via CSS.
group: components
aliases:
  - "/docs/components/breadcrumb/"
toc: true
---

## Example

Use an ordered or unordered list with linked list items to create a minimally styled breadcrumb. Use our utilities to add additional styles as desired.

{{< example >}}
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item active" aria-current="page">Home</li>
  </ol>
</nav>

<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>

<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item"><a href="#">Library</a></li>
    <li class="breadcrumb-item active" aria-current="page">Data</li>
  </ol>
</nav>
{{< /example >}}

## Dividers

Dividers are automatically added in CSS through [`::before`](https://developer.mozilla.org/en-US/docs/Web/CSS/::before) and [`content`](https://developer.mozilla.org/en-US/docs/Web/CSS/content). They can be changed by modifying a local CSS custom property `--bs-breadcrumb-divider`, or through the `$breadcrumb-divider` Sass variable — and `$breadcrumb-divider-flipped` for its RTL counterpart, if needed. We default to our Sass variable, which is set as a fallback to the custom property. This way, you get a global divider that you can override without recompiling CSS at any time.

{{< example >}}
<nav style="--bs-breadcrumb-divider: '>';" aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>
{{< /example >}}

When modifying via Sass, the [quote](https://sass-lang.com/documentation/modules/string#quote) function is required to generate the quotes around a string. For example, using `>` as the divider, you can use this:

```scss
$breadcrumb-divider: quote(">");
```

It's also possible to use an **embedded SVG icon**. Apply it via our CSS custom property, or use the Sass variable.

{{< callout info >}}
**Inlined SVG requires properly escaped characters.** Some reserved characters, such as `<`, `>` and `#`, must be URL-encoded or escaped. We do this with the `$breadcrumb-divider` variable using our [`escape-svg()` Sass function]({{< docsref "/customize/sass#escape-svg" >}}). When customizing the CSS variable, you must handle this yourself. Read [Kevin Weber's explanations on CodePen](https://codepen.io/kevinweber/pen/dXWoRw ) for more info.
{{< /callout >}}

{{< example >}}
<nav style="--bs-breadcrumb-divider: url(&#34;data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='8' height='8'%3E%3Cpath d='M2.5 0L1 1.5 3.5 4 1 6.5 2.5 8l4-4-4-4z' fill='%23000000'/%3E%3C/svg%3E&#34;);" aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>
{{< /example >}}

```scss
$breadcrumb-divider: url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' width='8' height='8'><path d='M2.5 0L1 1.5 3.5 4 1 6.5 2.5 8l4-4-4-4z' fill='#{$breadcrumb-divider-color}'/></svg>");
```

You can also remove the divider setting `--bs-breadcrumb-divider: '';` (empty strings in CSS custom properties counts as a value), or setting the Sass variable to `$breadcrumb-divider: none;`.

{{< design-callout-alert >}}
This variant **without the breadcrumb dividers** should not be used because it does not respect the Orange Design System specifications.

Please refer to the [Local Headers/Breadcrumb](https://system.design.orange.com/0c1af118d/p/774477-local-headers/b/743cd0/i/66611057) guidelines on the Orange Design System website.
{{< /design-callout-alert >}}

{{< example >}}
<nav style="--bs-breadcrumb-divider: '';" aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>
{{< /example >}}


```scss
$breadcrumb-divider: none;
```

<!-- Boosted mod: Dark variant -->
## Dark variant

{{< added-in "5.2.1" >}}

Add `.breadcrumb-dark` to the `.breadcrumb` for a dark variant.

{{< example class="bg-dark" >}}
<nav aria-label="dark breadcrumb">
  <ol class="breadcrumb breadcrumb-dark">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item"><a href="#">Library</a></li>
    <li class="breadcrumb-item active" aria-current="page">Data</li>
  </ol>
</nav>
{{< /example >}}
<!-- End mod -->

## Accessibility

Since breadcrumbs provide a navigation, it's a good idea to add a meaningful label such as `aria-label="breadcrumb"` to describe the type of navigation provided in the `<nav>` element, as well as applying an `aria-current="page"` to the last item of the set to indicate that it represents the current page.

For more information, see the [ARIA Authoring Practices Guide breadcrumb pattern](https://www.w3.org/WAI/ARIA/apg/patterns/breadcrumb/).

## CSS

### Variables

{{< added-in "5.2.0" >}}

As part of Boosted's evolving CSS variables approach, breadcrumbs now use local CSS variables on `.breadcrumb` for enhanced real-time customization. Values for the CSS variables are set via Sass, so Sass customization is still supported, too.

{{< scss-docs name="breadcrumb-css-vars" file="scss/_breadcrumb.scss" >}}

<!-- Boosted mod: Dark variant -->
Customization through CSS variables can be seen on the `.breadcrumb-dark` modifier class where we override specific values without adding duplicate CSS selectors.

{{< scss-docs name="breadcrumb-dark-css-vars" file="scss/_breadcrumb.scss" >}}
<!-- End mod -->

### Sass variables

Variables for all breadcrumbs:

{{< scss-docs name="breadcrumb-variables" file="scss/_variables.scss" >}}

<!-- Boosted mod: Dark variant -->
Variables for [dark breadcrumb](#dark-variant):

{{< scss-docs name="breadcrumb-dark-variables" file="scss/_variables.scss" >}}
<!-- End mod -->
