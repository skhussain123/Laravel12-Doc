

#  Laravel Testing (Feature & Unit Testing with PHPUnit)
Laravel integrates PHPUnit for testing, helping you write unit tests and feature tests to ensure your app works as expected.


## Types of Tests
| Test Type    | Purpose                                          | Example                                   |
| ------------ | ------------------------------------------------ | ----------------------------------------- |
| Unit Test    | Test small, isolated pieces (functions, classes) | Testing a helper function or model method |
| Feature Test | Test HTTP requests, full workflows, user actions | Testing form submission or API endpoints  |



###  Creating Tests
Run these commands to create test files:
**Unit test:**
```bash
php artisan make:test ExampleTest --unit
```
**Feature test:**
```bash
php artisan make:test UserRegistrationTest
```

### Unit Test Example
File: tests/Unit/ExampleTest.php

```bash
namespace Tests\Unit;

use Tests\TestCase;

class ExampleTest extends TestCase
{
    public function test_sum()
    {
        $this->assertEquals(4, 2 + 2);
    }
}

```
**Run tests:**
```bash
php artisan test
```

## Feature Test Example
File: tests/Feature/UserRegistrationTest.php

```bash
namespace Tests\Feature;

use Tests\TestCase;
use Illuminate\Foundation\Testing\RefreshDatabase;

class UserRegistrationTest extends TestCase
{
    use RefreshDatabase;

    public function test_user_can_register()
    {
        $response = $this->post('/register', [
            'name' => 'John Doe',
            'email' => 'john@example.com',
            'password' => 'password',
            'password_confirmation' => 'password',
        ]);

        $response->assertStatus(302); // Redirect after registration
        $this->assertDatabaseHas('users', ['email' => 'john@example.com']);
    }
}

```

### Useful Testing Methods
| Method                          | Description                   |
| ------------------------------- | ----------------------------- |
| `$this->assertEquals()`         | Check if two values are equal |
| `$this->assertTrue()`           | Check if value is true        |
| `$this->assertDatabaseHas()`    | Check if DB contains data     |
| `$this->post()`, `$this->get()` | Simulate HTTP requests        |
| `$response->assertStatus()`     | Check HTTP response status    |
| `$response->assertJson()`       | Check JSON response content   |


### Refreshing Database
Use trait RefreshDatabase in feature tests to rollback DB after each test:

```bash
use Illuminate\Foundation\Testing\RefreshDatabase;

class MyTest extends TestCase
{
    use RefreshDatabase;
}

```

### Summary
| Concept          | Description                                |
| ---------------- | ------------------------------------------ |
| Unit Testing     | Test isolated functions or classes         |
| Feature Testing  | Test user flows, HTTP requests             |
| PHPUnit          | Testing framework used by Laravel          |
| Artisan Commands | `php artisan make:test` to generate tests  |
| Running Tests    | `php artisan test` or `vendor/bin/phpunit` |




