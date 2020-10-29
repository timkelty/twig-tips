# Use `attr` and `tag`.

## Ugly…

![](resources/nope.jpg)

```twig
{% set tag = link ? 'a' : 'div' %}

<{{ tag }}
  class="text-lg{% if error %} text-red{% endif %}"
  {% if %}href=""{% endif %}
  data-foo="{{ {bar: 'baz'}|json_encode|html_attr }}">
  Drake is not impressed.
</{{ tag }}>
```

## Getting better…

![](resources/yep.jpg)

```twig
{% set link = link ?? null %}
{% set error = error ?? null %}
{% set tag = link ? 'a' : 'div' %}
{% set fooData = {
  bar: 'baz'
} %}

<{{ tag }}
  {{ attr({
    class: ['text-lg', error ? 'text-red'],
    href: link,
    data: {
      foo: fooData
    }
  }) }}
  Drake is happy.
</{{ tag }}>
```

## Final answer 💯

![](resources/clap.gif)

```twig
{% set link = link ?? null %}
{% set error = error ?? null %}
{% set tag = link ? 'a' : 'div' %}
{% set fooData = {
  bar: 'baz'
} %}

{{ tag(tag, {
  class: ['text-lg', error ? 'text-red'],
  href: link,
  data: {
    foo: fooData
  },
  text: 'Drake wants your number',
})}}
```
