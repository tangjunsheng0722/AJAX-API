# Ajax API
## fetch API
> Fetch API 是XMLHttpRequest的现代替代方法，用于从服务器的检索资源。与XMLHttpRequest不同，它具有更强大的功能集和更有意义的名称。由于其语法和结构，Fetch也是灵活且易于使用的。但是，与其他AJAX HTTP库区别开来的是，它受到所有现代Web浏览器的支持。提取遵循一个请求-响应方法，Fetch提出请求并返回一个解析为Response对象的promise。
```
fetch('url',{
    method:'get
}).then(response=>response.json())
  .then(jsonData=> console.log(jsonData))
  .catch(err=>{
        err.log;
  })
```
如上，您可以传递一个Request对象来获取，或者，也可以仅传递要获取的资源的URL。


> 如果您需要POST表单数据或使用Fetch创建AJAX文件上传？除了Fetch之外，您还需要一个输入表单，并使用FormData库来存储表单对象
```
let inp = document.querySelector('input[type='file']');
let data = new FormData();
data.append('file',inp.files[0]);
data.append('user','aaaa');
fetch('/form',{
    method:"POST",
    body:data
})
```
## Axios
> Axios是一个基于XMLHttpRequest构建的JavaScript库，用于进行AJAX调用。它允许您从浏览器和服务器发出HTTP请求。此外，它还支持ES6原生的Promise API。 Axios的其他突出特点包括：
* 拦截请求和响应
* 使用promise来转换请求和响应数据
* 自动转换JSON数据
* 取消实时请求
> 安装Axios   npm install axios
```
axios.get('/url').then(
    function(res){
        // 执行代码
    }.catch(
        function(err){
            err.log;
        }
    )
)
```
## jQuery
> jQuery曾经是JavaScript中比较有名的一个前端库，用于处理从AJAX调用到操纵DOM内容的所有事情。尽管其他相关前端库的相关性有所降低，但仍然可以使用jQuery来进行异步调用
```
$.ajax({
    url:'/api',
    type:'get',
    dataType:'json',
    success:function(data){
        data.log;
    },
    fail:function(err){
        err.log;
    }
})
```
> 关于jQuery的好处是，你在开发遇到的疑问，你在网上都可以查找到答案和发现大量文档支持。我发现了很多使用FormData()和jQuery进行AJAX文件上传的例子。这是最简单的方法：
```
let formData = new FormData();
formData.append('file',$('#file')[0].files[0]);
$.ajax({
    url:'/api',
    type:'POST',
    data:formData,
    success: function(data){
        data.log;
    }
})
```
## SuperAgent
> superagent它是一个强大并且可读性很好的轻量级ajaxAPI，是一个关于HTTP方面的一个库，而且它可以将链式写法玩的出神入化
var superagent = require('superagent');

    superagent
        .post('/api') // method+url
        .send({ // 请求数据
            'key': 'value'
        })
        .set('header_key', 'header_value') // 设置请求头
        .end(function(err, res) { // 处理响应
            if (err) {
                //do something
            } else {
                //do something
            }
        })

## Request-简化的HTTP客户端
> Request是进行HTTP调用的最简单的方法之一。结构和语法与在Node.js中处理请求的方式非常相似。目前，该项目在GitHub上有18K星，值得一提的是：Request是可用的HTTP库之一。这里是一个例子：
```
let request = require('request');
request('/api',function(err,res,body){
    err.log;
    res.log;
    body.log;
})
```
