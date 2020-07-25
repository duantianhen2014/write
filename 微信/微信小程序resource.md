## 微信小程序

#### 单包

 node wuWxapkg.js /a/c/c/d.wxapkg

#### 多包

./bingo.sh testpkg/master.wxapkg 
./bingo.sh testpkg/_1123949441_355.wxapkg -s=../master
./bingo.sh testpkg/_-1403820346_29.wxapkg -s=../master
./bingo.sh testpkg/_-1793266136_29.wxapkg -s=../master
./bingo.sh testpkg/_2029521889_29.wxapkg -s=../master
./bingo.sh testpkg/_-562677449_29.wxapkg -s=../master
./bingo.sh testpkg/_-819050195_29.wxapkg -s=../master

#### 单独解包

子包js：

​	node wuJs.js D:/node-project/yg_new/_1206133534_44/pkg_payment/app-service.js

子包wxss：

子包wxml：

​	node wuWxml.js D:/node-project/yg_new/_1206133534_44/pkg_payment/app-service.js

子包json：

​	node wuJs.js D:/node-project/yg_new/_-513890145_44/pkg_custom/page-frame.js