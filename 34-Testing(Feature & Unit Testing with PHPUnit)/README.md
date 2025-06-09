

Laravel unit testing ko asan aur simple tareeqay se samjhtay hain. Testing ka matlab hota hai apnay code ko check karna ke sab kuch sahi kaam kar raha hai ya nahi — automatically.

Laravel mein Unit Testing use karne ka faida yeh hai ke aap apna kaam fast, error-free, aur professional bana sakte ho. Real-world project mein unit testing se bugs kam hoti hain, aur confidence milta hai ke code sahi kaam kar raha hai.

Unit Test ka matlab hai code ke chhote hisson (functions, classes, models) ko check karna. Ye chhoti chhoti cheezein test karta hai, jaise:

1. ek function sahi result de raha hai ya nahi
2. koi model ka data theek kaam kar raha hai ya nahi

###
| Step | Kaam                                    |
| ---- | --------------------------------------- |
| 1️⃣  | `php artisan make:test TestName --unit` |
| 2️⃣  | Test file me function banao             |
| 3️⃣  | `assertEquals()` se result check karo   |
| 4️⃣  | `php artisan test` se test run karo     |


 Haan, Laravel mein Unit Testing aur Feature Testing alag cheezein hain — dono ka maqsad testing hai, lekin level aur scope different hota hai.
 | 🔧 **Unit Testing**                                              | 🌐 **Feature Testing**                                       |
| ---------------------------------------------------------------- | ------------------------------------------------------------ |
| Code ke **chhote hisson** ko test karta hai (functions, classes) | Complete **user flow ya request-response** ko test karta hai |
| Sirf **ek function ya class** test hoti hai                      | **Multiple classes, routes, views, DB** sab test hote hain   |
| Fast hota hai (lightweight)                                      | Thoda slow hota hai (heavy process)                          |
| Database optional hota hai                                       | Zyada cases mein database zaroori hota hai                   |
| Mostly `--unit` flag se banta hai                                | Default test type hoti hai                                   |
| Example: `MathHelper::add()` function ko test karna              | Example: `/register` route pe form submit karke check karna  |


###  Kab Kya Use Karein?
| Situation                                          | Test Type                   |
| -------------------------------------------------- | --------------------------- |
| Function ka output test karna                      | ✅ Unit Test                 |
| Route, form, redirect, session, DB sab check karna | ✅ Feature Test              |
| Validation ya middleware ka test                   | ✅ Feature Test              |
| Email sending ka logic test (mock)                 | ✅ Unit or Feature (depends) |


### Laravel mein test kaise banate hain?
```bash
php artisan make:test UserTest --unit
```
**Is se ye file banegi:**
```bash
tests/Unit/UserTest.php
```
### ✅ Unit Test  1. Create the Helper Class
Man lo tumhare paas ek function hai jo price aur percentage se final price calculate karta hai
**app/Helpers/PriceHelper.php**

```bash
<?php

namespace App\Helpers;

class PriceHelper
{
    public static function calculateDiscount($price, $percentage)
    {
        return $price - ($price * $percentage / 100);
    }
}
```

### 2. Update Your Unit Test File
Update your PriceHelperTest.php to actually test that function:

```bash
namespace Tests\Unit;

use Tests\TestCase;
use App\Helpers\PriceHelper;

class PriceHelperTest extends TestCase
{
    public function test_discount_is_applied_correctly(): void
    {
        $this->assertEquals(800, PriceHelper::calculateDiscount(1000, 20));
    }

    public function test_zero_discount_returns_same_price(): void
    {
        $this->assertEquals(500, PriceHelper::calculateDiscount(500, 0));
    }
}
```

### 3. Run the Tests
```bash
php artisan test
```
**Or directly with PHPUnit:**
```bash
vendor/bin/phpunit tests/Unit/PriceHelperTest.php
```


## feature test
### Step 1: Make Sure Route Exists
Open your routes/web.php and check:


```bash
php artisan make:test IndexRouteTest
```
**This will create a file:**
```bash
tests/Feature/IndexRouteTest.php
```

### Step 2: Write the Test Code
Open that file and replace its content with:
```bash
<?php


namespace Tests\Feature;

use Illuminate\Foundation\Testing\RefreshDatabase;
use Illuminate\Foundation\Testing\WithFaker;
use Tests\TestCase;

class IndexRouteTest extends TestCase
{
    /**
     * A basic feature test example.
     */
    public function test_example(): void
    {
        $response = $this->get('/about'); /// agr ap yaha koe esa route likhty jo ha nhi ya us route me koe error hoga to feature testing me pakara jayega error ///
         

        $response->assertStatus(200);
    }
}

```

### 3. Wep.php
```bash
Route::get('/', function () {
    return view('welcome');
});

Route::get('about',[HomeController::class, 'about'])->name('about');
```


### Useful Helper Methods
```bash
$this->get('/');            // Simulate a GET request
$this->post('/login');      // Simulate a POST request
$this->actingAs($user);     // Simulate a logged-in user
$this->assertStatus(200);   // Assert response status
$this->assertSee('text');   // Assert content on page

```

### 1. Laravel Application Boot karta hai
**TestCase Laravel ka base test class hai jo:**
* Ye app ka environment load karta hai (.env.testing use hota hai).
* application instance create karta hai so that you can test routes, DB, etc.

