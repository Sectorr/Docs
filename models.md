# Models
The Sectorr models are located in the <code class="language-php">app/Models</code> directory.

## Basic models
A basic model needs at least one protected variable called <code class="language-php">$table</code> and it needs to be the same as the database table you want to link to your model. Also you will need to extend the base <code class="language-php">Model</code> class:

```php
namespace App\Models;

use Sectorr\Core\Database\Model;

class User extends Model
{
  protected $table = 'users';
}
```
