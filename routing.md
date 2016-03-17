<h1>Routing</h1>
<p>
  The Sectorr routes file is located in the <code>app</code> directory.
</p>

<h2>Basic routing</h2>
<code>
  Route::get('/', ['as' => 'home', 'uses' => 'WelcomeController@index', 'middleware' => 'guest']);
</code>
