

#  Laravel Rate Limiting & Throttling
Rate Limiting is a way to control the number of requests a user or client can make to your application in a given time window. This protects your app from abuse or overload.


### Why Use Rate Limiting?

* Prevent API abuse or brute-force attacks.
* Protect server resources.
* Improve overall app stability.


### Laravel Throttle Middleware
Laravel comes with built-in throttle middleware to easily add rate limiting.

### How to Use Throttle Middleware
You can apply it to routes like this:

```bash
Route::middleware('throttle:60,1')->group(function () {
    Route::get('/api/data', 'DataController@index');
});
```

* 60 = max 60 requests
* 1 = per 1 minute


### Customize Throttle with Named Middleware
In app/Http/Kernel.php, middleware alias:
```bash
'throttle' => \Illuminate\Routing\Middleware\ThrottleRequests::class,
```

###  Using Rate Limiting in API Routes
By default, api.php routes use throttle middleware with limits set in RouteServiceProvider.

### Testing Rate Limits
If a client exceeds the limit, Laravel returns:

```bash
{
  "message": "Too Many Attempts."
}
```
with HTTP status 429.



| Feature                 | Usage                             |
| ----------------------- | --------------------------------- |
| Basic throttle          | `throttle:60,1` middleware        |
| Custom rate limiter     | Define in `RateLimiter::for()`    |
| Limit by user or IP     | Use `by()` method in rate limiter |
| Response when limit hit | HTTP 429 with "Too Many Attempts" |


