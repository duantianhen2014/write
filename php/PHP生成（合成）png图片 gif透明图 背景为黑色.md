## PHP生成（合成）png图片 gif透明图 背景为黑色

#### 问题1. 背景：使用PHP中GD库函数进行png图片生成，双击打开图片预览：背景为透明色，PhotoShop打开背景为黑色。

最近做头像上传用到剪切，只要GIF或者PNG是透明的话，剪切后都会变成黑色的背景图。

解决方案有2种：

**1.背景图填充白色的背景。**

Php代码  [![收藏代码](https://www.iteye.com/images/icon_star.png)](javascript:void())

1. $white = imagecolorallocate($dstim,255,255,255);  
2. imagefilledrectangle($dstim,0,0,$width,$height,$white);  
3. imagecolortransparent($dstim,$white);   

**2.设置图片走透明通道。** 

Php代码  [![收藏代码](https://www.iteye.com/images/icon_star.png)](javascript:void())

1. $img = imagecreatefrompng($src);  
2. imagesavealpha($img,true);//这里很重要;  
3. $thumb = imagecreatetruecolor(300,300);  
4. imagealphablending($thumb,false);//这里很重要,意思是不合并颜色,直接用$img图像颜色替换,包括透明色;  
5. imagesavealpha($thumb,true);//这里很重要,意思是不要丢了$thumb图像的透明色;  
6. imagecopyresampled($thumb,$img,0,0,0,0,300,300,300,300);  
7. imagepng($thumb,"temp.png");   

**以上2种方式均测试成功。**