# Controllers
Controllers are where you handle your application logic. The Sectorr controllers are located in the <code class="language-php">app/Controllers</code> directory.

## Basic controller usuage

### Defing a controller in a route
Controllers are defined in your <code class="language-php"><a href="http://www.sectorr.co/docs/routing">app/routes.php</a></code> file. This is done by starting with the 'uses' key in the options array of the route, the value will be the controller and method seperated by a <code class="language-php">@</code>.

```php
Route::get('home', ['as' => 'home', 'uses' => 'WelcomeController@home']);
```

The above route will use the <code class="language-php">home</code> method in the <code class="language-php">WelcomeController</code>.

### Controller structure
A basic controller will look something like the example below.

```php
namespace App\Controllers;

class WelcomeController extends Controller
{
  public function home()
  {
    // Code here
  }
}
```

Every controller needs to extend the base <code class="language-php">Controller</code> class. If you need some basic functionality or variables in every controller, you can put this in the <code class="language-php">Controller</code> class. You should also define the <code class="language-php">namespace</code> of the controller, otherwise you will get a controller not found exception. The controller's methods depend on the defined method names in the <code class="language-php">app/routes.php</code> file.

### Returning a view with variable data
Usually you will return a view from your controller and pass some variable data to it, what you might want to do is pass the logged in user as an object to your view:

```php
namespace App\Controllers;

use Sectorr\Core\Auth\Auth;

class WelcomeController extends Controller
{
  public function home()
  {
    $user = (Auth::check() ? Auth::user() : '');
    
    return view('home', ['user' => $user]);
  }
}
```

When using other classess like the <code class="language-php">Sectorr\Core\Auth\Auth</code> class, you will need to <code <code class="language-php">use</code> them. This is why working with a smart text editor is recommended, something like <a href="https://www.jetbrains.com/phpstorm/">PhpStorm</a>.

### Using dynamic parameters

When passing parameters to your controller method via the route url, you can use them by simply putting them in the controller method parameters.

```php
namespace App\Controllers;

class WelcomeController extends Controller
{
  public function home($user_id)
  {
    $user = User::find($user_id);
    $user = (! empty($user) ? $user : '');
    
    return view('home', ['user' => $user]);
  }
}
```

### Returning a view with variable data
Usually you will return a view from your controller and pass some variable data to it, what you might want to do is pass the logged in user as an object to your view:

```php
namespace App\Controllers;

use App\Models\User;

class WelcomeController extends Controller
{
  public function profile($id)
  {
    $user = User::find($id);
    
    return view('home', ['user' => $user]);
  }
}
```
