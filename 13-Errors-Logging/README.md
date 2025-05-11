
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
