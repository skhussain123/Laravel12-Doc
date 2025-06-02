
# Errors
A project while underway, is borne to have a few errors. Errors and exception handling is already configured for you when you start a new Laravel project. Normally, in a local environment we need to see errors for debugging purposes. We need to hide these errors from users in production environment. This can be achieved with the variable APP_DEBUG set in the environment file .env stored at the root of the application.

For local environment the value of APP_DEBUG should be true but for production it needs to be set to false to hide errors.

Note − After changing the APP_DEBUG variable, you should restart the Laravel server.


### Logging
Logging is an important mechanism by which system can log errors that are generated. It is useful to improve the reliability of the system. Laravel supports different logging modes like single, daily, syslog, and errorlog modes. You can set these modes in config/app.php file.

```bash
'log' => 'daily'
```

You can see the generated log entries in storage/logs/laravel.log file.


### Rendering Exceptions
The render method is responsible for converting exceptions into HTTP responses. Laravel automatically renders appropriate error pages for common exceptions like 404 Not Found or 500 Internal Server Error.

For custom exceptions, you can define how they should be rendered by overriding the render method in the Handler.php file.

For example, to render a custom error page for a CustomException:
```bash
public function render($request, Throwable $exception)
{
    if ($exception instanceof CustomException) {
        return response()->view('errors.custom', [], 500);
    }

    return parent::render($request, $exception);
}

```