# Laravel - Request
In Laravel, Request is used to get data from the user — like form inputs, query parameters, or JSON payloads — when the user makes a request to your application (like submitting a form or clicking a link).

## What is Request in Laravel?
Laravel uses the Illuminate\Http\Request class to handle HTTP requests. You use it to access input data, files, headers, etc.

### How to Use Request in a Controller:
```bash
use Illuminate\Http\Request;

class PostController extends Controller
{
    public function store(Request $request)
    {
        $title = $request->input('title');
        return 'The title is: ' . $title;
    }
}
```

##  Common Request Methods:
| Method                       | Description                           |
| ---------------------------- | ------------------------------------- |
| `$request->input('key')`     | Get input from any request (GET/POST) |
| `$request->all()`            | Get all input fields as array         |
| `$request->only([...])`      | Get only specific inputs              |
| `$request->except([...])`    | Get all except specific inputs        |
| `$request->has('key')`       | Check if input exists                 |
| `$request->file('file')`     | Get uploaded file                     |
| `$request->method()`         | Get request method (GET, POST, etc.)  |
| `$request->isMethod('post')` | Check method type                     |


## Example with Form Data:
```bash 
public function submit(Request $request) {
    $name = $request->input('name');
    $email = $request->input('email');

    return "Name: $name, Email: $email";
}
```

## JSON Request Example (e.g., from APIs):
```bash
public function apiData(Request $request) {
    $data = $request->json()->all();
    return response()->json($data);
}
```

##  Validation with Request:
```bash
public function store(Request $request) {
    $request->validate([
        'name' => 'required',
        'email' => 'required|email',
    ]);
}
```


