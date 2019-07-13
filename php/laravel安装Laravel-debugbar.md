# laravel安装Laravel-debugbar

1. composer安装

   ```php
   composer require "barryvdh/laravel-debugbar:~3.2" --dev
   ```

2. 生成配置文件，存放位置 `config/debugbar.php`

   ```php
   php artisan vendor:publish --provider="Barryvdh\Debugbar\ServiceProvider"
   ```

3. 打开 `config/debugbar.php`，将 `enabled` 的值设置为：

   ```php
   'enabled' => env('APP_DEBUG', false),
   ```

