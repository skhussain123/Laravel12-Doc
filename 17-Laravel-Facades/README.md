


# Laravel - Facades
In Laravel, facades provide a static interface to classes that are available in the application's service container. They serve as "static proxies" to underlying classes, offering a simple and expressive syntax while maintaining more testability and flexibility than traditional static methods.

```bash
use Illuminate\Support\Facades\Cache;

Cache::put('key', 'value', 60);

```

## How Do Facades Work?
Facades in Laravel extend the base Illuminate\Support\Facades\Facade class. The core of their functionality lies in the getFacadeAccessor method, which returns the service container binding for the underlying class.

```bash
namespace Illuminate\Support\Facades;

class Cache extends Facade
{
    protected static function getFacadeAccessor()
    {
        return 'cache';
    }
}

```

### Common Built-in Facades
Laravel provides a variety of built-in facades for common tasks:

* Cache: Interact with the caching system.
* DB: Access the database query builder.
* Log: Write log messages.
* Auth: Handle authentication.
* Route: Define application routes.


## Creating Custom Facades
You can create your own custom facades to simplify access to services in your application. Here's how:

**Step 1: Create a Service Class**
First, create a service class that provides the functionality you want to expose via a facade.
```bash
namespace App\Services;

class PaymentService
{
    public function process($order)
    {
        // Process the payment for the given order
        return "Processed order #$order successfully!";
    }
}

```

**Step 2: Register the Service in a Service Provider**
Next, bind the service class to the service container in a service provider.
```bash
namespace App\Providers;

use Illuminate\Support\ServiceProvider;
use App\Services\PaymentService;

class AppServiceProvider extends ServiceProvider
{
    public function register()
    {
        $this->app->singleton(PaymentService::class, function ($app) {
            return new PaymentService();
        });
    }
}

```

**Step 3: Create the Facade**
Now, create a facade that provides a static interface to the service.
```bash
namespace App\Facades;

use Illuminate\Support\Facades\Facade;

class Payment extends Facade
{
    protected static function getFacadeAccessor()
    {
        return \App\Services\PaymentService::class;
    }
}
```

**Step 4: Register the Facade Alias**
Finally, register the facade alias in the config/app.php file.
```bash
'aliases' => [
    // Other aliases...
    'Payment' => App\Facades\Payment::class,
],
```

**Now, you can use the facade to access the service.**
```bash
use Payment;

echo Payment::process(123);

```

**Real-Time Facades**
Laravel also supports real-time facades, allowing you to treat any class in your application as if it were a facade without creating a formal facade class.
```bash
use Facades\App\Services\PaymentService;

echo PaymentService::process(123);

```