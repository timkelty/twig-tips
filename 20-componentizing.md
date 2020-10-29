# Know when to make a component.

A component can be anything you find yourself repeating across the site.

That said, don't make components until you find yourself repeating something.

https://tailwindcss.com/docs/extracting-components#extracting-html-components

![](resources/nope.jpg)

<!-- {% raw %} -->

```twig
{# _news/index.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
}).all() %}
    <div>
        <!-- Card -->
        <div>
            {% for asset in entry.listingImage.limit(1).all() %}
                <img src="{{ asset.url }}" alt="">
            {% endfor %}
            <h3>{{ entry.title }}</h3>
            {{ entry.description }}
        </div>
    </div>
{% endfor %}
```

<!-- {% endraw %}) -->
