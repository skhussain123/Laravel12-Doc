

# Laravel Dependency Injection (DI)
Dependency Injection is a design pattern where Laravel automatically provides the required class dependencies to your classes or methods, instead of you creating them manually.

### Why Use Dependency Injection?

* Makes your code cleaner and easier to test.
* Decouples class dependencies.
* Improves maintainability and flexibility.

### How Does Laravel Do It?
Laravel uses the Service Container to automatically resolve and inject dependencies.

### Example 1: Constructor Injection
```bash
namespace App\Http\Controllers;

use App\Services\PaymentGateway;

class PaymentController extends Controller
{
    protected $payment;

    public function __construct(PaymentGateway $payment)
    {
        $this->payment = $payment;  // Injected automatically by Laravel
    }

    public function process()
    {
        $this->payment->pay();
    }
}

```
When you create PaymentController, Laravel automatically injects an instance of PaymentGateway.


### Example 2: Method Injection
You can inject dependencies directly in controller methods:

```bash
use Illuminate\Http\Request;

public function store(Request $request, PaymentGateway $payment)
{
    $payment->pay();
}

```

### Binding Interfaces to Implementations
In AppServiceProvider (or any service provider), bind interfaces:

```bash
public function register()
{
    $this->app->bind(
        'App\Contracts\PaymentGatewayInterface',
        'App\Services\StripePaymentGateway'
    );
}
```
Now Laravel injects StripePaymentGateway wherever PaymentGatewayInterface is required.

### Summary
| Concept               | Explanation                             |
| --------------------- | --------------------------------------- |
| Dependency Injection  | Laravel auto-injects class dependencies |
| Service Container     | Resolves and manages class dependencies |
| Constructor Injection | Inject in constructor                   |
| Method Injection      | Inject in methods                       |
| Interface Binding     | Bind interfaces to implementations      |


