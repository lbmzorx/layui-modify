# layui-modify
layui is very useful ui frame ,but some function need to modify and lots of characters would be support


update laydate
###laydate 

# layui的修改

### upload文件上传的修改
1、增加 selectedfile函数<br>
    可在config json对象中配置使用，该函数是最先执行的回调，在官方choose函数之前执行,参数
    为选择的文件
    
    upload.render({
       selectedfile:function(files){
            console.log(files);   //文件对象
        },
     });
    
    
2、增加datadeal函数<br>
  可在config json对象中配置使用，该函数在上传前执行，before函数之后执行，
  参数为等待上传的表单对象，需要返回该对象，否则不做处理。

    upload.render({
      datadeal:function(data){
        console.log(data);    //form对象
        return data;
      },
    });

  同时更改了表单的顺序，原来的顺序是先带上传文件，然后是自己配置的额外参数data，现在交换
  了一下顺序，以便适应对象存储的需要（阿里云对象存储必须要换顺序）
  
  3、加参数<br>
  
    给done加第四个参数，为服务器响应的文本信息
    
    给error加第三个参数，为服务器响应（可以获取码），第四个参数为服务器响应的文本信息
    
  
     error:function(index,upload,res,texterr){
        console.log(res.status); //状态码，比如404，500
        console.log(texterr);    //error
     }

