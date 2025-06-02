
# Laravel Repository Pattern
The Repository Pattern is a design pattern that abstracts data access logic and separates it from business logic. It helps make your code cleaner, more maintainable, and easier to test.


### Why Use the Repository Pattern?

* Decouples database queries from controllers/services.
* Makes it easier to switch data sources (e.g., Eloquent, API, cache).
* Helps with unit testing by mocking repositories.
* Keeps code organized and reusable.


###  Basic Structure

* Repository Interface: Defines methods (contract).
* Repository Implementation: Contains data access logic.
* Controller/Service: Uses the repository via the interface.

### Step 1: Create Repository Interface
app/Repositories/UserRepositoryInterface.php

```bash
namespace App\Repositories;

interface UserRepositoryInterface
{
    public function all();
    public function find($id);
    public function create(array $data);
    public function update($id, array $data);
    public function delete($id);
}

```

### Step 2: Create Repository Implementation
app/Repositories/UserRepository.php

```bash
namespace App\Repositories;

use App\Models\User;

class UserRepository implements UserRepositoryInterface
{
    public function all()
    {
        return User::all();
    }

    public function find($id)
    {
        return User::find($id);
    }

    public function create(array $data)
    {
        return User::create($data);
    }

    public function update($id, array $data)
    {
        $user = User::find($id);
        if ($user) {
            $user->update($data);
            return $user;
        }
        return null;
    }

    public function delete($id)
    {
        return User::destroy($id);
    }
}
```

### Step 3: Bind Interface to Implementation
In AppServiceProvider.php:

```bash
public function register()
{
    $this->app->bind(
        \App\Repositories\UserRepositoryInterface::class,
        \App\Repositories\UserRepository::class
    );
}
```

### Step 4: Use Repository in Controller
```bash
use App\Repositories\UserRepositoryInterface;

class UserController extends Controller
{
    protected $users;

    public function __construct(UserRepositoryInterface $users)
    {
        $this->users = $users;
    }

    public function index()
    {
        $allUsers = $this->users->all();
        return view('users.index', compact('allUsers'));
    }
}

```

### Benefits
| Benefit                | Explanation                                     |
| ---------------------- | ----------------------------------------------- |
| Separation of concerns | Keeps data access logic separate                |
| Easier testing         | Mock repository for unit tests                  |
| Flexibility            | Switch data source without changing controllers |
| Cleaner code           | Controller logic is simplified                  |


