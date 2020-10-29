# Inflection

```twig
{% set inflector = create('craft\\helpers\\Inflector') %}
{% set cacti = inflector.pluralize('cactus') %}
{% set cactus = inflector.singularize(cacti) %}
{% set totalCacti = 4 %}
{% set bestCactus = 3 %}

{{ "I love the #{inflector.ordinalize(totalCacti)} #{cactus}." }}
{{ "I love the #{totalCacti > 1 ? cacti : cactus }." }}
```
