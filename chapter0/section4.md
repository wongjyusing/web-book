## MVC
MVC（Model–view–controller），中文意思是：模型-视图-控制器。  
模型这方面先不介绍，因为之前我们只用到视图和控制器。  
先从Django说起吧。  
### Django  
从Django中，我们可以很直观的看到**视图**是在我们之前写的views.py。
```python
# hello/views.py
from django.shortcuts import render,HttpResponse

# Create your views here.
# 在这里创建你的视图

# 创建一个名为home的函数，参数是请求
def home(request):
    context = 'hello world'
    # 返回的内容是 http响应context
    # 用大白话说，就是当接受到请求
    # 返回context的内容
    return HttpResponse(context)
```
控制器呢？？  
缩小范围来说，控制器相当于我们之前编写的urls.py文件。  
现在只讲hello目录下的urls.py。  
```python
# 从django路由中导入 路径方法
from django.urls import path

# 从当前目录下导入views
from . import views

# 路由参数配置
urlpatterns = [

    # 路径方法
    # 第一个参数是路径，路径为空，说明是根目录
    # 第二个参数是采取的方法，采取的是views中的home函数
    # 第三个是该路径的变量名，现在用不到，后面再讲。
    path('',views.home,name='home'),
]
```
urls.py相当于是**路由器**。用于分配路径。    
一个网站，相当于是一个路由器。  
以我的[博客为例](porksuimai.com)，现在你们点进去是首页，也就是根目录，当你点击里面的其他内容，就会跳到其他页面，相应的网址的后缀也会发生变化，也就是到了其他的路径。  
如果我们现在在浏览器输入`http://127.0.0.1:8000/hello`的话。  
只会看到404页面，当然其它框架也是同样的效果。  
这是因为我们没有定义`http://127.0.0.1:8000/hello`的处理方法。  
### Tornado
现在看一下Tornado的代码。  
在原来的基础上，添加了一个方法
```python
# 导入 龙卷风的 输入输出循环
import tornado.ioloop
# 导入 龙卷风的 web
import tornado.web

# 新建一个类，继承了 龙卷风web中的响应处理器 方法
class MainHandler(tornado.web.RequestHandler):
    # 当请求为get时
    def get(self):
        context = "Hello, world"
        # 写出context的内容
        self.write(context)

class HelloHandler(tornado.web.RequestHandler):
    def get(self):
        context = "你好，世界!"
        self.write(context)

if __name__ == "__main__":
    # 应用等于 龙卷风应用了下方的列表中的方法
    application = tornado.web.Application([
        (r"/", MainHandler),
        (r"/hello", HelloHandler),
    ])
    # 应用监听8888端口
    application.listen(8888)
    # 龙卷风的 开始 当前的 输入输出循环
    tornado.ioloop.IOLoop.current().start()
```
这个时候，大家试一下运行tornado的hello.py文件，  
在浏览器中输入`http://127.0.0.1:8888`和`http://127.0.0.1:8888/hello`看一下效果。  
### Flask
这个就一目了然了
```python
# 从烧瓶导入烧瓶方法
from flask import Flask
# 实例化烧瓶的__name__
app = Flask(__name__)

# 装饰器方法，绑定根路径
@app.route('/')
# 根目录采取的方法是hello_world函数返回'Hello, World!'文本内容
def hello_world():
    return 'Hello, World!'
```
