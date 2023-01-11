Laravel Log Viewer
================

This is a fork from https://github.com/rap2hpoutre/laravel-log-viewer/ v1.7.0 updated to work on Laravel 9. 

**All credits go the original authors.**


## Install (Laravel)
Install via composer
```bash
composer require nmfmcosta/laravel-log-viewer
```

Add Service Provider to `config/app.php` in `providers` section
```php
LB\LaravelLogViewer\LaravelLogViewerServiceProvider::class,
```

Add a route in your web routes file:
```php 
Route::get('logs', '\LB\LaravelLogViewer\LogViewerController@index');
```

Go to `http://myapp/logs` or some other route

### Install (Lumen)
Install via composer
```bash
composer require nmfmcosta/laravel-log-viewer
```

Add the following in `bootstrap/app.php`:
```php
$app->register(\LB\LaravelLogViewer\LaravelLogViewerServiceProvider::class);
```

Explicitly set the namespace in `app/Http/routes.php`:
```php
$router->group(['namespace' => '\LB\LaravelLogViewer'], function() use ($router) {
    $router->get('logs', 'LogViewerController@index');
});
```

## Advanced usage
### Customize view
Publish `log.blade.php` into `/resources/views/vendor/laravel-log-viewer/` for view customization:

```bash
php artisan vendor:publish \
  --provider="LB\LaravelLogViewer\LaravelLogViewerServiceProvider" \
  --tag=views
``` 

### Edit configuration
Publish `logviewer.php` configuration file into `/config/` for configuration customization:

```bash
php artisan vendor:publish \
  --provider="LB\LaravelLogViewer\LaravelLogViewerServiceProvider"
``` 

### Troubleshooting
If you got a `InvalidArgumentException in FileViewFinder.php` error, it may be a problem with config caching. Double check installation, then run `php artisan config:clear`.

