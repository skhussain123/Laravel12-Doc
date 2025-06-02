
# Laravel Task Scheduling (Cron Jobs)
Laravel's Task Scheduling feature allows you to automate repetitive tasks like sending emails, clearing logs, backups, etc., using a clean, fluent syntax — without needing to write full cron entries for each task.


### Common Scheduling Methods
| Method                       | Description                  |
| ---------------------------- | ---------------------------- |
| `->everyMinute()`            | Run every minute             |
| `->hourly()`                 | Run every hour               |
| `->daily()`                  | Run once per day at midnight |
| `->weekly()`                 | Run once per week            |
| `->monthly()`                | Run once per month           |
| `->dailyAt('13:00')`         | Run daily at specific time   |
| `->timezone('Asia/Karachi')` | Set time zone                |

