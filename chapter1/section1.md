## 使用模板  
首先，把上一章节的learn项目，复制一份。  
到你需要练习的目录中。  
把上一小节的hello.html文件复制到learn中的templates目录下。  
项目结构如下：
```bash
.
├── db.sqlite3
├── hello
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   ├── __init__.py
│   │   └── __pycache__
│   │       └── __init__.cpython-36.pyc
│   ├── models.py
│   ├── __pycache__
│   │   ├── admin.cpython-36.pyc
│   │   ├── __init__.cpython-36.pyc
│   │   ├── models.cpython-36.pyc
│   │   ├── urls.cpython-36.pyc
│   │   └── views.cpython-36.pyc
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── learn
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-36.pyc
│   │   ├── settings.cpython-36.pyc
│   │   ├── urls.cpython-36.pyc
│   │   └── wsgi.cpython-36.pyc
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── static
└── templates
    └── hello.html    # 模板文件

8 directories, 25 files
```
## 开始  
我们这次只需要修改一个文件即可。  
hello目录下的views.py。  
### views.py
写入以下的代码
```python
from django.shortcuts import render,HttpResponse

# Create your views here.
def home(request):
    context = 'hello world'
    #return HttpResponse(context)
    # 注意，下面的代码中，request是必须是第一个参数

    return render(request,'hello.html')
```
使用命令`python manage.py runserver`。  
并在浏览器上打开`http://127.0.0.1:8000`即可看到效果
