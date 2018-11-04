# The Standalone Laravel Blade
The standalone version of [Laravel's Blade templating engine](https://laravel.com/docs/5.7/blade) for use outside of Laravel 5.7.

### Installation
----------------
The package can be installed via Composer by typing this command in your terminal or console:

```bash
composer require adelynx/blade
```

##Usage
-------

Create a Blade instance by passing it the folder(s) where your view files are located, and a cache folder. Render a template by calling the `make` method. More information about the Blade templating engine can be found on https://laravel.com/docs/5.7/blade.

```php
use Adelynx\Blade\Blade;

$blade = new Blade('views', 'cache');

echo $blade->make('homepage', ['name' => 'John Doe']);
```

Now you can easily create a directive by calling the ``compiler()`` function

```php
$blade->compiler()->directive('datetime', function ($expression) {
    return "<?php echo with({$expression})->format('F d, Y g:i a'); ?>";
});

{{-- In your Blade Template --}}
<?php $dateObj = new DateTime('2018-01-01 23:59:59') ?>
@datetime($dateObj)
```

The Blade instances passes all methods to the internal view factory. So methods such as `exists`, `file`, `share`, `composer` and `creator` are available as well. Check out the [original documentation](https://laravel.com/docs/5.7/views) for more information.