

# Laravel Accessors & Mutators (Eloquent Attribute Casting)
Accessors and Mutators in Laravel allow you to format data when getting or setting attributes on Eloquent models.

## 1. Accessors – Format Data When Getting It
Accessors modify the value when retrieving it from the database.

###  Syntax:
```bash
public function get{AttributeName}Attribute($value)
```

### Example:
```bash
// app/Models/User.php

public function getNameAttribute($value)
{
    return ucfirst($value); // Capitalize first letter
}

```

### Usage:
```bash
$user = User::find(1);
echo $user->name; // Automatically capitalized

```

## 2. Mutators – Format Data Before Saving
Mutators modify the value before saving it to the database.

```bash
public function set{AttributeName}Attribute($value)

```

```bash
public function setPasswordAttribute($value)
{
    $this->attributes['password'] = bcrypt($value);
}

```

### Usage:
```bash
$user = new User;
$user->password = 'secret'; // Automatically hashed
$user->save();

```

## 3. New Style (Laravel 9+) — Using Attribute Class
```bash
use Illuminate\Database\Eloquent\Casts\Attribute;

protected function name(): Attribute
{
    return Attribute::make(
        get: fn ($value) => ucfirst($value),
        set: fn ($value) => strtolower($value),
    );
}

```

### 4. Practical Use Cases
| Field        | Accessor                      | Mutator                 |
| ------------ | ----------------------------- | ----------------------- |
| `name`       | Capitalize before showing     | Lowercase before saving |
| `created_at` | Format to human-readable date | —                       |
| `email`      | —                             | Save as lowercase       |
| `password`   | —                             | Hash before saving      |


