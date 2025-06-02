

#  Laravel Custom Artisan Commands
Laravel allows you to create custom Artisan commands to automate tasks like sending emails, clearing caches, or generating reports.


## 1. Create a Custom Command
```bash
php artisan make:command MyCustomCommand
```
**✅ This will create a file at:**
```bash
app/Console/Commands/MyCustomCommand.php
```

### 2. Basic Command Structure
```bash
namespace App\Console\Commands;

use Illuminate\Console\Command;

class MyCustomCommand extends Command
{
    // Command signature (used in terminal)
    protected $signature = 'my:custom';

    // Command description
    protected $description = 'This is a custom command example';

    public function handle()
    {
        // Command logic
        $this->info('Custom command executed successfully!');
    }
}

```

### 3. Run the Command
```bash
php artisan my:custom
```