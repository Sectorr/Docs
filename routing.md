# Routing
The Sectorr routes are defined in the <code class="language-php">app/routes.php</code> file.

## Basic routing
Routing in Sectorr is made as easy as possible, for a simple get request you can use the method shown below.

```php
Route::get('/', ['as' => 'home', 'uses' => 'WelcomeController@index']);
```

The first parameter is the route's url, the second is an array. Within this array you can give up to 3 items, each with a key and a value. The first one would be the name of the route, for this you would use the key 'as'. 

Second you can choose a <a href="http://www.sectorr.co/docs/controllers">Controller</a> and method call, for this you should use the 'uses' key and then put in the exact name of your <a href="http://www.sectorr.co/docs/controllers">Controller</a> and method. So in this example the <a href="http://www.sectorr.co/docs/controllers">Controller</a> that will be called is <code class="language-php">WelcomeController</code> and the method is <code class="language-php">index</code>. If the request is a post request, you would do the exact same, but instead of using the <code class="language-php">Route::get()</code> method you would use the <code class="language-php">Route::post()</code> method.

The last item in the array is the <a href="http://www.sectorr.co/docs/middleware">middleware</a> you want to use in the Route. For this you should use the 'middleware' key, and then choose your <a href="http://www.sectorr.co/docs/middleware">middleware</a> class as value, with or without a capital letter and without file extension. You can read more about middleware <a href="http://www.sectorr.co/docs/middleware">here</a>.

## Routing parameters
You can also use dynamic parameters in your routes, to do this you put the url piece you want to be dynamic between <code class="language-php">{}</code>. A route with dynamic parameters would look something like this:

```php
Route::get('user/{id}', ['as' => 'profile', 'uses' => 'UserController@profile']);
```

In your view you can echo out a dynamic route destination using the <code class="language-php">route()</code> helper as following:

```html
<a href="{{ route('profile', ['id' => 5]) }}"></a>
```

Next you can get the dynamic values in the controller by putting them in the parameters of the controller method, and use them to get a user for example:

```php
namespace App\Controllers;

use App\Models\User;

class UserController extends Controller
{
    public function profile($id)
    {
        $user = User::find($id);
        
        return $user;
    }
}
```

Passing multiple values to a route is done exactly the same, and is usually seperated by <code class="language-php">/</code>'s. Check out the route below as an example.

```php
Route::get('{user}/{post}', ['as' => 'user-post', 'uses' => 'PostController@getPost']);
```

Creating a link with multiple parameters in your view is done exactly the same as you would do for a link with one dynamic parameter, except for the second array parameter in the route() helper will have the multiple values.

```html
<a href="{{ route('user-post', ['user' => $user->name, 'post' => $post->slug]) }}">Post</a>
```

Getting multiple variables from the url in the <a href="http://www.sectorr.co/docs/controllers">controller</a> is done a little bit different.

```php
namespace App\Controllers;

use App\Models\User;
use App\Models\Post;

class UserController extends Controller
{
    public function profile($data)
    {
        $username = $data['user'];
        $postslug = $data['post'];
        
        $user = User::where('username', $username)->first();
        $post = Post::where('slug', $postslug)->first();
        
        return redirect('post', ['user' => $user, 'post' => $post]);
    }
}
```
