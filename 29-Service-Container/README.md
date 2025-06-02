
# Laravel Service Container
The Service Container (also called the IoC Container) is a powerful tool in Laravel that manages class dependencies and performs dependency injection automatically.

## What Does the Service Container Do?

* Resolves and instantiates classes.
* Injects dependencies automatically.
* Manages bindings between interfaces and implementations.
* Helps decouple code for easier testing and maintenance.

### How It Works?

When you type-hint a class or interface in a constructor or method, Laravel’s service container "resolves" it:
* Finds what that class needs.
* Automatically creates instances of those dependencies.
8 Passes everything together.

### Common Usage
**Binding a Class or Interface**
In a Service Provider (usually AppServiceProvider):
```bash
public function register()
{
    $this->app->bind('App\Contracts\PaymentGateway', 'App\Services\StripePaymentGateway');
}
```
This tells Laravel:
When someone asks for PaymentGateway, give them an instance of StripePaymentGateway.


### Resolving a Class Manually
```bash
$payment = app()->make('App\Contracts\PaymentGateway');
$payment->pay();
```
**Or shortcut:**
```bash
$payment = resolve('App\Contracts\PaymentGateway');
```

### Automatic Injection Example
```bash
class OrderController extends Controller
{
    protected $payment;

    public function __construct(\App\Contracts\PaymentGateway $payment)
    {
        $this->payment = $payment;  // Service Container injects this automatically
    }
}
```

###  Key Methods of the Service Container
| Method        | Description                                                             |
| ------------- | ----------------------------------------------------------------------- |
| `bind()`      | Register a class or interface binding                                   |
| `singleton()` | Register a class to always return the same instance (singleton pattern) |
| `make()`      | Resolve a class manually                                                |
| `instance()`  | Register an existing instance                                           |


### Singleton Example
```bash
$this->app->singleton('Logger', function ($app) {
    return new Logger();
});

```

### Summary
| Concept              | What it Means                           |
| -------------------- | --------------------------------------- |
| Service Container    | Laravel's powerful dependency resolver  |
| Binding              | Tell Laravel what to inject             |
| Resolving            | Get an instance from the container      |
| Singleton            | Same instance every time                |
| Dependency Injection | Automatic injection using the container |

