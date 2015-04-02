#Panel: Roles and Permissions

This repo is just a simple example to use [Entrust](https://github.com/Zizaco/entrust) with a custom panel to edit roles and permissions or you can simply assign permissions to a role without that panel.

#Features
  - Create/Update/Delete Roles, Permissions and Users with REST resources
  - Entrust [migration](database/migrations/2015_03_30_121557_entrust_setup_tables.php#L20) contains a new column named level, it's used to display the checkboxes roles that belongsTo a user roles (see [User.php](app/User.php#L46), used in [RolesPermissionsController.php](app/Http/Controllers/RolesPermissionsController.php#L54) and [RoleLowerOrEqualToCurrentUser.php](app/Repositories/Criteria/Role/RoleLowerOrEqualToCurrentUser.php#L22))
  - [AuthorizeMiddleware](app/Http/Middleware/AuthorizeMiddleware.php) check the permissions based on route and current user. (This is to improve to check create_MODEL, update_MODEL, show_MODEL, delete_MODEL).
  - In the [view](resources/views/roles_permissions/index.blade.php#L27) I check if permission [hasRole](app/Models/Permission.php#L17) to verify if relationships exists in permission_role table


#Screenshots
###Logged as Admin
![Admin panel](https://github.com/Rtransat/laravel-entrust-role-permission-panel/raw/master/public/img/panel-admin.jpg)

###Logged as Editor
![Editor panel](https://github.com/Rtransat/laravel-entrust-role-permission-panel/raw/master/public/img/panel-editor.jpg)

#I use

* [Laravel 5](https://github.com/laravel/laravel) of course :)
* [Entrust](https://github.com/Zizaco/entrust)
* [Repositories](https://github.com/Bosnadev/Repositories)
* [html](https://github.com/LaravelCollective/html)

#Installation

```sh
$ git clone https://github.com/Rtransat/laravel-entrust-role-permission-panel && cd laravel-entrust-role-permission-panel
$ composer update
```

**Config your .env file in root project (laravel-entrust-role-permission-panel/.env)**

```
DB_HOST=localhost
DB_DATABASE=database
DB_USERNAME=username
DB_PASSWORD=password
```

```sh
$ php artisan migrate:install
$ php artisan migrate
$ php artisan db:seed
$ php artisan serve
```

#Account

    admin@admin.com / admin
    editor@editor.com / editor
    user@user.com / user

#Todo list

  - Improve [AuthorizeMiddleware](app/Http/Middleware/AuthorizeMiddleware.php)
  - Refactor

#You want improve this repo ?

Feel free to send your pull request