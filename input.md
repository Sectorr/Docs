# Input handling
Handling input is made very easy in Sectorr, because of the build-in Input class located in the <code class="language-php">Sectorr/Core/Input</code> directory.

## Basic usuage
The Input class contains 3 static methods: <code class="language-php">Input::exists()</code>, <code class="language-php">Input::get()</code> and <code class="language-php">Input::all()</code>.

### Checking if input exists
Using the <code class="language-php">Input::exists()</code> method, you can check if the current request holds any input. The exists method has one optional parameter, this is the input type (POST or GET) as a string.
So to check if there is any input, you would write a simple if statement like this:

```php
if (Input::exists()) {
  return Input::all();
} else {
  return 'There is no input';
}
```

If you want to check if there is any input with a special type you could write an if statement like this:

```php
if (Input::exists('post')) {
  return Input::get()
} else {
  return 'There is no POST input';
}
```

### Retrieving all input
Retrieving all input is really easy, using the <code class="language-php">Input::all()</code> method:

```php
if (Input::exists()) {
  $input = Input::all();
  
  return $input;
}
```

### Retrieving certain input parts
Retrieving a certain part of the input is very easy as well. You just pass the name of the input field in the <code class="language-php">Input::get()</code> method as parameter:

```php
if (Input::exists('post')) {
  $email = Input::get('email');
  
  return $email;
}
```
