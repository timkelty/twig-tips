# Scoping with `for` and `with`

## Nope…

![](resources/nope.jpg)

```twig
{% if entry.assetsField.exists %}
  <img src="{{ entry.assetsField.one().url }}" alt="">
{% endif %}
```

## Yep!

![](resources/yep.jpg)

```twig
{% for asset in entry.assetsField.limit(1).all() %}
    <img src="{{ asset.url }}" alt="">
{% endfor %}
```

## Nope…

![](resources/nope.jpg)

```twig
  {% set featuredImgSrc = 'resources/nope.jpg' %}
  {% set featuredImgAlt = 'Nope' %}
  <img src="{{ featuredImgSrc }}" alt="{{ featuredImgAlt }}">
```

## Yep!

![](resources/yep.jpg)
```twig
{% with {
  src: 'resources/yep.jpg',
  alt: 'Yep!',
} %}
  <img src="{{ src }}" alt="{{ alt }}">
{% endwith %}
```
