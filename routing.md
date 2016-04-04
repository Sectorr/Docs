# Routing
The Sectorr routes are defined in the <code class="language-php">app/routes.php</code> file.

## Basic routing
Routing in Sectorr is made as easy as possible, for a simple get request you can use the method shown below.

```php
    Route::get('/', ['as' => 'home', 'uses' => 'WelcomeController@index']);
```

The first parameter is the route's url, the second is an array. Within this array you can give up to 3 items, each with a key and a value. The first one would be the name of the route, for this you would use the key 'as'. 

Second you can choose a <a href="http://www.sectorr.co/docs/controllers">Controller</a> and method call, for this you should use the 'uses' key and then put in the exact name of your <a href="http://www.sectorr.co/docs/controllers">Controller</a> and method. So in this example the <a href="http://www.sectorr.co/docs/controllers">Controller</a> that will be called is <code class="language-php">WelcomeController</code> and the method is <code class="language-php">index</code>. If the request is a post request, you would do the exact same, but instead of using the <code class="language-php">Route::get()</code> method you would use the <code class="language-php">Route::post()</code> method.
