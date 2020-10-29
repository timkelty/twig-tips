# Trigger Warning: Macros suck, avoid them

Includes and embeds are almost always a better choice.
One exception is macros using `_self` for micro-templates that aren't worth an separate file:

<!-- {% raw %} -->

```twig
{% set data = [
  {
    label: 'Foo',
    value: 'foo',
  },
  {
    label: 'Foo',
    value: 'bar'
  }
] %}

{% macro cell(data = { class: 'text-left'}, tag = 'td') %}
  {{ tag(tag, data) }}
{% endmacro %}

<table>
  <thead>
      <tr>
        {% for col in rows|first %}
          {{ _self.cell({ text: col.label, class: 'text-center' }, 'th') }}
        {% endfor %}
      </tr>
  </thead>
  <tbody>
    {% for row in data %}
      <tr>
        {% for col in row %}
          {{ _self.cell(col.value) }}
        {% endfor %}
      </tr>
    {% endfor %}
  </tbody>
</table>
```

<!-- {% endraw %}) -->
