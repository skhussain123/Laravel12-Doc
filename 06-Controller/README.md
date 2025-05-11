

# Laravel - Controllers
In the MVC framework, the letter C stands for Controller. It acts as a directing traffic between Views and Models. In this chapter, you will learn about Controllers in Laravel.

## Creating a Controller
Open the command prompt or terminal based on the operating system you are using and type the following command to create controller using the Artisan CLI (Command Line Interface).
```bash
php artisan make:Controller UserController
```
app/Http/Controller/UserController.php



## Restful Resource Controllers
Often while making an application we need to perform CRUD (Create, Read, Update, Delete) operations. Laravel makes this job easy for us. Just create a controller and Laravel will automatically provide all the methods for the CRUD operations. You can also register a single route for all the methods in routes.php file.

```bash
php artisan make:controller MyController
```

