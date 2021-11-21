## JavaScript Ajax上传文件

#### 1. FormData

```javascript
				var form = $('#upload-excel')[0];
        var formdata = new FormData(form);
        console.log('formdata', formdata);
        $.ajax({
            url: "{:url('importExcel')}",
            data: formdata,
            type: 'POST',
            processData: false,	// 不处理发送的数据，因为data值是Formdata对象，不需要对数据做处理
            async: false,
            cache: false,
            contentType: false, // 不设置Content-type请求头
            success: function (text) {
                console.log('text', text);
            },
            error: function () {
            }
        });
```



#### 2. AjaxUpload

```html
<script src="/static/js/ajaxupload.3.6.js"></script>
<script src="/static/js/mui.js"></script>
<link rel="stylesheet" href="/static/css/jquery.fileupload-ui.css"/>

<a class="mini-button" id="upload">上传</a>

<script type="text/javascript">
		new AjaxUpload('#upload', {
        action: "{:url('Upload/addImg')}",
        data : {
            'key1' : "This data won't",
            'key2' : "be send because",
            'key3' : "we will overwrite it"
        },
        name: 'file',
        onSubmit : function(file , ext){
            if (ext && /^(jpg|png|jpeg|gif)$/.test(ext)){
                this.setData({
                    'key': 'This string will be send with the file'
                });
            } else {
                alert('Error: only images are allowed');
                return false;
            }
        },
        onComplete : function(data,response){
            console.log(response)
            var json = $.parseJSON(response);
            if(json.error > 0){

            } else {
                
            }
        }
    });
</script>
```

