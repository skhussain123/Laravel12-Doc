


# 1. What is a Model in Laravel?
A Model represents a database table. Each model interacts with a specific table using Eloquent ORM (Laravel’s built-in ORM).

```bash
php artisan make:model Post
```
This creates a Post.php model in app/Models.


```bash
use App\Models\Post;

$posts = Post::all();              // Get all posts
$post = Post::find(1);             // Find post by ID
Post::create(['title' => 'Test']); // Create a new post


```

## 2. What is a Migration in Laravel?
A Migration is a PHP file that defines the structure of a database table (create, update, delete). It's like version control for your database.

```bash
php artisan make:migration create_posts_table
```
This creates a file in database/migrations.


###  Inside Migration File:
```bash
public function up()
{
    Schema::create('posts', function (Blueprint $table) {
        $table->id();
        $table->string('title');
        $table->text('body')->nullable();
        $table->timestamps();
    });
}

```

###  Run Migration:
```bash
php artisan migrate
```


### Common Migration Commands

| Command                                         | Description                               |
| ----------------------------------------------- | ----------------------------------------- |
| `php artisan make:migration create_users_table` | Create a new migration                    |
| `php artisan migrate`                           | Run all migrations                        |
| `php artisan migrate:rollback`                  | Undo the last batch                       |
| `php artisan migrate:fresh`                     | Drop all tables and re-run all migrations |
| `php artisan migrate:status`                    | See which migrations have run             |
| `php artisan make:model Post -m`                | Create a new migration   with model       |




