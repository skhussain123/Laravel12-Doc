

# Laravel - Overview

Laravel is a powerful MVC PHP framework, designed for developers who need a simple and elegant toolkit to create full-featured web applications. Laravel was created by Taylor Otwell. This is a brief tutorial that explains the basics of Laravel framework.

Laravel is an open-source PHP framework, which is robust and easy to understand. It follows a model-view-controller design pattern. Laravel reuses the existing components of different frameworks which helps in creating a web application. The web application thus designed is more structured and pragmatic.

Laravel offers a rich set of functionalities which incorporates the basic features of PHP frameworks like CodeIgniter, Yii and other programming languages like Ruby on Rails. Laravel has a very rich set of features which will boost the speed of web development.

If you are familiar with Core PHP and Advanced PHP, Laravel will make your task easier. It saves a lot time if you are planning to develop a website from scratch. Moreover, a website built in Laravel is secure and prevents several web attacks.


* Laravel was created by Taylor Otwell. 
* The framework was first released in June 2011. 

 
**Install and create laravel project** 

* Composer global require laravel/installer 
* Laravel new example-app 




### Advantages of Laravel
Laravel offers you the following advantages, when you are designing a web application based on it −

* The web application becomes more scalable, owing to the Laravel framework.
* Considerable time is saved in designing the web application, since Laravel reuses the components from other framework in developing web application.
* It includes namespaces and interfaces, thus helps to organize and manage resources.


### Composer
Composer is a tool which includes all the dependencies and libraries. It allows a user to create a project with respect to the mentioned framework (for example, those used in Laravel installation). Third party libraries can be installed easily with help of composer.

All the dependencies are noted in composer.json file which is placed in the source folder.


## **Features of Laravel**
Laravel offers the following key features which makes it an ideal choice for designing web applications −


### **Modularity**
Laravel provides 20 built in libraries and modules which helps in enhancement of the application. Every module is integrated with Composer dependency manager which eases updates.

### **Testability**
Laravel includes features and helpers which helps in testing through various test cases. This feature helps in maintaining the code as per the requirements.

### **Routing**
Laravel provides a flexible approach to the user to define routes in the web application. Routing helps to scale the application in a better way and increases its performance.

### **Configuration Management**
A web application designed in Laravel will be running on different environments, which means that there will be a constant change in its configuration. Laravel provides a consistent approach to handle the configuration in an efficient way.


### **Schema Builder**
Schema Builder maintains the database definitions and schema in PHP code. It also maintains a track of changes with respect to database migrations.

### **Template Engine**
Laravel uses the Blade Template engine, a lightweight template language used to design hierarchical blocks and layouts with predefined blocks that include dynamic content.


### **Authentication**
User authentication is a common feature in web applications. Laravel eases designing authentication as it includes features such as register, forgot password and send password reminders.

### **Redis**
Laravel uses Redis to connect to an existing session and general-purpose cache. Redis interacts with session directly.

### **Queues**
Laravel includes queue services like emailing large number of users or a specified Cron job. These queues help in completing tasks in an easier manner without waiting for the previous task to be completed.


## **Laravel MVC Architecture Explained**
Model – View – Controller
This pattern separates your application logic into three layers to make code clean, scalable, and manageable.


### **1. Model (app/Models/)**

* Role: Handles all data logic and interaction with the database.
* Represents a table in the database.
* Each model corresponds to one table.
* You use Eloquent ORM in Laravel to query data easily.

```bash
namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Product extends Model
{
    protected $fillable = ['name', 'price'];
}
```

### **2. View (resources/views/)**

* Role: Responsible for the UI (User Interface) — what the user sees.
* Uses Blade templating engine (.blade.php).
* Displays dynamic content passed by the controller.

```bash
<!-- resources/views/products/index.blade.php -->
<h1>All Products</h1>
@foreach ($products as $product)
    <p>{{ $product->name }} - ${{ $product->price }}</p>
@endforeach

```


### **3. Controller (app/Http/Controllers/)**
* Role: Acts as a bridge between Model and View.
* Receives requests
* Fetches data using models
* Passes data to views

```bash
namespace App\Http\Controllers;

use App\Models\Product;
use Illuminate\Http\Request;

class ProductController extends Controller
{
    public function index()
    {
        $products = Product::all(); // Fetch data from Model
        return view('products.index', compact('products')); // Pass to View
    }
}
```

## Environment Configuration
Environment variables are those which provide a list of web services to your web application. All the environment variables are declared in the .env file which includes the parameters required for initializing the configuration.

By default, the .env file includes following parameters −

