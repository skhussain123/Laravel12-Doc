

# Laravel - Cookie
In Laravel, Cookies are small pieces of data stored in the user's browser. You can use cookies to store temporary information like user preferences, tokens, etc.

Laravel automatically encrypts and decrypts cookies to keep data safe. You don’t need to encrypt manually.

### 1. Set a Cookie
```bash
return response('Hello User')
            ->cookie('user_name', 'Ali', 60); // 60 minutes

Cookie::queue('user_name', 'check', 60);

```

### 2. Getting a Cookie (Cookie lena)
```bash
public function getCookie(Request $request) {
    $name = $request->cookie('user_name');
    return 'Cookie Value: ' . $name;
}

```

### 3. Deleting a Cookie (Cookie delete karna)
```bash
return response('Cookie Deleted')
            ->cookie('user_name', '', -1);
```