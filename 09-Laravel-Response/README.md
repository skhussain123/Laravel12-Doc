

# Laravel - Response 
In Laravel, a Response is what your application sends back to the browser or client after it handles a request — like showing a page, sending JSON, redirecting, etc.

### 1. Basic String Response
```bash
return "Welcome to Laravel!";
```

### 2. View Response
```bash
return view('home');
```

### 3. JSON Response (APIs ke liye)
```bash
return response()->json([
    'name' => 'Ali',
    'email' => 'ali@example.com',
]);
```

### 4. Redirect Response
```bash
return redirect('/dashboard');
```

Or redirect to a named route:
```bash
return redirect()->route('home');
```

### 5. Attach Cookie to Response
```bash
return response('Hello')->cookie('user', 'Ali', 60);
```

### 6. Custom Status Code
```bash
return response('Not Found', 404);
```


### 7. Download Response
```bash
return response()->download(public_path('file.pdf'));
```