# Laravel Routing (Latest Version: Laravel 12)
Laravel routing is the mechanism that determines how your application responds to different HTTP requests (e.g., GET, POST, PUT, DELETE). It allows you to define application URLs and specify the logic that should be executed when a user accesses them. 

Laravel has a clean and flexible routing mechanism that allows you to easily define:
* Web routes for pages (views)
* API routes for APIs (stateless)
* Console routes for Artisan commands
* Broadcast channels for real-time communication


| File           | Purpose                                            |
| -------------- | -------------------------------------------------- |
| `web.php`      | Routes for browser (session, CSRF, cookies, views) |
| `api.php`      | Routes for REST APIs (stateless)                   |
| `console.php`  | Artisan CLI commands                               |
| `channels.php` | Laravel Echo and broadcasting channels             |


## **Type of Routing*

* Basic Routing
* Route parameters
* Named Routes



### **Basic Routing**
```bash
use App\Http\Controllers\UserController;

Route::get('/users', [UserController::class, 'index']);
```
This calls the index() method in UserController when /users is visited.


### **Route Parameters**
```bash
Route::get('/user/{id}', function ($id) {
    return "User ID: $id";
});
```
**Optional:**
```bash
Route::get('/user/{name?}', function ($name = 'Guest') {
    return $name;
});
```


### **Named Routes**
```bash
Route::get('/profile', function () {
    return 'Your profile';
})->name('profile');

$url = route('profile');
```

**Multiple Parameters:**
```bash
Route::get('/post/{id}/comment/{commentId}', function ($id, $commentId) {
    return "Post $id, Comment $commentId";
});
```


### **Grouping Routes**
```bash
Route::prefix('admin')->middleware('auth')->group(function () {
    Route::get('/dashboard', function () {
        return 'Admin Dashboard';
    });
});
```

