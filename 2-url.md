# ALWAYS use the `url()` function.

Yes, ALWAYS.

https://craftcms.com/docs/3.x/dev/functions.html#url

## Nope…

![](resources/nope.jpg)

```twig
<a href="/resources/?category={{ category.id }}">Category Link</a>
```

## Yep!

![](resources/yep.jpg)

```twig
<a href="{{ url('resources', {category: category.id}) }}">Category Link</a>
```
