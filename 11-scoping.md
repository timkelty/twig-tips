# Scoping with `for` and `with`

## Nope…

![](resources/nope.jpg)

<!-- {% raw %} -->

```twig
{% if entry.assetsField.exists %}
  <img src="{{ entry.assetsField.one().url }}" alt="">
{% endif %}
```

<!-- {% endraw %}) -->

## Yep!

![](resources/yep.jpg)

<!-- {% raw %} -->

```twig
{% for asset in entry.assetsField.limit(1).all() %}
    <img src="{{ asset.url }}" alt="">
{% endfor %}
```

<!-- {% endraw %}) -->

## Nope…

![](resources/nope.jpg)

<!-- {% raw %} -->

```twig
  {% set featuredImgSrc = 'resources/nope.jpg' %}
  {% set featuredImgAlt = 'Nope' %}
  <img src="{{ featuredImgSrc }}" alt="{{ featuredImgAlt }}">
```

<!-- {% endraw %}) -->

## Yep!

![](resources/yep.jpg)

<!-- {% raw %} -->

```twig
{% with {
  src: 'resources/yep.jpg',
  alt: 'Yep!',
} %}
  <img src="{{ src }}" alt="{{ alt }}">
{% endwith %}
```

<!-- {% endraw %}) -->
