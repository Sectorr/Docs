# Views
Views are where your HTML and application logic come together. In views you can use the variable data from a <a href="http://www.sectorr.co/docs/controllers">Controller</a> and use this in your HTML. The Views are located in the <code class="language-php">app/Views</code> directory.

## Basic views
Sectorr uses Blade templating, this means every view has to have a <code class="language-php">.blade.php</code> extension. So a view name would be for example: <code class="language-php">welcome.blade.php</code>.

A basic view would look something like this:
```html
<html>
  <body>
    </h1>This is a view</h1>
  </body>
</html>
```

This file would be located at: <code class="language-php">app/Views/welcome.blade.php</code>

## Returning views
To display the content of a view on the screen, you will need to return it. You can do this by returning the <code class="language-php">View::make('home')</code> method or just the global view('home') helper function. This function will need the view name as parameter without extension, and it will start looking in the <code class="language-php">app/Views</code> directory.
```php
return view('home');
```
So in the example above, the view that will be returned is <code class="language-php">app/Views/home.blade.php</code>.

## Passing variables to views
The main reason to use views is to easily use variables in your HTML. Passing variables to views is really easy, just like using them in your views. Let's take a look at how we return a view with variables.

Passing variables to the returned view is easily done by adding a second parameter. This second parameter should be an associative array, the keys will be the name of the variable in the view, the second will be the value of the variable.

```php
return view('home', ['name' => 'Henk', 'age' => '20']);
```

If you already have variables in your <a href="http://www.sectorr.co/docs/controllers" >Controller</a>, you can also use PHP's compact function. You have to use the name of the existing variables, which will create an associative array for you with the value matching the key.
```php
$name = 'Henk';
$age = '20';

return view('home', compact('name', 'age'));
```
To output these variables in your view, you can simply echo them:
```html
<html>
  <body>
    </h1>Welcome <?php echo $name; ?></h1>
    <p>Your age is: <?php echo $age; ?></p>
  </body>
</html>
```
You can also use <a href="http://www.sectorr.co/docs/blade">Blade</a> to echo your variables:
```html
<html>
  <body>
    <h1>Welcome <code class="language-php">{{ $name }}</code></h1>
    <p>Your age is: <code class="language-php">{{ $age }}</code></p>
  </body>
</html>
```
