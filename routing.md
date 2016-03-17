<h1>Routing</h1>
<p>
  The Sectorr routes are defined in the <code>app/routes.php</code> file.
</p>

<h2>Basic routing</h2>
<p>
  Routing in Sectorr is made as easy as possible, for a simple get request you can use the method shown below.
</p>
<code>
  Route::get('/', ['as' => 'home', 'uses' => 'WelcomeController@index']);
</code>
<p>
  The first parameter is the route's url, the second is an array. Within this array you can give up to 3 items, each with a key and a value. The first one would be the name of the route, for this you would use the key 'as'. Second you can choose a Controller and method call, for this you should use the 'uses' key and then put in the exact name of your Controller and method. So in this example the Controller that will be called is <code>WelcomeController</code> and the method is <code>index</code>. If the request is a post request, you would do the exact same, but instead of using the <code>Route::get()</code> method you would use the <code>Route::post()</code> method.
</p>
