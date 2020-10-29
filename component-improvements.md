## Improving a component.

```
{# _news/index.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
}).all() %}
    <div>
        {% include "_components/_card" %}
    </div>
{% endfor %}
```

```
{# _components/_card.twig #}

<div>
    {% for asset in entry.listingImage.limit(1).all() %}
        <img src="{{ asset.url }}" alt="">
    {% endfor %}
    <h3>{{ entry.title }}</h3>
    {{ entry.description }}
</div>
```

---

## Improvement #1: Don't rely on the parent template's environment.

```
{# _news/index.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
}).all() %}
    <div>
        {% include "_components/_card" with {
            entry: entry,
        } only %}
    </div>
{% endfor %}
```

```
{# _components/_card.twig #}

<div>
    {% for asset in entry.listingImage.limit(1).all() %}
        <img src="{{ asset.url }}" alt="">
    {% endfor %}
    <h3>{{ entry.title }}</h3>
    {{ entry.description }}
</div>
```

---

## Improvement #2: Don't rely on an element's content model.

It's good practice to make your component's data agnostic.

Let's you easily do things like eagerload an asset in one spot but not in another or use the component with a category and not with an entry. Also helps with static data for prototyping in the early stages of a project.

```
{# _news/index.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
}).all() %}
    <div>
        {% include "_components/_card" with {
            image: entry.listingImage.one(),
            heading: entry.title,
            description: entry.description,
        } only %}
    </div>
{% endfor %}
```

```
{# _news/index-alt.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
    with: ["listingImage"],
}).all() %}
    <div>
        {% include "_components/_card" with {
            image: entry.listingImage|slice(0, 1),
            heading: entry.title,
            description: entry.description,
        } only %}
    </div>
{% endfor %}
```

```
{# _components/_card.twig #}

<div>
    {% if image %}
        <img src="{{ asset.image }}" alt="">
    {% endif %}
    {% if heading %}
        <h3>{{ heading }}</h3>
    {% endif %}
    {{ description }}
</div>
```

---

## Improvement #3: Set your component's variables up top.

This allows you a better defense against what is being passed through.

And allows opportunity to set defaults.

It also provides more clarity and a little separation between data and markup.

```
{# _news/index.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
}).all() %}
    <div>
        {% include "_components/_card" with {
            image: entry.listingImage.one(),
            heading: entry.title,
            description: entry.description,
        } only %}
    </div>
{% endfor %}
```

```
{# _components/_card.twig #}

{% set image = image ?? null %}
{% set heading = heading ?? "Lorem ipsum dolor sit amet" %}
{% set description = description ?? null %}

<div>
    {% if image %}
        <img src="{{ asset.image }}" alt="">
    {% endif %}
    <h3>{{ heading }}</h3>
    {{ description }}
</div>
```

---

## Improvement #4: Make your include an embed, if needed.

Right before launch, the client request a new card layout that re-uses everything except the heading style?

Easily use your include as an embed where needed.

```
{# _news/index.twig #}

{% for entry in craft.entries({
    section: "news",
    limit: 10,
}).all() %}
    <div>
        {% embed "_components/_card" with {
            image: entry.listingImage.one(),
            description: entry.description,
        } only %}
            {% block heading %}
                {% include "_components/_special-hdg" with {
                    text: entry.title,
                } only %}
            {% endblock %}
        {% endembed %}
    </div>
{% endfor %}
```

```
{# _components/_card.twig #}

{% set image = image ?? null %}
{% set heading = heading ?? "Lorem ipsum dolor sit amet" %}
{% set description = description ?? null %}

<div>
    {% if image %}
        <img src="{{ asset.image }}" alt="">
    {% endif %}
    {% block heading %}
        <h3>{{ heading }}</h3>
    {% endblock %}
    {{ description }}
</div>
```
