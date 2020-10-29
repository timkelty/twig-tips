# ALWAYS use the `url()` function.

Yes, ALWAYS.

https://craftcms.com/docs/3.x/dev/functions.html#url

## Nope…

![](resources/nope.jpg)

<!-- {% raw %} -->

```twig
<a href="/resources/?category={{ category.id }}">Category Link</a>
```

<!-- {% endraw %}) -->

## Yep!

![](resources/yep.jpg)

<!-- {% raw %} -->

```twig
<a href="{{ url('resources', {category: category.id}) }}">Category Link</a>
```

<!-- {% endraw %}) -->
