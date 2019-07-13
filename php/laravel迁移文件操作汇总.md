# laravel迁移文件操作汇总

1. 创建迁移文件

   * **php artisan make:migration create_users_table**（不指定表名）
   * **php artisan make:migration create_users_table --create=users**（指定表名）

2. 更新迁移文件（在已把迁移文件入库后）

   再次创建修改类型的迁移文件（原有新建文件不动），指向已经存在的表

   **php artisan make:migration update_votes_to_users_table --table=user**

   （注意：要在此迁移文件中的down操作及进行up操作的反处理）

   eg: 

   ```php
   $table->engine = 'InnoDB';
   $table->dropColumn('votes'); //删除表的字段
   $table->dropColumn('votes', 'avatar', 'location'); //删除多个字段
   $table->renameColumn('from', 'to');//修改表的字段
   ```

3. 进行php artisan migrate进行入库操作

   PS：php artisan migrate:rollback操作默认进行step=1的回滚

   php artisan migrate:reset重置、还原