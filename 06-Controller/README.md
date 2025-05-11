

# Laravel - Controllers
In Laravel, a controller is a PHP class that handles the logic for incoming requests and outgoing responses. Instead of writing all your logic in routes, you keep it clean and organized inside controller methods.

## Creating a Controller
Open the command prompt or terminal based on the operating system you are using and type the following command to create controller using the Artisan CLI (Command Line Interface).
```bash
php artisan make:Controller UserController
```
app/Http/Controller/PostController.php


##  Example of a Basic Controller
```bash
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class PostController extends Controller
{
    public function index() {
        return "This is the index of posts.";
    }

    public function store(Request $request) {
        // Store logic
    }
}
```

## Connecting Controller to Routes
```bash
use App\Http\Controllers\PostController;

Route::get('/posts', [PostController::class, 'index']);
Route::post('/posts', [PostController::class, 'store']);
```


## Resource Controller
If you're building a full CRUD system, you can generate a resource controller with:
```bash
php artisan make:controller PostController --resource
```

This command automatically adds 7 common methods:
| Method      | Purpose             |
| ----------- | ------------------- |
| `index()`   | Show all records    |
| `create()`  | Show form to create |
| `store()`   | Save new record     |
| `show()`    | Show single record  |
| `edit()`    | Show edit form      |
| `update()`  | Update a record     |
| `destroy()` | Delete a record     |

Then register all routes with one line:
```bash
Route::resource('posts', PostController::class);
```


