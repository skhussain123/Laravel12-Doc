


#  Laravel Eloquent ORM (Object-Relational Mapping)
Eloquent ORM is Laravel’s built-in way to interact with your database using PHP objects instead of raw SQL queries. It simplifies CRUD operations and handles relationships between tables easily.

### 1. What is Eloquent?
Eloquent maps database tables to PHP classes (Models), and rows to objects.

```bash
use App\Models\Post;

$posts = Post::all(); // Returns all rows from posts table as Post objects

```

###  2. Basic CRUD with Eloquent
| Operation | Example                                                                 |
| --------- | ----------------------------------------------------------------------- |
| Create    | `Post::create(['title' => 'New Post']);`                                |
| Read      | `Post::find(1);` or `Post::where('title', 'Like', '%Laravel%')->get();` |
| Update    | `$post = Post::find(1); $post->title = 'Updated'; $post->save();`       |
| Delete    | `$post = Post::find(1); $post->delete();`                               |


Make sure $fillable or $guarded is set in your model to allow mass assignment.

```bash
protected $fillable = ['title', 'body'];
```

### 3. Eloquent Relationships
Eloquent makes it easy to work with related tables.

#### One to One
```bash
// User.php
public function profile() {
    return $this->hasOne(Profile::class);
}

// Profile.php
public function user() {
    return $this->belongsTo(User::class);
}

```

#### One to Many
```bash
// Post.php
public function comments() {
    return $this->hasMany(Comment::class);
}
```

#### Many to Many
```bash
// Post.php
public function tags() {
    return $this->belongsToMany(Tag::class);
}
```

#### Accessing Relationships
```bash
$user = User::find(1);
$profile = $user->profile;

$post = Post::with('comments')->find(1);
```

### 4. Query Builder with Eloquent
Eloquent uses Laravel’s query builder under the hood:
```bash
$posts = Post::where('is_published', true)->orderBy('created_at', 'desc')->get();
```
**Other common methods:**

1. first()
2. get()
3. count()
4. exists()
5. pluck('column')


### 6. Useful Eloquent Methods
| Method            | Description                         |
| ----------------- | ----------------------------------- |
| `all()`           | Get all records                     |
| `find(id)`        | Get record by ID                    |
| `where()`         | Add conditions                      |
| `create()`        | Create a record                     |
| `update()`        | Update a record                     |
| `delete()`        | Delete a record                     |
| `with()`          | Eager load relationships            |
| `firstOrCreate()` | Find or create                      |
| `firstOrFail()`   | Get first or throw 404 if not found |



### Summary
| Concept       | Description                             |
| ------------- | --------------------------------------- |
| Eloquent ORM  | Laravel’s object-oriented database tool |
| Models        | Represent tables                        |
| Records       | Rows become model objects               |
| Relationships | Built-in methods for table relations    |


