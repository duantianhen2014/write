# larave数据库操作

1. pluck 返回指定的字段值信息列表

   ```php
   Category::where('id', '6')->orWhere('parent_id', '6')->pluck('name')
   //返回的值如下
   //0 => "广告位置"
   //1 => "顶部位置"
   //2 => "中部位置"
   //3 => "底部位置"
   ```


