

#  1. Session Management in Laravel
Session is used to store data across multiple requests — like login status, user preferences, or temporary variables.


### Common Session Methods
| Method                        | Description                   |
| ----------------------------- | ----------------------------- |
| `session(['key' => 'value'])` | Store data in session         |
| `session('key')`              | Get value from session        |
| `session()->has('key')`       | Check if a session key exists |
| `session()->forget('key')`    | Remove one item from session  |
| `session()->flush()`          | Remove all session data       |




```bash
// Store value in session
session(['username' => 'check']);

// Get value
$name = session('username');

// Remove specific key
session()->forget('username');

// Remove all session data
session()->flush();

```


### 2. Flash Messages in Laravel
Flash messages are stored in the session but only available for the next request — usually used after redirects.

**Use Case:**
Show success, error, or warning messages after form submission or actions (like "Post created successfully").

### Setting Flash Message

```bash
// In Controller
return redirect()->back()->with('success', 'Post created successfully!');
```

### Showing in Blade View
```bash
@if(session('success'))
    <div class="alert alert-success">
        {{ session('success') }}
    </div>
@endif

```
**You can use multiple types:**

### Summary Table
| Concept        | Purpose                          | Duration                 |
| -------------- | -------------------------------- | ------------------------ |
| Session        | Store user-specific data         | Until removed or expired |
| Flash Messages | Temporary message after redirect | One request only         |


### Bonus: Blade Component for Alerts

```bash
@if(session()->has('success'))
    <x-alert type="success" :message="session('success')" />
@endif

```