# Force JSON Response For API Requests in Laravel 11

```php
// bootstrap/app.php
 
return Application::configure(basePath: dirname(__DIR__))
 
    //...
 
    ->withExceptions(function (Exceptions $exceptions) {
        $exceptions->shouldRenderJsonWhen(function (Request $request, Throwable $e) {
            if ($request->is('api/*')) {
                return true;
            }
 
            return $request->expectsJson();
        });
    })->create();
```
