# Laravel Routing (Latest Version: Laravel 12)
Routing in Laravel is the system that maps URLs (like /login, /dashboard, etc.) to specific code—either a controller method or a closure—that handles the request and returns a response.

Laravel has a clean and flexible routing mechanism that allows you to easily define:
* Web routes for pages (views)
* API routes for APIs (stateless)
* Console routes for Artisan commands
* Broadcast channels for real-time communication


| File           | Purpose                                            |
| -------------- | -------------------------------------------------- |
| `web.php`      | Routes for browser (session, CSRF, cookies, views) |
| `api.php`      | Routes for REST APIs (stateless)                   |
| `console.php`  | Artisan CLI commands                               |
| `channels.php` | Laravel Echo and broadcasting channels             |


