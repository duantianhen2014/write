# 图片Orientation属性

```php
<?php
$str = "http://file.api.weixin.qq.com/cgi-bin/media/get?access_token=".$access_token."&media_id=".$media_id;
$image = imagecreatefromstring(file_get_contents($str));
//此函数可传入url地址
$exif = exif_read_data($str);

if(!empty($exif['Orientation'])) {
 switch($exif['Orientation']) {
 case 8:
  $image = imagerotate($image,90,0);
  break;
 case 3:
  $image = imagerotate($image,180,0);
  break;
 case 6:
  $image = imagerotate($image,-90,0);
  break;
 }
}
```



PS: 阿里云OSS图片Orientation

1.   获取 图片 ImageInfoByFile  信息， 判断如果  orient  如果  1,2,3,4 均不需要转，5,6,7,8 为90度或-90度
     ​    url  拼接   ?imageMogr2/auto-orient
2.   如果 是遇到用户上传 gif  
图片地址拼接  ?x-oss-process=image/resize,w_750/auto-orient,1/format,jpg

![](D:\write\php\images\orientation.png)