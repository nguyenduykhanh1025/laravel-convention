# Bad - Good Code Convention

## Controllers

Controllers phải đặt tên theo số nhiều.

```php
class PostsController
{
    // ...
}
```

Cố gắng giữ cho bộ điều khiển đơn giản và bám vào các từ khóa CRUD mặc định(index, create, store, show, edit, update, destroy).

Trong ví dụ sau, chúng ta có PostsController@favorite và PostsControlle@unfavorite, hoặc chúng ta có thể giải nén nó vào một FavoritePostsController riêng biệt.

```php
class PostsController
{
    public function create()
    {
        // ...
    }

    // ...

    public function favorite(Post $post)
    {
        request()->user()->favorites()->attach($post);

        return response(null, 200);
    }

    public function unfavorite(Post $post)
    {
        request()->user()->favorites()->detach($post);

        return response(null, 200);
    }
}
```

Ở đây chúng ta quay trở lại các từ CRUD mặc định, store và destroy.

```php
class FavoritePostsController
{
    public function store(Post $post)
    {
        request()->user()->favorites()->attach($post);

        return response(null, 200);
    }

    public function destroy(Post $post)
    {
        request()->user()->favorites()->detach($post);

        return response(null, 200);
    }
}
```

## Validation

Chuyển validation từ controllers đến Request classes (ở đây tôi để ở DTOs).

Bad:

```php
public function store(Request $request)
{
    $request->validate([
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
        'publish_at' => 'nullable|date',
    ]);
    ...
}
```

Good:

```php
public function store(PostRequest $request)
{
    ...
}
class PostRequest extends Request
{
    public function rules(): array
    {
        return [
            'title' => 'required|unique:posts|max:255',
            'body' => 'required',
            'publish_at' => 'nullable|date',
        ];
    }
}
```

## Business logic nên để ở service class

Controller chỉ nên đảm nhiệm trách nhiệm của nó, vì vậy nên các business logic từ controllers nên chuyển đến service classes.

Bad:

```php
public function store(Request $request)
{
    if ($request->hasFile('image')) {
        $request->file('image')->move(public_path('images') . 'temp');
    }

    ...
}
```

Good:

```php
public function store(Request $request)
{
    $this->articleService->handleUploadedImage($request->file('image'));
    ...
}
class ArticleService
{
    public function handleUploadedImage($image): void
    {
        if (!is_null($image)) {
            $image->move(public_path('images') . 'temp');
        }
    }
}
```

## Sử dụng config and language files, constants để thay thế cho text trong khi code

Bad:

```php
public function isNormal(): bool
{
    return $article->type === 'normal';
}
return back()->with('message', 'Your article has been added!');
```

Good:

```php
public function isNormal()
{
    return $article->type === Article::TYPE_NORMAL;
}
return back()->with('message', __('app.article_added'));
```

## Không lấy data từ .env file

Pass the data to config files instead and then use the `config()` helper function to use the data in an application.

Bad:

```php
$apiKey = env('API_KEY');
```

Good:

```php
// config/api.php
'key' => env('API_KEY'),
// Use the data
$apiKey = config('api.key');
```

## Typed properties

Bạn nên định nghĩa loại thuộc tính bất cứ khi nào có thể. Không sử dụng một docblock.

Bad:

```php
class Foo
{
  /** @var string */
  public $bar;
}
```

Good:

```php
class Foo
{
  public string $bar;
}
```

## String

Bad:

```php
$greeting = 'Hi, I am ' . $name . '.';
```

Good:

```php
$greeting = "Hi, I am {$name}.";
```

## If statements

Luôn sử dụng dấu ngoặc nhọn.

Bad:

```php
if ($condition) ...
```

Good:

```php
if ($condition) {
  ...
}
```

## Avoid else

Tránh sử dụng else bởi vì nó làm code khó đọc hơn. Trong hầu hết các trường hợp, nó có thể được cấu trúc lại bằng cách sử dụng trả về sớm.

Bad:

```php

if ($conditionA) {
   if ($conditionB) {
      // condition A and B passed
   }
   else {
     // conditionB A passed, B failed
   }
}
else {
   // conditionB A failed
}
```

Good:

```php
if (! $conditionBA) {
   // conditionB A failed

   return;
}

if (! $conditionB) {
   // conditionB A passed, B failed

   return;
}

// condition A and B passed
```
