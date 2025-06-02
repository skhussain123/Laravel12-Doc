

# Laravel Events & Listeners
Laravel’s Events & Listeners system lets you decouple logic by separating actions into events and their handlers (listeners).

### Why Use Events?

* Keep your code clean and organized.
* Run extra logic after something happens (e.g. user registered, order placed).
* Makes your app more flexible and scalable.


### Real-World Example:
📝 Event: UserRegistered
🔔 Listener: SendWelcomeEmail


###  1. Create an Event & Listener
```bash
php artisan make:event UserRegistered
php artisan make:listener SendWelcomeEmail --event=UserRegistered

```


###  2. Event Structure (UserRegistered.php)
```bash
class UserRegistered
{
    use Dispatchable, InteractsWithSockets, SerializesModels;

    public $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }
}

```


### 3. Listener Structure (SendWelcomeEmail.php)
```bash
class SendWelcomeEmail
{
    public function handle(UserRegistered $event)
    {
        Mail::to($event->user->email)->send(new WelcomeMail($event->user));
    }
}

```

### 4. Register in EventServiceProvider
app/Providers/EventServiceProvider.php

```bash
protected $listen = [
    UserRegistered::class => [
        SendWelcomeEmail::class,
    ],
];

```


### 5. Fire the Event
You can dispatch the event like this:

```bash
event(new UserRegistered($user));
```
This triggers the SendWelcomeEmail listener automatically.


### Summary Table
| Concept      | Description                                    |
| ------------ | ---------------------------------------------- |
| **Event**    | Something that *happens* (e.g. UserRegistered) |
| **Listener** | Reacts to an event (e.g. Send welcome email)   |
| **Register** | In `EventServiceProvider`                      |
| **Dispatch** | `event(new EventName(...))`                    |


