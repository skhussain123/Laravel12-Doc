

# What is Localization in Laravel?
Localization in Laravel means adapting your application to support multiple languages, so users can view content in their own preferred language.


## Why Use Localization?
To build apps for global users — e.g., English, Urdu, Arabic, French — and switch the language dynamically based on the user’s preference or location.

### 1. Where are Language Files Stored?
Language files are stored in:

```bash
/resources/lang/{locale}/

```

**Example:**
```bash
resources/lang/en/messages.php
resources/lang/ur/messages.php

```

###  2. Language File Example

resources/lang/en/messages.php

```bash
return [
    'welcome' => 'Welcome to our website',
    'login' => 'Login',
];

```
resources/lang/ur/messages.php
```bash
return [
    'welcome' => 'ہماری ویب سائٹ پر خوش آمدید',
    'login' => 'لاگ ان کریں',
];

```

### 3. Using Translations in Blade
```bash
{{ __('messages.welcome') }}

```
**It will show:**:

* English: Welcome to our website
* Urdu: ہماری ویب سائٹ پر خوش آمدید

### 4. Setting the App Locale
Set default language in config/app.php:
```bash
'locale' => 'en',
```
**To change it at runtime:**


### 5. Switch Language Button (Example)
```bash
<a href="{{ url('lang/en') }}">English</a>
<a href="{{ url('lang/ur') }}">اردو</a>

```
In web.php

```bash
Route::get('lang/{locale}', function ($locale) {
    session(['locale' => $locale]);
    App::setLocale($locale);
    return redirect()->back();
});

```
In Middleware (optional):
```bash
if (session()->has('locale')) {
    App::setLocale(session('locale'));
}
```

### Summary
| Feature            | Description                                 |
| ------------------ | ------------------------------------------- |
| **Localization**   | Supporting multiple languages               |
| **Language Files** | Stored in `resources/lang/{locale}/`        |
| **Usage**          | `__('file.key')` to display translated text |
| **Switching**      | Set via session, URL, or user settings      |


