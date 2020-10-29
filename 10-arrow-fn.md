# Use arrow functions in Twig.

## Nope…

![](resources/nope.jpg)

<!-- {% raw %} -->

```twig
{% set youngest = 0 %}

Over 21:
{% for entry in craft.entries.all() if entry.firstName and entry.age > 21 %}
  {{ entry.firstName }}{{ not loop.last ? ',' }}
  {% if youngest < entry.age %}
    {% set youngest = entry.age %}
  {% endif %}
{% endfor %}

Youngest: {{ youngest }}
```

<!-- {% endraw %}) -->

## #nailedit

![](resources/yep.jpg)

<!-- {% raw %} -->

```twig
{% set over21 = craft.entries.all()|filter(e => e.firstName && entry.age > 21) %}
{% set ages = over21|reduce((curr, prev) => prev|merge(curr.age), []) %}

Over 21: {{ over21|map(e => e.firstName)|join(',') }}
Youngest: {{ ages|min }}
```

<!-- {% endraw %}) -->
