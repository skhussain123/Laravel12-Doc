
# Laravel - Namespaces
Namespaces can be defined as a class of elements in which each element has a unique name to that associated class. It may be shared with elements in other classes.

The use keyword allows the developers to shorten the namespace.
use <namespace-name>;

The default namespace used in Laravel is App, however a user can change the namespace to match with web application. Creating user defined namespace with artisan command is mentioned as follows −

```bash namespace App\Http\Controllers;

php artisan app:name SocialNet
namespace SocialNet\Http\Controllers;

```

* Laravel me namespace ka use code ko organize krne ke liye hota hai, jese:

Agar aap chahte ho ke app ka naam "SocialNet" ho ya aapki project/App ka naam reflect ho, to aap namespace change karte ho.

1. Laravel ke andar har controller, model, middleware ya class apne specific folder me hoti hai. namespace batata hai ke ye class kis folder (ya module) se belong karti hai.
* UserController ki location: app/Http/Controllers
* User model ki location: app/Models

2. Jab aap use App\Models\User; likhtay ho, to PHP ko samajh ata hai ke User class kis file me milegi. Ye autoloading Laravel ke composer ke zariye hoti hai, aur namespace isme madad karta hai.

3. Agar aapke paas 2 alag Helper classes hain, ek Admin folder me aur ek User folder me, to aap unko namespace ke zariye differentiate kr saktay ho:

```bash
namespace App\Helpers\Admin;

class Helper {
    // Admin specific logic
}

```
```bash
namespace App\Helpers\User;

class Helper {
    // User specific logic
}

```

```bash
use App\Helpers\Admin\Helper as AdminHelper;
use App\Helpers\User\Helper as UserHelper;
```