# Many ways to skin a concat.

<!-- {% raw %} -->

```twig
{# Broke #}
{% set string = foo ~ ' ' ~ bar ~ '!' %}

{# Woke #}
{% set string = [foo, ' ', bar, '!']|join() %}

{# Bespoke #}
{% set string = "#{foo} #{bar}!" %}

{# You do you, I guess… #}
{% set string = "%s %s!"|format(foo, bar) %}
```

<!-- {% endraw %}) -->
