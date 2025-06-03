

### 1. What is Laravel?
Laravel ek popular PHP framework hai jo web applications develop karne ke liye use hota hai. Ye MVC (Model-View-Controller) architecture follow karta hai jisme application logic (Model), UI (View), aur routing/controller (Controller) alag alag manage hoti hain. Laravel developer ko fast, secure, aur maintainable applications banane me madad karta hai.


### 2. What are the main features of Laravel?
Laravel me bohat si built-in features hoti hain jaise routing system jo URL ko controllers se connect karta hai, Eloquent ORM jo database queries ko simplify karta hai, Blade templating engine jo HTML me dynamic data show karta hai, Middleware jo HTTP requests filter karta hai, Artisan CLI jo development tasks automate karta hai, aur bahut kuch.


### 3. What is MVC?

MVC ek design pattern hai jisme 3 components hote hain:
1. Model: Data aur business logic ko represent karta hai, jaise database interaction.
2. View: User interface jahan data show hota hai.
3. Controller: User ke requests ko handle karta hai, models se data leta hai, aur views ko response bhejta hai. MVC se code organized aur maintainable hota hai.


### 4. What is routing in Laravel?
Routing wo process hai jisme URL patterns ko specific controllers ya closures ke sath map kiya jata hai. Jaise agar user example.com/home pe jaye to ye routing decide karti hai ke kaunsa function call hoga.


### 5. What is a controller?
Controller ek class hoti hai jisme application logic likha jata hai. Ye user ke request ko receive karta hai, required data fetch karta hai (usually models se), aur response ke liye view ya JSON return karta hai.


### 6. What is Blade in Laravel?
Blade Laravel ka templating engine hai. Ye aapko HTML me dynamic content insert karne ke liye special syntax provide karta hai, jaise {{ $variable }}. Blade me loops, conditions, aur components bhi use kiye ja sakte hain. Ye code ko clean aur reusable banata hai.

### 7. How do you create a controller?
Aap artisan command php artisan make:controller ControllerName chalakar naya controller bana sakte hain. Isse aapke app/Http/Controllers folder me ek file ban jati hai jisme aap methods likh sakte hain.

### 8. How to create a model in Laravel?
Model banane ke liye artisan command php artisan make:model ModelName use hota hai. Model class aapke database table ko represent karti hai aur Eloquent ORM ke methods ke sath database operations ko easy banati hai.

### 9. What is Eloquent ORM?
Eloquent Laravel ka ORM (Object Relational Mapper) hai jo database queries ko PHP objects me translate karta hai. Iska matlab aap SQL queries ki jagah PHP syntax me apna data fetch, insert, update kar sakte hain.


### 10. How to insert data using Eloquent?
Aap ek model instance create kar ke data set karte hain aur phir save() method call karte hain. Jaise:

```bash
$user = new User;
$user->name = 'Ali';
$user->email = 'ali@example.com';
$user->save();
```

### 11. How to retrieve all records?
Agar aapko kisi table ke tamam records chahiye, to aap Eloquent ka all() method use kar sakte hain. Jaise:
```bash
$users = User::all();

```
Ye sabhi users ko ek collection (array jaisa object) ki form me return karega.


### 12. How to find a record by ID?
Agar aapko kisi specific record ki zarurat ho jiska ID pata ho, to find() method use karte hain:

```bash
$user = User::find(1);

```
Ye user with ID=1 ko laega ya null return karega agar nahi mile.


### 13. What is migration?
Migration ek version control system hai database ke liye. Iske zariye aap database me tables create, modify ya delete kar sakte hain code ke through, taake development me sab synchronize rahe.

### 14. How to create a migration?
Naya migration banane ke liye artisan command:
```bash
php artisan make:migration create_users_table
```
Is se database/migrations folder me ek file banegi jisme aap table structure define kar sakte hain.


### 15. How to run migrations?
Jo migration files ban chuki hain, unhe database pe apply karne ke liye ye command chalate hain:

```bash
php artisan migrate

```


### 16. What is Laravel Artisan?
Artisan Laravel ka command-line interface (CLI) hai jo development ke bohat saare tasks automate karta hai, jaise controllers banana, migrations run karna, tests chalana, cache clear karna, etc.

