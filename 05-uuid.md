# UUID for when your component needs a unique ID.

<!-- {% raw %} -->

```twig
{% set uuid = create('craft\\helpers\\StringHelper').UUID() %}

<div class="tabs">
    <ul>
        {% for i in 0..3 %}
            <li><a href="#{{ ['tab', loop.index, uuid]|join('-')|id }}">Tab 1</a></li>
        {% endfor %}
    </ul>
    {% for i in 0..3 %}
        <div id="{{ ['tab', loop.index, uuid]|join('-')|id }}">
        </div>
    {% endfor %}
</div>
```

<!-- {% endraw %}) -->
