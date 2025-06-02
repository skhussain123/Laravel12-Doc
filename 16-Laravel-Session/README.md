

# Laravel - Session
Sessions are used to store information about the user across multiple requests. For example, once a user logs in, session data is used to remember them on every page.


### Laravel Provides Multiple Session Drivers:
Laravel offers several options (drivers) to store session data:

* file – stores sessions in files (default)
* cookie – stores entire session in a cookie
* database – stores sessions in a database table
* apc – uses APC cache
* memcached – uses Memcached for fast session storage
* redis – uses Redis, good for scalable apps
* array – used for testing; data is not stored between requests


### Default Driver
By default, Laravel uses the file driver, because it’s simple and lightweight.
```bash
// config/session.php
'driver' => 'file',
```

### Where Is Session Data Configured?
```bash
config/session.php
```


### 1. Store Data in Session
```bash
session(['key' => 'value']);
```
or
```bash
Session::put('username', 'Ali');
```

### 2. Retrieve Data from Session
```bash
$value = session('key');
```
Or:

```bash
$username = Session::get('username');
```

### 3. Check if Session Key Exists
```bash
if (Session::has('username')) {
    // Do something
}
```

### 4. Remove (Forget) a Session Value
```bash
Session::forget('username');
```

### 5. Remove All Session Data
```bash
Session::flush();
```

### 6. Flash Data (One-time Session)
```bash
Session::flash('success', 'User created successfully!');
```

### 7. Regenerate Session ID (Security Purpose)
```bash
Session::regenerate();
```

| Task             | Syntax                           |
| ---------------- | -------------------------------- |
| Store session    | `Session::put('key', 'value')`   |
| Retrieve session | `Session::get('key')`            |
| Check key exists | `Session::has('key')`            |
| Delete one key   | `Session::forget('key')`         |
| Delete all       | `Session::flush()`               |
| Flash message    | `Session::flash('key', 'value')` |
| Regenerate ID    | `Session::regenerate()`          |
