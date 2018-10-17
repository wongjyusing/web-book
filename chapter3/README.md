## MVC是什么？？
其实，在上一章节的**总结**，哪里我们就用了MVC模式  
MVC模式（Model–view–controller）。  
- Model：模型，也可以说是数据库。  
- View：视图。  
- Controller：控制器。  

不过在python的web框架大多数称为**MTV(Model-Tempaltes-View)**模式。  
- Model：模型，也可以理解为数据库
- Tempaltes：模（mu，读第二声）板文件，也就是我们之前写的html文件。  
- View：视图，就是我们的之前写的返回内容的函数。  

读起来很奇怪对吧？？  
这里讲一下我个人学习web开发的**理解方式**。  
## UVMVT  
为什么叫UVMT呢？？  
由于我个人是通过Django入门web开发。UVMT其实就是我们打开`http://127.0.0.1:8000/python`在Django运行的过程。  
urls.py=>views.py=>models.py=>views.py=>xxxx.html  
注意，上面的路径走向是静态网站的流程。  
这种理解方式是把MVC中的C拆出来，变成U。  
V里面拆出了T。  
- 在浏览器打开`http://127.0.0.1:8000/python`  
- 路由urls.py接受到该请求，请求路径有效，匹配该路径对应的方法
- views根据传入的参数`python`  
- 在models中寻找是否有该参数匹配的字段  
- 有，则返回数据给views。  
- 根据view绑定的模板文件T返回页面给用户。  

看上去还是很懵对吧？？  
## 小说网站  
这个是一个小练习，models的内容呢，我们用data来代替。  
尝试用你喜欢的框架实现一个**三层结构的小说网站**。  
数据可以在[web开发对应的文件](https://github.com/wongjyusing/web_project)中下载，主要是**data**目录。   
里面是python的字典格式。   
里面的数据是金庸先生的15部小说。  
构建这个**三层结构的小说网站**。  
需要的知识有：  
python：字典、包引用  
html：h1、a、p标签。  
框架的模板语句，jinjia2语法（注意，每个框架的语法都不一样，自行阅读框架的文档）。  
## 开发思路  
这个网站需要写三个html文件。  
- 书的列表页
- 书的章节列表页
- 书的正文列表页  

三个视图处理方法。  
三个路径。  
网站的样式先不考虑，先学会把数据呈现到模板后，再调整。  
相信，当你自行阅读框架的文档，并成功做出了这个三层结构的小说网站后。  
不管你是用ruby的ruby on rails、还是java的Spring。都能快速上手。  
  
