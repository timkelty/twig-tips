# Don't Use Twig: Components/Helpers!

## With very little module code…

<!-- {% raw %} -->

```php
<?php
namespace modules\appmodule;

class AppModule extends \yii\base\Module
{
    public function init()
    {
        parent::init();

        $this->setComponents([
            'inflector' => \craft\\helpers\\Inflector::class,
            'string' => \craft\helpers\StringHelper::class,
            'collection' => \Illuminate\Support\Collection::class,
            'url' => \craft\helpers\UrlHelper::class,
        ]);
    }
}
```

<!-- {% endraw %}) -->

## You now have access to all these components from Twig or PHP:

<!-- {% raw %} -->

```twig
{{ craft.app.modules.appmodule.inflector.pluralize('cactus') }}
{{ craft.app.modules.appmodule.url.rootRelativeUrl('https://site.com/foo') }}
```

<!-- {% endraw %}) -->