### 17. What is tinker in Laravel?
Tinker ek interactive REPL (Read-Eval-Print Loop) shell hai jisme aap Laravel application ke code ko real time me test kar sakte hain. Isme aap models ko access karke queries run kar sakte hain. Command:

```bash
php artisan tinker
```

### 18. How to create a route in Laravel?
Routes routes/web.php me define ki jati hain. Example:

```bash
Route::get('/home', [HomeController::class, 'index']);
```
Ye /home URL pe request aane par HomeController ke index method ko call karega.


### 19. What is CSRF?
CSRF (Cross-Site Request Forgery) ek security threat hai jisme unauthorized requests kisi user ke naam se ki jati hain. Laravel automatically CSRF token generate karta hai jo forms me hidden field ke taur par use hota hai aur har POST request ke sath verify hota hai, jisse security barhti hai.

### 20. What is middleware?
Middleware ek filter layer hai jo HTTP requests ko controller tak pohanchne se pehle process karta hai. Jaise authentication check karna, request logging karna, ya CORS headers set karna. Laravel me aap custom middleware bhi bana sakte hain.

### 21. What is the request lifecycle in Laravel?
Laravel me jab user koi request karta hai, to wo sabse pehle public/index.php file par aati hai jo sari requests ko handle karti hai. Phir request middleware ke through guzarti hai jahan security aur authorization checks hote hain. Uske baad route middleware aur routing system request ko appropriate controller ya closure tak pohanchata hai. Controller logic chalata hai aur response banata hai, jo browser ko bhej diya jata hai.


### 22. How to validate form data?
Laravel me aap $request->validate() method use karke form data ko validate kar sakte hain. Jaise:
```bash
$request->validate([
  'name' => 'required|string|max:255',
  'email' => 'required|email|unique:users'
]);

```
Agar validation fail hota hai to automatically user ko errors ke sath wapas form par redirect kar diya jata hai.


### 23. How to use sessions in Laravel?
Session ek temporary storage hota hai jo user-specific data ko store karta hai, jaise login info. Aap session me data set kar sakte hain:
```bash
session(['key' => 'value']);
```
Aur is data ko kisi bhi page ya request me session('key') se access kar sakte hain.


### 24. How to get session value?
Session se value nikalne ke liye aap simple session('key') function use karte hain. Agar wo key exist karti hai to value mil jayegi, warna null.


### 25. How to use flash messages?
Flash messages wo temporary messages hote hain jo ek request ke liye store hote hain aur agle request me show kiye jate hain. Laravel me aap session()->flash('message', 'Success!'); se set karte hain. Ye message form submission ke baad ek baar user ko dikhaya jata hai.


### 26. How to use pagination?
Jab database se bohat saare records la rahe ho, to pagination use karte hain taake data pages me divide ho jaye. Eloquent me:
```bash
$users = User::paginate(10);
```
Ye har page par 10 records show karega aur links banayega agla ya pehla page dekhne ke liye.


### 27. How to send email in Laravel?
Laravel me email bhejne ke liye built-in Mail facade use hota hai. Pehle ek mail class banate hain, phir usay send karte hain:

```bash
Mail::to('user@example.com')->send(new WelcomeMail());
```
Aapko email settings .env file me configure karni hoti hain (SMTP).


### 28. How to create a mail class?
Mail class banane ke liye artisan command:

```bash
php artisan make:mail WelcomeMail
```
Is class me aap email ka subject, view aur data define karte hain jo email me jayega.


### 29. What is .env file?
.env file ek environment configuration file hai jisme sensitive info jaise database credentials, email SMTP settings, app key, aur debug mode hota hai. Is file ko git me commit nahi karte taake security rahe.

### 30. How to connect DB in Laravel?
Database connection ke liye .env file me parameters set karte hain:

```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_db
DB_USERNAME=root
DB_PASSWORD=your_password

```
Phir Laravel automatically config/database.php se ye config load kar leta hai.


### 31. What is service container in Laravel?
Service Container ek powerful tool hai jo class dependencies aur dependency injection ko manage karta hai. Matlab agar ek class ko doosri class ki zarurat hai, to service container automatically us dependency ko resolve karke inject kar deta hai. Ye loosely coupled code likhne me madad karta hai.

