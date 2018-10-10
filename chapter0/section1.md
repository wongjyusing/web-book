## Django  
Django(丛林)，作为python的web框架。  
它属于是**大而全**。同时也说明它很**笨重**。   
我的个人意见，如果你是小白，想要学习python的web开发，最好从Django入手。  
可能，它一开始的配置和使用，很麻烦。  
但是学会Django后，再去学习其它两款框架，你只需要了解一下它们之间的区别，就可以很快上手。  
## 创建一个django项目  
现在创建和配置会很麻烦。不过请忍耐一下。  
后面的其他练习可以直接复制这个项目，然后修改里面的一两个文件即可。  
把终端目录切换到**chapter0/django_learn**目录下
注意是要在**虚拟环境**中哦。  
依次执行下面的命令。  
```bash
django-admin startproject learn

cd learn

python manage.py startapp hello

touch hello/urls.py

mkdir templates

mkdir static
```
这个时候目录结构如下：
```bash
.
├── hello
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── learn
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── static
└── templates

5 directories, 13 files
```
现在呢，先不介绍每个文件和目录作用。  
后面总结再讲，我们先配置好项目并运行起来后再说吧。  
## 配置learn项目  
### settings.py
打开learn目录下的settings.py文件。根据下面给出的代码对原来的代码进行替换。  
```python
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'hello',
]

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

# Internationalization
# 国际化 这里有很多修改，可以直接复制粘贴即可
# https://docs.djangoproject.com/en/2.1/topics/i18n/

LANGUAGE_CODE = 'zh-hans'  # 有修改，zh-hans 简体中文

TIME_ZONE = 'Asia/Shanghai' # 有修改 设置时区 亚洲/上海

USE_I18N = True

USE_L10N = True

USE_TZ = False          #关闭国际时间


# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/2.1/howto/static-files/
STATIC_URL = '/static/'
# 静态文件配置路径  有修改  后期部署环节需要删掉
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static'),]
```
这个settings.py的内容先不用管，后面我会在附录中放一份我翻译后的settings.py文件。  
### urls.py  
现在，我们项目中有两个urls.py，我们先修改在learn目录下的urls.py文件
```python
"""learn URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/2.1/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path,include

urlpatterns = [
    path('',include('hello.urls')),
    path('admin/', admin.site.urls),
]
```
然后编写**hello**目录下的urls.py
```python
from django.urls import path
from . import views
urlpatterns = [
    path('',views.home,name='home'),
]
```
最后打开hello目录下的views.py文件。  
写入下面的内容：
```python
from django.shortcuts import render,HttpResponse

# Create your views here.
def home(request):
    context = 'hello world!'
    return HttpResponse(context)
```  
## 运行项目  
把终端切换到根目录下，有**manage.py**文件的目录就是根目录。  
使用下面的命令运行项目。  
`python manage.py runserver`  
通常终端哪里会有一堆红字，不用管。  
打开浏览器，输入`http://127.0.0.1:8000/`即可看到**hello world!**，这几个字。  
说明项目运行成功。  
至于为什么呢？留到后面总结哪里再讲。  
