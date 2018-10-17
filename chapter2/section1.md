## Django  
先复制代码，运行以后，在本章节的总结哪里再进行讲解。  
还是复制一份之前的项目，创建Django项目和配置的确挺麻烦。  
改写hello目录下的views.py文件。  
```python
from django.shortcuts import render,HttpResponse

# Create your views here.
def home(request):
    context = 'hello world'
    #return HttpResponse(context)
    return render(request,'hello.html')

def hello(request,name):
    context = f'你好，{ name }'

    return HttpResponse(context)

def hi(request,name):
    context = {}
    context['your_name'] = name
    return render(request,'hi.html',context)
```  
改写urls.py  
```python
from django.urls import path,re_path
from . import views
urlpatterns = [
    path('',views.home,name='home'),
    re_path('hello/(?P<name>[\w-]+)/',views.hello),
    re_path('hi/(?P<name>[\w-]+)/',views.hi,)

]
```
在根目录下的templates目录下新建一个名为hi.html的文件
写入如下内容：
```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <meta charset="utf-8">
        <title>{{ your_name }}</title>
    </head>
    <body>
        <p>Hi，{{ your_name }}</p>
    </body>
</html>
```
然后运行项目。  
通过浏览器打开`http://127.0.0.1:8000/hello/python`  
然后，打开`http://127.0.0.1:8000/hi/ruby`  
好了，现在请大家把上面链接最后的后缀，python或者ruby替换成你的英文名试一下。  
  
