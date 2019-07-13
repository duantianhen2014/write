# PHP的全球唯一标示符：com_create_guid

com_create_guid。该函数需要**PHP支持com扩展支持或者修改**下获取GUID函数的实现以兼容各个PHP版本，在PHP不支持的情况下，[手册](<https://www.php.net/manual/zh/function.com-create-guid.php>)中出现了兼容代码：

function guid() {    

​    if (function_exists('com_create_guid')) {        

​        return com_create_guid();    

​    } else {     

​        mt_srand((double)microtime()*10000);

​        $charid = strtoupper(md5(uniqid(rand(), true))); 

​        $hyphen = chr(45);        

​        $uuid   = chr(123)            

​                 .substr($charid, 0, 8).$hyphen               

​                 .substr($charid, 8, 4).$hyphen            

​                 .substr($charid,12, 4).$hyphen            

​                 .substr($charid,16, 4).$hyphen            

​                 .substr($charid,20,12)            

​                 .chr(125);

​        return $uuid;    

​    }

}