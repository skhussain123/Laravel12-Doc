

#  Laravel Collections (Higher Order Functions)
Laravel Collections are powerful wrappers around arrays with lots of handy methods for working with data.

Higher Order Functions let you write cleaner and more readable code by calling methods on each item without writing explicit loops or callbacks.


### What are Higher Order Functions?
Instead of writing this:

```bash
$users->filter(function ($user) {
    return $user->active;
});

```
**You can write:**
```bash
$users->filter->active;
```
Laravel calls the active property or method on each item automatically.

### Common Higher Order Collection Methods
| Method     | Description                     | Example                      |
| ---------- | ------------------------------- | ---------------------------- |
| `filter`   | Filter items by property/method | `$users->filter->active`     |
| `reject`   | Remove items by property/method | `$users->reject->banned`     |
| `map`      | Transform items                 | `$users->map->formatName()`  |
| `each`     | Run code for each item          | `$users->each->markAsRead()` |
| `contains` | Check if any item has property  | `$users->contains('admin')`  |
| `pluck`    | Get list of property values     | `$users->pluck('email')`     |


### Example Usage
Suppose you have a collection of users, each with an active boolean property:
```bash
$activeUsers = $users->filter->active;
```
This automatically keeps users where $user->active == true.


### Using Higher Order Messages with Methods
```bash
$users->each->sendWelcomeEmail();

```

**Equivalent to:**
```bash
$users->each(function ($user) {
    $user->sendWelcomeEmail();
});
```

### Summary Table
| Feature                  | Without Higher Order Function             | With Higher Order Function  |
| ------------------------ | ----------------------------------------- | --------------------------- |
| Filter active users      | `$users->filter(fn($u) => $u->active)`    | `$users->filter->active`    |
| Call method on each user | `$users->each(fn($u) => $u->sendEmail())` | `$users->each->sendEmail()` |


