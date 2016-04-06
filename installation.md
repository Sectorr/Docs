# Installation
There are two ways to install Sectorr to your (local) webserver. You can download and install it using <code class="language-php"><a href="http://www.getcomposer.org">Composer</a></code>, or download the .zip file.

## Installation using .zip file
You can download the .zip file <code class="language-php"><a href="{$download}">here</a></code>. Download it and extract it in your webwroot directory of your webserver.

## Installation using Composer
Installing Sectorr using <code class="language-php"><a href="http://www.getcomposer.org">Composer</a></code> is one of the easiest ways to get you started. You can do this by using the <code class="language-php"><a href="http://www.getcomposer.org">Composer</a></code> create-project command in your terminal. If you do not have composer, you can download it <code class="language-php"><a href="http://www.getcomposer.org">here</a></code>
<code class="language-php">composer create-project sectorr/sectorr <b>[project-folder]</b> --prefer-dist</code>

## Configuration
Sectorr has got a very easy configuration, just open the <code class="language-php">app/config.json</code> file.

```json
{
  "database": {
    "host": "localhost",
    "username": "root",
    "password": "",
    "name": "test-app"
  },
  "user": "App\\Models\\User"
}
```
