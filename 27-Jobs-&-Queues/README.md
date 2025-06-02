

#  Laravel Jobs & Queues
Laravel’s Jobs and Queues system lets you defer time-consuming tasks (like sending emails, processing files, or API calls) so your app stays fast.


###  Why Use Jobs & Queues?
✅ Improves performance
✅ Handles heavy tasks in the background
✅ Prevents timeouts and lag for users


### Real Example
✍️ Action: User registers
🧵 Job: SendWelcomeEmail is queued and runs in the background


### 1. Create a Job
```bash
php artisan make:job SendWelcomeEmail

```
This creates:
```bash
app/Jobs/SendWelcomeEmail.php

```

### 2. Job Structure
```bash
class SendWelcomeEmail implements ShouldQueue
{
    use Dispatchable, InteractsWithQueue, Queueable, SerializesModels;

    public $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function handle()
    {
        Mail::to($this->user->email)->send(new WelcomeMail($this->user));
    }
}

```

###  3. Dispatch the Job
```bash
use App\Jobs\SendWelcomeEmail;

SendWelcomeEmail::dispatch($user);

```


###  4. Set Up the Queue System
Choose Driver in .env:

```bash
QUEUE_CONNECTION=database

```
**Then run:**
```bash
php artisan queue:table
php artisan migrate
```
This creates a jobs table to hold queued jobs.


### 5. Run the Queue Worker
```bash
php artisan queue:work
```

### 6. Delayed Jobs
```bash
SendWelcomeEmail::dispatch($user)->delay(now()->addMinutes(5));
```


### 7. Retry Failed Jobs
Failed jobs go into failed_jobs table (optional). You can retry them:
```bash
php artisan queue:retry all
```

### Summary
| Concept      | Description                                       |
| ------------ | ------------------------------------------------- |
| **Job**      | Code that runs in the background                  |
| **Queue**    | Holds jobs before they're processed               |
| **Dispatch** | Run job using `JobName::dispatch()`               |
| **Worker**   | Process jobs with `php artisan queue:work`        |
| **Driver**   | Choose how jobs are stored (database, redis, etc) |


