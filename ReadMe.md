NewArkStudios Website
Written in Lararvel Framework

Debug Tools
-laravel
-laravel debugbar

Issues and Troubleshooting
- Make sure storage is writable by 

``` php
# Group Writable (Group, User Writable)
$ sudo chmod -R gu+w storage

# World-writable (Group, User, Other Writable)
$ sudo chmod -R guo+w storage
```
- Make sure bootstrap cache is writeable as well
chmod 777 bootstrap/cache

## Development Environment
Visual Studio Code with xdebug and xdebug extension
Lampp server change etc/http.conf to follow this https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug
pointing to installed xdebug on local machine

**Files Ignored are listed under .gitignore and .git/info/exclude**

## Database Configuration 
**Change .env file**
Note password and username listed in master docs
Migrate appropriate databases and install
```
php artisan migrate:install

php artisan migrate
```
To make new databases in laravel simply call

```
php artisan make:migration <migration_name> --create=<table_name>
```

**To clear data and reinstall databases **
```
php artisan migrate:refresh
```


To seed a database, in "DatabaseSeeder.php" add
```
    $this->call(<SeedName>::class);
```
Create the seed with 
```
    php artisan make:seeder <SeedName>
    // once complete and coded for seed with
    php artisan db:seed
```

Note if one cannot seed then we need to update our autload files
as they may not be synced

```
composer dump-autoload
```
Packages out of date? Run

```
composer update
composer install
```

**HTML Purifier package used** you will need to run
This package was used to prevent script injections but still allow HTML
links and images
```
chmod 777 -R vendor/ezyang/htmlpurifier/library/HTMLPurifier/DefinitionCache/Serializer
```

If run into errors delete migrations table and already existing tables

