


# What is Authentication and Authorization?
In Laravel (and all web applications), authentication and authorization are key concepts for security.

### 1. Authentication = "Who are you?"
Authentication is the process of verifying the user's identity (i.e., login, register, etc.).

**✅ Purpose:**
Checks if the user is logged in.
Handles login, registration, logout, password resets.

```bash
if (Auth::check()) {
    // The user is authenticated
}

```

### Laravel Provides:

* Auth::login($user)
* Auth::check() – is user logged in?
* Auth::user() – get the logged-in user


### 2. Authorization = "What are you allowed to do?"
Authorization is the process of determining user permissions — what they are allowed to access or modify after login.

**✅ Purpose:**

* Checks if the user has access to a resource or action.
* Uses Gates or Policies.

**Laravel Provides:**

* Gate::define() – for custom logic
* Policies – linked to models for granular control

```bash
if (Auth::user()->can('delete-post', $post)) {
    // Allow delete
}
```

### 🧾 Summary Table

| Feature          | Authentication                | Authorization                       |
| ---------------- | ----------------------------- | ----------------------------------- |
| **Question**     | Who are you?                  | What can you do?                    |
| **Purpose**      | Verify user identity          | Control access to actions/resources |
| **Comes First?** | ✅ Yes                         | ❌ Only after authentication         |
| **Handled By**   | Laravel Breeze, UI, Jetstream | Gates and Policies                  |
| **Examples**     | Login, Register, Logout       | Can update post? Can delete user?   |


