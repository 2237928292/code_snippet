# vue 相关的代码片段 #

#### 赋值 #####

> 给某对象赋值时 ， 例如 obj 直接使用 . 赋值后不可更改 需使用 $set

```
this.$set(obj,'key',value)
```

#### vue上传文件 #####

> vue使用Element组件上传 图片 视频 文档 等，并且转为Base64编码

``` 
<el-upload class="upload-demo" drag action="https://jsonplaceholder.typicode.com/posts/" :before-upload="BeforeUpload" multiple>
      <i class="el-icon-upload"></i>
      <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
      <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div>
</el-upload>
    
BeforeUpload: function (file) {
      let Size = (file.size / 1024 / 1024).toFixed(3);
      console.log(Size + "MB");
      console.log(file);

      if (Size > 10) {
        this.$look("warning", "提示！", "文件大小不得超过10MB");
        return false;
      }

      let _this = this;
      let reader = new FileReader();
      reader.readAsDataURL(file);
      reader.onload = function (e) {
        let newUrl = reader.result; //图片路径
        console.log(newUrl)  //base64
      };
},
    
```

