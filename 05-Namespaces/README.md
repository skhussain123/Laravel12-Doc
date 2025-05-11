
# Laravel - Namespaces
Namespaces can be defined as a class of elements in which each element has a unique name to that associated class. It may be shared with elements in other classes.

The use keyword allows the developers to shorten the namespace.
use <namespace-name>;

The default namespace used in Laravel is App, however a user can change the namespace to match with web application. Creating user defined namespace with artisan command is mentioned as follows −

```bash namespace App\Http\Controllers;

php artisan app:name SocialNet
namespace SocialNet\Http\Controllers;

```

Agar aap chahte ho ke app ka naam "SocialNet" ho ya aapki project/App ka naam reflect ho, to aap namespace change karte ho.


