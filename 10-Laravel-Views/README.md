


# Laravel - Views 
In Laravel, a View is a file that contains HTML + Blade syntax. It is used to display the user interface of your web application — like showing a page, form, or layout.

All view files are stored in the resources/views/ folder.
Laravel uses the .blade.php extension for view files because it supports Blade Templating Engine.

### 2. Return a View in Controller or Route
```bash
return view('home');
```

### 3. Passing Data to View
```bash
return view('home', ['name' => 'Ali']);
```

**Then in your Blade file:**
```bash
<p>Welcome, {{ $name }}</p>
```

| Task            | Blade Syntax             |
| --------------- | ------------------------ |
| Echo variable   | `{{ $name }}`            |
| If condition    | `@if ($age > 18)`        |
| For loop        | `@for`, `@foreach`, etc. |
| Include partial | `@include('header')`     |
| Layout extend   | `@extends('layout')`     |



### 5. Create a Layout File
```bash
<!-- resources/views/layouts/app.blade.php -->
<html>
  <body>
    @yield('content')
  </body>
</html>

```


```bash
@extends('layouts.app')

@section('content')
  <h1>This is Home Page</h1>
@endsection

```
@extends se layout use kiya ja raha hai aur @section me apna content diya gaya hai.


### 6. Include Another View
Yeh dusri view file (jaise header) ko is file ke andar include kar raha hai.

| Feature          | Usage Example                      |
| ---------------- | ---------------------------------- |
| Return view      | `view('home')`                     |
| Send data        | `view('home', ['key' => 'value'])` |
| Blade variable   | `{{ $key }}`                       |
| Conditional      | `@if`, `@else`, `@endif`           |
| Looping          | `@foreach`, `@for`, `@while`       |
| Layouts          | `@extends`, `@section`, `@yield`   |
| Include partials | `@include('file')`                 |
