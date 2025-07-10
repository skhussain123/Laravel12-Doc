

# Laravel - Cookie
In Laravel, Cookies are small pieces of data stored in the user's browser. You can use cookies to store temporary information like user preferences, tokens, etc.

Laravel automatically encrypts and decrypts cookies to keep data safe. You don’t need to encrypt manually.

### 1. Set a Cookie
```bash
return response('Hello User')
            ->cookie('user_name', 'Ali', 60); // 60 minutes

Cookie::queue('user_name', 'check', 60);

```

### 2. Update
```bash
 Cookie::queue('user_name', 'UpdatedHussain', 60); // old value overwrite ho jayegi
```

### 3. Deleting a Cookie (Cookie delete karna)
```bash
Cookie::queue(Cookie::forget('user_name'));
```

| Operation | Code                                         | Explanation                  |
| --------- | -------------------------------------------- | ---------------------------- |
| Create    | `Cookie::queue('name', 'value', minutes)`    | Browser me cookie set krna   |
| Read      | `$request->cookie('name')`                   | Cookie ki value lena         |
| Update    | `Cookie::queue('name', 'newValue', minutes)` | Same name se dobara set krdo |
| Delete    | `Cookie::queue(Cookie::forget('name'))`      | Cookie ko delete krna        |

