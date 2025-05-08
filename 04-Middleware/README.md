# Laravel - Middleware
Middleware acts as a bridge between a request and a response. It is a type of filtering mechanism. This chapter explains you the middleware mechanism in Laravel.

Laravel includes a middleware that verifies whether the user of the application is authenticated or not. If the user is authenticated, it redirects to the home page otherwise, if not, it redirects to the login page.

### 🔧 What Middleware Can Do
* ✅ Check if a user is authenticated
* 🔒 Restrict access to certain routes
* 🧼 Sanitize input or modify headers
* 🔁 Log request/response
* 🌐 Handle CORS, API tokens, etc.
 
```bash
php artisan make:middleware CheckRole
```