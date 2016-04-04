# Middleware
The Sectorr middleware is located in the <code class="language-php">app/Middleware</code>. Middleware is used to create filters for
certain locations in your application.

## Basic middleware useage
The basic middleware files you get with the standard Sectorr installation are <code class="language-php">app/Middleware/Auth.php</code> and <code class="language-php">app/Middleware/Guest.php</code>, you can use these in your <code class="language-php">app/routes.php</code> file. You can do this by adding an extra item to the array with <code class="language-php">middleware</code> as the key, like the example below:

```php
    Route::get('auth/login', ['as' => 'login', 'uses' => 'AuthController@getLogin', 'middleware' => 'auth');
```

The value will be the name of the middleware file without extension and it will work with or without a capital.
