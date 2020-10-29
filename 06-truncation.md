# Trunction

## With SEOMatic

[https://nystudio107.com/docs/seomatic/Using.html#helper-functions-seomatic-helper](https://nystudio107.com/docs/seomatic/Using.html#helper-functions-seomatic-helper)

<!-- {% raw %} -->

```twig
{% set excerpt = seomatic.helper.truncateOnWord(entry.richText, 180) %}

{% set matrixText = seomatic.helper.extractTextFromField(entry.contentMatrix) %}
{% set excerpt = seomatic.helper.truncateOnWord(matrixText, 180) %}
```

<!-- {% endraw %}) -->

## With `StringHelper`

<!-- {% raw %} -->

```twig
{% set stringHelper = create('craft\\helpers\\StringHelper') %}
{% set string = 'Lorem ipsum dolor sit amet' %}
{% set excerpt = stringHelper.safeTruncate(string, 10) %}
```

<!-- {% endraw %}) -->
