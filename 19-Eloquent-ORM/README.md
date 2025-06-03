


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
Ye methods aap Models ke zariye use karte ho (jaise: User::where(...), User::create(...), etc.)
Ye object-oriented aur expressive syntax provide karta hai.
| Method                     | Description                                   |
| -------------------------- | --------------------------------------------- |
| `create()`                 | New record insert with mass assignment        |
| `save()`                   | Record ko manually save karta hai             |
| `update()`                 | Record update karta hai                       |
| `delete()`                 | Record delete karta hai                       |
| `first()`                  | Pehla result laata hai                        |
| `get()`                    | Sab results laata hai                         |
| `find(id)`                 | ID ke zariye record find karta hai            |
| `firstOrCreate()`          | Record exist kare to laaye, warna insert kare |
| `updateOrCreate()`         | Exist kare to update, warna create kare       |
| `firstOrNew()`             | Exist kare to laaye, warna object banaye      |
| `pluck()`                  | Sirf ek column ki values laata hai            |
| `with()`                   | Eager loading (relations ke sath)             |
| `has()`                    | Relation filter karne ke liye                 |
| `whereHas()`               | Relation-based condition                      |
| `belongsTo()`, `hasMany()` | Relationship define karte hain                |



### 7. Query Builder Methods
Ye methods aap DB facade ke through use karte ho (DB::table('users')->where(...), etc.)
Ye lightweight aur direct SQL-like queries banata hai.

| Method                             | Description                   |
| ---------------------------------- | ----------------------------- |
| `insert()`                         | Data insert karta hai         |
| `update()`                         | Data update karta hai         |
| `delete()`                         | Data delete karta hai         |
| `select()`                         | Columns select karta hai      |
| `where()`                          | Condition lagata hai          |
| `get()`                            | Sab records laata hai         |
| `first()`                          | Pehla record laata hai        |
| `pluck()`                          | Ek column ki values laata hai |
| `join()`                           | Table join karta hai          |
| `orderBy()`                        | Sorting                       |
| `limit()`                          | Limit set karta hai           |
| `count()`                          | Count laata hai               |
| `avg()`, `sum()`, `min()`, `max()` | Aggregates                    |




### Summary
| Concept       | Description                             |
| ------------- | --------------------------------------- |
| Eloquent ORM  | Laravel’s object-oriented database tool |
| Models        | Represent tables                        |
| Records       | Rows become model objects               |
| Relationships | Built-in methods for table relations    |



### Query Builder vs Eloquent
| Feature           | **Query Builder**                      | **Eloquent ORM**                        |
| ----------------- | -------------------------------------- | --------------------------------------- |
| **Definition**    | Fluent and low-level SQL query builder | High-level Active Record implementation |
| **Approach**      | Array-based, manual                    | Object-oriented, model-based            |
| **Performance**   | Slightly faster                        | Slightly slower (due to object mapping) |
| **Readability**   | Closer to SQL                          | Cleaner and more expressive             |
| **Relationships** | Manual joins required                  | Built-in relationship handling          |
| **Return Type**   | Arrays                                 | Model objects                           |
| **Use Case**      | When you need custom, complex SQL      | When you want clean, maintainable code  |


### 1. Example: Fetch All Posts
**Query Builder:**
```bash
$posts = DB::table('posts')->get();
```

**Eloquent:**
```bash
use App\Models\Post;
$posts = Post::all();
```


###  2. Example: Insert Data

**Query Builder:**
```bash
DB::table('posts')->insert([
    'title' => 'New Post',
    'body' => 'Post content here'
]);
```

**Eloquent:**
```bash
Post::create([
    'title' => 'New Post',
    'body' => 'Post content here'
]);
```


### 3. Example: Where & Conditions
**Query Builder:**
```bash
$posts = DB::table('posts')
    ->where('status', 'published')
    ->orderBy('created_at', 'desc')
    ->get();
```

**Eloquent:**
```bash
$posts = Post::where('status', 'published')
    ->orderBy('created_at', 'desc')
    ->get();
```

### 4. Example: Relationships
**Query Builder:**

```bash
$comments = DB::table('comments')
    ->where('post_id', 1)
    ->get();

```

**Eloquent:**
```bash
$post = Post::find(1);
$comments = $post->comments; // if hasMany relationship is defined

```

### 5. When to Use What

| Scenario                                 | Use             |
| ---------------------------------------- | --------------- |
| You want fast, custom SQL queries        | ✅ Query Builder |
| You want elegant, clean code             | ✅ Eloquent      |
| You work with table joins manually       | ✅ Query Builder |
| You work with models and relationships   | ✅ Eloquent      |
| You need speed with minimal overhead     | ✅ Query Builder |
| You want maintainability and scalability | ✅ Eloquent      |



