# Don't Use Twig: Components/Helpers!

## With very little module code…

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

## You now have access to all these components from Twig or PHP:

```twig
{{ craft.modules.appmodule.inflector.pluralize('cactus') }}
{{ craft.modules.appmodule.url.rootRelativeUrl('https://site.com/foo') }}
```