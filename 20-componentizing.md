# Know when to make a component.

A component can be anything you find yourself repeating across the site.

That said, don't make components until you find yourself repeating some DOM structure.

Embeds aren't just for big structures, like a wrapper for your content + sidebar layout. (show example)

They can be used for any component that you want to pass another component or bit of html too. (show example)

Walk through the component improvements file. Still needs added by Rob.

![](resources/nope.jpg)

```twig
{# _news/index.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
}).all() %}
    <div>
        {% include "_components/card" %}
    </div>
{% endfor %}
```

```twig
{# _components/card.twig #}

<div>
    {% for asset in entry.listingImage.limit(1).all() %}
        <img src="{{ asset.url }}" alt="">
    {% endfor %}
    <h3>{{ entry.title }}</h3>
    {{ entry.description }}
</div>
```
