# 🪄 Laravel Admin (Ladmin v2)

[![Latest Stable Version](https://poser.pugx.org/hexters/ladmin/v/stable)](https://packagist.org/packages/hexters/ladmin)
[![Total Downloads](https://poser.pugx.org/hexters/ladmin/downloads)](https://packagist.org/packages/hexters/ladmin)
[![License](https://poser.pugx.org/hexters/ladmin/license)](https://packagist.org/packages/hexters/ladmin)

The magic of creating an Administrator page.

![Dashboard](https://github.com/hexters/assets/blob/main/ladmin/v2/captures/dashboard.png?raw=true)

# 🏷️ Laravel Version

|Version|Laravel|
|:-:|:-:|
| [v1.0.x](https://github.com/hexters/ladmin/blob/v1.0.3/readme.md) | 7.x |
| [v1.8.*](https://github.com/hexters/ladmin/blob/v1.8.3/readme.md)| 8.x |
|v2.0.*|9.x|

Schema for apps that have a login page for members. You can use [laravel/breeze](https://github.com/laravel/breeze), [larave/ui](https://github.com/laravel/ui), [laravel jetstream](https://jetstream.laravel.com/1.x/introduction.html), etc.

![Scheme Member](https://github.com/hexters/assets/blob/main/ladmin/v2/captures/scheme.png?raw=true)
# ℹ️ What's New ?

Now **Ladmin** comes with the concept of **HMVC** (Hierarchical Model View Controller) . [Click here for more details.](https://github.com/hexters/ladmin/wiki/Module)

```bash
$ php artisan module:make-menu PostMenu --module=Blog
```

# 🚀 Quickstart

Follow the steps below to get started faster! Add the repository by running the command below.

```bash
$ composer require hexters/ladmin
```

Follow the installation with the `--with-admin-table` option.
```
$ php artisan ladmin:install --with-admin-table
```

Run migrate and seed, to install ladmin database tables
```bash
$ php artisan migrate --seed
```

And run seeder ladmin module, to assign role and permission to existing user.
```bash
$ php artisan module:seed Ladmin
```

Installation is complete, please access `http://localhost:8000/administrator`

![Login Page](https://github.com/hexters/assets/blob/main/ladmin/v2/captures/login-page.png?raw=true)

# 🧰 Manual Installation

If you want to use the `App\Models\User` model class as a login account, then follow the steps below.

Use `\Hexters\Ladmin\LadminAccount` into model `\App\Modules\User` see the example.
```php
. . .
use Hexters\Ladmin\LadminAccount;

class User extends Authenticatable {

  use HasApiTokens, HasFactory, Notifiable, LadminAccount;

  . . .
```

Open file `\Database\Seeders\DatabaseSeeder`, add the code below or you can create your own seeder file.
```php

\App\Models\User::factory(10)->create();

```

Follow the installation below.

```
$ php artisan ladmin:install
```

Run migrate and seed, to install ladmin database tables
```bash
$ php artisan migrate --seed
```

And run seeder ladmin module, to assign role and permission to existing user.
```bash
$ php artisan module:seed Ladmin
```

And please access `http://localhost:8000/administrator`


# 🗂️ Custom Namespaces

To call `view`, `language`, `config`, and `component` file, you need to add the prefix of module's name eg `blog`, see example below.

Calling View:
```php
  view('blog::article.index');
```

Calling Lang:
```php
  __('blog::error.auth.message');

  trans('blog::error.auth.message');

  Lang::get('blog::error.auth.message');
```

Calling Config:
```php
  config('blog.name')
```

For component view, if you have component named `\Modules\Blog\View\Components\Input` class, then the way to call it by running.
```html
  <x-blog-input />
```

# 🌇 Layout Templating

### Guest Layout
```html
<x-ladmin-guest-layout>
  
  <x-slot name="metaTitle">Meta Page Title</x-slot>

  @push('before-style')
    <!-- ... -->
  @endpush
  <x-slot name="styles">
    <!-- <link href="custom.css" rel="stylesheet" /> -->
  </x-slot>
  @push('after-style')
    <!-- ... -->
  @endpush

  <!-- Content here -->

  @push('before-script')
    <!-- ... -->
  @endpush
  <x-slot name="scripts">
    <!-- <script src="custom.js" ></script> -->
  </x-slot>
  @push('after-script')
    <!-- ... -->
  @endpush

</x-ladmin-guest-layout>
```

## Auth Layout

```html
<x-ladmin-auth-layout>

  <x-slot name="title">Page Title</x-slot>

  <!-- Follow guest layout for slots & stacks -->
  
</x-ladmin-auth-layout>
```

# 📖 Documentation
View complete [documentation here](https://github.com/hexters/ladmin/wiki)