### 32. What is dependency injection?
Dependency Injection ka matlab hai ke aap apni classes me jo bhi required services hain, unko directly create na karein, balke unko constructor ya method parameters ke through inject karain. Laravel service container ye kaam karta hai aur testing aur maintenance easy ho jati hai.

### 33. What are service providers?
Service providers wo classes hoti hain jo Laravel application me services ko register aur boot karti hain. Jaise database, mail, cache services. Ye app/Providers folder me hoti hain aur config/app.php me register hoti hain.


### 34. How to create a service provider?
Artisan command se:

```bash
php artisan make:provider CustomServiceProvider
```
Phir isme register() aur boot() methods define karte hain jahan aap apni services bind kar sakte hain.


### 35. What is queue in Laravel?
Queue system background me tasks ko delay karke run karta hai, jaise emails bhejna ya heavy processing. Isse app fast aur responsive rehta hai. Laravel me different queue drivers (database, Redis, etc.) supported hain.

### 36. How to dispatch a job to a queue?
Pehle ek job banate hain:
```bash
php artisan make:job SendEmailJob
```
**Phir us job ko dispatch karte hain:**
```bash
SendEmailJob::dispatch($user);
```
Ye job background me asynchronously chalti hai.


### 37. What is the difference between get() and first() in Eloquent?
get() method multiple records return karta hai ek collection me, jabke first() sirf pehla record return karta hai ya null agar record na mile.


### 38. How to soft delete in Laravel?
Soft delete me record database me rehta hai lekin delete mark hota hai. Iske liye model me SoftDeletes trait use karte hain:

```bash
use Illuminate\Database\Eloquent\SoftDeletes;
class Post extends Model {
    use SoftDeletes;
}
```
**Aur table me deleted_at timestamp column hota hai.**

### 39. What is event and listener in Laravel?
Event ek action hai jo app ke andar hota hai, jaise user registered. Listener wo class ya function hai jo is event ke response me kaam karta hai, jaise welcome email bhejna. Isse app modular aur loosely coupled banta hai.


### 40. How to create an event and listener?
```bash
php artisan make:event UserRegistered
php artisan make:listener SendWelcomeEmail --event=UserRegistered
```

### 41. What is API Resource in Laravel?
API Resource ek tarah ka transformer hota hai jo aapke model data ko JSON format me structured aur clean banata hai jab aap API response bhejte hain. Ye aapko data ko customize karne ki facility deta hai, jaise kisi field ko hide karna ya extra information add karna.

### 42. How to create API Resource?
```bash
php artisan make:resource UserResource
```
Phir isme toArray() method me aap specify karte hain ke API me kaunse fields bhejne hain.


### 43. What is policy in Laravel?
Policy authorization ka ek component hai jo user permissions ko control karta hai. Ye decide karta hai ke kaun user kis resource pe kaunse actions kar sakta hai, jaise edit, delete, ya view.


### 44. How to create and use policy?
Policy banane ke liye:
```bash
php artisan make:policy PostPolicy --model=Post
```
Phir AuthServiceProvider me policy register karni hoti hai. Controller ya routes me authorize method se permission check karte hain.


### 45. What are Laravel Collections?
Collections ek enhanced array object hain jo bohat saare useful methods provide karte hain jaise filtering, mapping, reducing. Ye data ko manipulate karna easy banata hai aur readable code likhne me madad karta hai.


### 46. How to use eager loading in Laravel?
Eager loading database queries ko optimize karta hai jab related models fetch karne hon, taake N+1 query problem na ho. Example:

```bash
$users = User::with('posts')->get();
```


### 47. What is caching in Laravel?
Caching frequently used data ko temporary storage me rakhna hota hai taake application faster response de. Laravel multiple cache drivers support karta hai jaise file, Redis, Memcached.

### 48. How to clear cache in Laravel?
```bash
php artisan cache:clear
php artisan config:clear
php artisan route:clear

```

### 49. What is task scheduling in Laravel?
Task scheduling se aap repetitive commands ko automatically chalwa sakte hain jaise daily emails, cleanup tasks, etc. Ye cron jobs ki tarah kaam karta hai. Laravel me app/Console/Kernel.php me schedule define karte hain.

### 50 . How to schedule a task?
Kernel.php me schedule() method me likhte hain:

```bash
$schedule->command('emails:send')->daily();

```


