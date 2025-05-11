


# Laravel Forms 
In Laravel, Forms are used to collect user input and send it to the server for processing (like login, registration, contact, etc.). Laravel provides powerful tools for form handling, validation, and CSRF protection.


### 1. Create a Basic HTML Form
```bash
<form action="/submit" method="POST">
    @csrf
    <input type="text" name="name" placeholder="Enter your name">
    <button type="submit">Submit</button>
</form>
```

* @csrf — Laravel ka security token hota hai jo har form me zaroori hai.
* action="/submit" — Form kahan bhejna hai (route ya URL).
* method="POST" — Data server ko bhejne ka method.


### 2. Form Data Handle Karna (Controller ya Route me)
```bash
Route::post('/submit', function (Illuminate\Http\Request $request) {
    $name = $request->input('name');
    return "Hello, $name";
});

```


### 3. Validation in Controller
```bash
public function store(Request $request)
{
    $request->validate([
        'name' => 'required|min:3',
    ]);

    // Save or process the data
    return redirect()->back()->with('success', 'Form submitted!');
}
```


### 4. Show Validation Errors in Blade File
```bash
@if ($errors->any())
    <ul>
        @foreach ($errors->all() as $error)
            <li>{{ $error }}</li>
        @endforeach
    </ul>
@endif
```

### 5. Old Input Values Show Karna
```bash
<input type="text" name="name" value="{{ old('name') }}">
```

| Task                  | Syntax Example                       |
| --------------------- | ------------------------------------ |
| Start Form            | `<form method="POST" action="/url">` |
| CSRF Protection       | `@csrf`                              |
| Input Field           | `<input name="name">`                |
| Validation            | `$request->validate([...])`          |
| Old Input Value       | `value="{{ old('name') }}"`          |
| Show Errors           | `$errors->any()`, `$errors->all()`   |
| Redirect with Success | `redirect()->with('success', 'msg')` |




### 6. From Validations
```bash

public function store(Request $request)
{
    $request->validate([
        'name' => 'required|min:3',
        'email' => 'required|email',
        'password' => 'required|min:6',
    ],
    [
        'name.required' => 'Please enter your name',
        'email.required' => 'Please enter your email',
        'email.email' => 'Enter a valid email address',
        'password.required' => 'Please enter a password',
        'password.min' => 'Password must be at least 6 characters'
    ]);

    // Save or process the data here...

    return redirect()->back()->with('success', 'Form submitted!');
}

```