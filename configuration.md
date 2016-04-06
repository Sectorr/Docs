# Configuration
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

The user config propertie is the namespace of the default user <a href="http://www.sectorr.co/docs/models">model</a>. If you create a different <a href="http://www.sectorr.co/docs/models">model</a> for your users, you'll need to change its namespace in the config, as this is used in the <a href="https://github.com/Sectorr/Core">Sectorr core</a>.

## Adding/editing config items
You can also add things like your project name and description or slogan to the config file for easy usuage:

```json
{
  "project" : {
    "title": "My first Sectorr app",
    "description": "Project description"
  }, 
  "database": {
    "host": "localhost",
    "username": "root",
    "password": "",
    "name": "test-app"
  },
  "user": "App\\Models\\User"
}
```

## Retrieving config items
Sectorr has a very easy config class which makes retrieving config items very easy:

```php
    <h1>Project title: {{ Config::get('project')['title'] }}</h1>
    <p>Project description: {{ Config::get('project')['description'] }}</p>
```
