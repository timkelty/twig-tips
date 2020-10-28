## Tip #1: Be aware of what's there.

Read the docs and know your environment.

https://twig.symfony.com/doc/3.x/

https://craftcms.com/docs/3.x/dev/twig-primer.html

## Tip #2: Use the `url()` function.

https://craftcms.com/docs/3.x/dev/functions.html#url

```
<a href="/resources/?category={{ category.id }}">Category Link</a>
```

Becomes...

```
<a href="{{ url('resources', {category: category.id}) }}">Category Link</a>
```

## Tip #3: Use the `svg()` function.

https://craftcms.com/docs/3.x/dev/functions.html#svg

```
{{ svg('@webroot/icons/lemon.svg')|attr({ class: 'w-4 h-4' }) }}

{% for asset in craft.assets.filename('lemon.svg').limit(1).all() %}
    {{ svg(asset)|attr({ class: 'w-4 h-4' }) }}
{% endfor %}
```

## Tip #4: Many ways to skin a concat.

```
{% set string = foo ~ ' ' ~ bar ~ '!' %}

{% set string = [foo, ' ', bar, '!']|join() %}

{% set string = "#{foo} #{bar}!" %}

{% set string = "%s %s!"|format(foo, bar) %}
```

## Tip #5: Quick prototyping with for loops.

```
{% for i in range(0, 3) %}

{% for i in 0..3 %}
```

## Tip #6: Seomatic has helper functions.

https://nystudio107.com/docs/seomatic/Using.html#helper-functions-seomatic-helper

```
{% set excerpt = seomatic.helper.truncateOnWord(entry.richText, 180) %}

{% set matrixText = seomatic.helper.extractTextFromField(entry.contentMatrix) %}
{% set excerpt = seomatic.helper.truncateOnWord(matrixText, 180) %}
```

## Tip #7: UUID for when your component needs a unique ID.

TODO: Rob

## Tip #8: Use `attr` and `tag`.

TODO: Tim

## Tip #9: Use arrow functions in Twig.

TODO: Tim

## Tip #10: Set default component attr and override with passed attrs.

```
{% include "_components/_forms/_button" with {
    text: "Submit",
    attrs: {
        type: "submit",
    },
} only %}
```

```
{% set text = text ?? null %}
{% set attrs = {
  class: 'button',
  type: 'button',
}|merge(attrs ?? null) %}

{% if text %}
    <button {{ attr(attrs) }}>{{ text }}</button>
{% endif %}
```

## Tip #11: Know when to make a component.

A component can be anything you find yourself repeating across the site.

That said, don't make components until you find yourself repeating some DOM structure.

Embeds aren't just for big structures, like a wrapper for your content + sidebar layout. (show example)

They can be used for any component that you want to pass another component or bit of html too. (show example)

Walk through the component improvements file. Still needs added by Rob.
