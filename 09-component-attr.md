# Set default component attr and override with passed attrs.

```twig
{% include "_components/forms/button" with {
    text: "Submit",
    attrs: {
        type: "submit",
    },
} only %}
```

```twig
{% set text = text ?? null %}
{% set attrs = {
  class: 'button',
  type: 'button',
}|merge(attrs ?? {}) %}

{% if text %}
    <button {{ attr(attrs) }}>{{ text }}</button>
{% endif %}
```