### 51. What is Laravel Passport?
Laravel Passport is a full OAuth2 server implementation for API authentication. It helps you easily set up secure API authentication using access tokens, refresh tokens, and scopes without building the system from scratch.

### 52. How to install and configure Laravel Passport?
```bash
composer require laravel/passport
```

**Then run migrations and install Passport:**
```bash
php artisan migrate
php artisan passport:install
```
Add Laravel\Passport\HasApiTokens trait in your User model and configure API authentication guard to use Passport.


### 53. What is Laravel Sanctum?
Sanctum provides a lightweight authentication system for SPAs (Single Page Applications), mobile apps, and simple token-based APIs. It’s simpler than Passport and focuses on issuing API tokens with abilities.


### 54. Difference between Passport and Sanctum?
Passport is for full OAuth2 server with all the features like scopes, refresh tokens, etc. Sanctum is simpler, mainly for token-based auth for SPAs and mobile apps.


### 55. What are observers in Laravel?
Observers listen to model events like creating, updating, deleting, and allow you to execute code when those events happen — useful for keeping your models clean.

### 56. How to create and use an observer?
```bash
php artisan make:observer UserObserver --model=User
```
**Register it in AppServiceProvider or any service provider:**

```bash
User::observe(UserObserver::class);
```

```bash
User::observe(UserObserver::class);
```

### 57. What is the use of the boot() method in models?
The boot() method in Eloquent models allows you to define event hooks for that model such as creating, updating, deleting events to run custom logic.

### What are mutators and accessors?
Mutators let you modify a model attribute before saving it to the database. Accessors let you modify an attribute when retrieving it. For example, formatting a date or encrypting a password.


### 59. How to create a mutator?
```bash
public function setPasswordAttribute($value) {
    $this->attributes['password'] = bcrypt($value);
}
```

### 60. How to create an accessor?
```bash
public function getNameAttribute($value) {
    return ucfirst($value);
}
```

### 61. What is the Repository Pattern?
It’s a design pattern to separate the logic of data retrieval (database queries) from business logic by using repository classes, making code easier to maintain and test.

### 62. How to implement the Repository Pattern?
Create repository interfaces and concrete classes to handle data access. Inject these repositories into controllers or services instead of directly using models.

### 63. What is broadcasting in Laravel?
Broadcasting allows you to share server-side events with client-side JavaScript in real-time using WebSockets.

### 64. How to configure broadcasting?
Set up a broadcasting driver (Pusher, Redis) in .env and config/broadcasting.php. Define events that implement ShouldBroadcast interface.


### 65. What is the difference between HasMany and BelongsTo relationships?
HasMany is used when one model owns many related models (e.g., User has many Posts).
BelongsTo is the inverse — the related model belongs to one parent (Post belongs to User).


### 66. How to define a many-to-many relationship?
Use belongsToMany method in both models. Example:

```bash
public function roles() {
    return $this->belongsToMany(Role::class);
}
```

### 67. What is polymorphic relationship?
It allows a model to belong to more than one other model on a single association. Example: Comments can belong to posts or videos.

### 68. How to implement polymorphic relations?
Use methods like morphMany and morphTo with a single table to handle multiple model types.

### 69. What is a job middleware in Laravel?
Job middleware allows you to add extra logic or constraints on queued jobs, such as rate limiting or timeout handling.


### 70. How to create custom validation rules?
You can create custom validation rules by making a rule class:
```bash
php artisan make:rule Uppercase

```
**Define your validation logic inside the passes() method.**


### 71. What is the use of when() method in query builder?
The when() method conditionally adds query constraints, which keeps your query clean and readable.

```bash
User::when($role, function ($query) use ($role) {
    return $query->where('role', $role);
})->get();
```

### 72. How to prevent SQL Injection in Laravel?
Laravel's query builder and Eloquent use PDO parameter binding by default, which prevents SQL injection.

### 73. What is the purpose of softDeletes() in migration?
It adds a nullable deleted_at timestamp column, which allows soft deletion of records (marking as deleted without removing from DB).

### 74. How to restore soft deleted records?
Use withTrashed() to include soft deleted records in query, and then restore() to recover them:

```bash
Post::withTrashed()->find($id)->restore();
```

