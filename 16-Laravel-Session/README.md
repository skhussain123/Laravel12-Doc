

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


| Driver             | Description                                                                                              | Best Use Case                                                  |
| ------------------ | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| `file` *(default)* | Session data ko storage path (usually `storage/framework/sessions`) me files ki form me store karta hai. | Local dev ya choti apps                                        |
| `cookie`           | Pura session data browser ke cookie me store hota hai (encrypted).                                       | Stateless apps ya lightweight session data                     |
| `database`         | Session data ek specific database table me store hota hai (usually `sessions` table).                    | Jab aapko centralized session chahiye multiple servers ke liye |
| `apc`              | APC (Alternative PHP Cache) ko use karta hai (server-side cache).                                        | Jab APC enabled ho aur fast access chahiye                     |
| `memcached`        | Session data Memcached me store hota hai — ek in-memory key-value store.                                 | Large scale, high-performance apps                             |
| `redis`            | Session data Redis me store hota hai — fast, scalable, and durable.                                      | High-concurrency ya distributed apps                           |
| `array`            | Session sirf memory me store hota hai aur next request me remove ho jata hai.                            | Testing purpose only (not persistent)                          |


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
