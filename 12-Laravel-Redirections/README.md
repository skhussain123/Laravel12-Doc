
# Laravel - Redirections
Laravel me Redirection ka matlab hai ek request ke baad user ko kisi dusre page ya route par bhejna. Laravel me redirection karna bohot simple hai using built-in methods.



### 1. Basic Redirect
```bash
return redirect('/home');
```


### 2. Redirect to Named Route
```bash
return redirect()->route('dashboard');
```

### 3. Redirect with Data (Flash Message)
```bash
return redirect('/home')->with('success', 'Logged in successfully!');
```

### 4. Redirect Back (Pichlay Page pe wapas jana)
```bash
return redirect()->back();
```


### 5. Redirect to Controller Action
```bash
return redirect()->action([UserController::class, 'profile']);
```

### 6. Redirect with Input (Old Form Data)
```bash
return redirect()->back()->withInput();
```


```bash
Route::get('/test', ['as'=>'testing',function() {
   return view('test2');
}]);

Route::get('redirect',function() {
   return redirect()->route('testing');
});

```

```bash
Route::get('rr','RedirectController@index');
Route::get('/redirectcontroller',function() {
   return redirect()->action('RedirectController@index');
});
```


| Task                     | Code Example                                   |
| ------------------------ | ---------------------------------------------- |
| Redirect to URL          | `redirect('/home')`                            |
| Redirect to named route  | `redirect()->route('route_name')`              |
| Redirect back            | `redirect()->back()`                           |
| Redirect with message    | `redirect()->with('msg', 'text')`              |
| Redirect with input data | `redirect()->back()->withInput()`              |
| Redirect to controller   | `redirect()->action([Controller::class, 'm'])` |