### 75. What is a Form Request in Laravel?
A Form Request is a custom request class used for encapsulating validation logic and authorization checks.


### 76. How to create a Form Request?
```bash
php artisan make:request StoreUserRequest
```
Define rules in rules() and authorization in authorize() methods.


### 77. How to handle file uploads in Laravel?
Use the store() or storeAs() methods on the uploaded file object to save files to configured disks.
```bash
$request->file('avatar')->store('avatars');
```

### 78. What is the use of config() helper?
It accesses or sets configuration values at runtime, e.g.,
```bash
config('app.timezone');
```

### 79. How to cache database queries in Laravel?
You can use the remember() method on queries to cache results for a specific time.
```bash
$users = Cache::remember('users', 60, function () {
    return User::all();
});
```


### 80. What is scope in Laravel models?
Scopes allow you to define common query constraints that can be reused. For example:
```bash
public function scopeActive($query) {
    return $query->where('active', 1);
}
```
**User::active()->get();**


### 82. How to use Laravel Mix to compile assets?
Define your asset pipeline in webpack.mix.js, for example:
```bash
mix.js('resources/js/app.js', 'public/js')
   .sass('resources/sass/app.scss', 'public/css');

```
**Then run:**
```bash
npm run dev
```


### 83. What is the difference between Route::get() and Route::post()?
Route::get() handles HTTP GET requests, usually for fetching data or displaying pages.
Route::post() handles HTTP POST requests, typically used for submitting forms or sending data.


### 84. What is the difference between abort(404) and throw new NotFoundHttpException()?
abort(404) immediately returns a 404 response with an optional message.
throw new NotFoundHttpException() throws an exception which Laravel handles and converts to a 404 response.


### 85. What is CSRF protection and how does Laravel handle it?
CSRF (Cross-Site Request Forgery) is an attack where unauthorized commands are transmitted from a user trusted by the application. Laravel automatically adds CSRF tokens to forms and verifies them on submission to prevent this.


### 86. How to exclude routes from CSRF verification?
Add route URIs to the $except array in the VerifyCsrfToken middleware located at app/Http/Middleware/VerifyCsrfToken.php.


### 87. What are Middlewares in Laravel?
Middleware are filters that inspect and manipulate HTTP requests entering your application. They can perform tasks like authentication, logging, CORS handling, etc.


### 88. How to create and register a middleware?
```bash
php artisan make:middleware CheckAge

```
Register in app/Http/Kernel.php either as route or global middleware.


### 90. What are Laravel Notifications?
Notifications provide a way to send messages via multiple channels like email, SMS, Slack, or database.


### 91. How to create and send a notification?
```bash
php artisan make:notification InvoicePaid
```
**Send using:**
```bash
$user->notify(new InvoicePaid($invoice));
```


### 92. What is Laravel Telescope?
Laravel Telescope is a debugging assistant that provides insight into requests, exceptions, database queries, queues, and more, making debugging easier.


### 93. How to install Laravel Telescope?
```bash
composer require laravel/telescope
```

**Then run migrations and publish assets:**
```bash
php artisan telescope:install
php artisan migrate
```


### 94. What is the purpose of the dispatch_now() method?
dispatch_now() runs a queued job immediately in the current process, instead of pushing it to the queue.

### 95. How to handle exceptions globally in Laravel?
Customize the render() and report() methods in the app/Exceptions/Handler.php to handle exceptions globally.



### 96. What is the use of the tap() helper function?
tap() allows you to call a callback with the given value and then return the value, useful for performing actions in a fluent pipeline.
```bash
return tap(User::first(), function ($user) {
    $user->update(['last_logged_in' => now()]);
});
```


### 97. What are custom macros in Laravel?
Macros allow you to add custom methods to existing classes at runtime, extending functionality without modifying original code.

### 98. How to create a custom macro?
```bash
Str::macro('reverse', function ($string) {
    return strrev($string);
});
```


### 99. What is the difference between sync() and attach() in many-to-many relationships?
attach() adds new records to the pivot table without removing existing ones.
sync() updates the pivot table to match the provided IDs, removing any not in the list.


### 100. How to handle multiple database connections in Laravel?
Define multiple connections in config/database.php and specify the connection in the model or query using:

```bash
DB::connection('connection_name')->table('users')->get();
```