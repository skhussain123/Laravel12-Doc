



# File Upload


```bash
use App\Http\Controllers\FileController;

Route::post('/upload', [FileController::class, 'store']);

```


```bash
  public function store(Request $request)
    {
        $request->validate([
            'file' => 'required|mimes:pdf,xlsx,csv|max:2048',
        ]);

        $fileName = time() . '.' . $request->file->extension();
        $request->file->move(public_path('uploads'), $fileName);

        return back()->with('success', 'File uploaded successfully!')->with('file', $fileName);
    }

```
* validate(): Ensures the uploaded file is of type PDF, XLSX, or CSV and does not exceed 2MB.
* move(): Moves the uploaded file to the public/uploads directory.

```bash
<form action="/upload" method="POST" enctype="multipart/form-data">
    @csrf
    <input type="file" name="file" required>
    <button type="submit">Upload</button>
</form>
```

* enctype="multipart/form-data": Necessary for file uploads.
* @csrf: Protects against cross-site request forgery.