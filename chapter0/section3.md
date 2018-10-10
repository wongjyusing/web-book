## Flask
flask(烧瓶)，这个的代码更简单。  
在web_project/chapter0/flask_learn目录下创建一个hello.py文件，写入下面的内容。
```python
from flask import Flask

app = Flask(__name__)


@app.route('/')
def hello():
    return 'Hello, World!'
```  
五行代码就可以做出一个小型服务器。  
它在python的web框架中属于**小而轻**的一款框架，它和Django一样，有非常好的社区支持。  
它的运行方式如下：
添加环境变量。  
`export FLASK_APP=hello.py`  
运行项目：  
`flask run`
在浏览器中输入`http://127.0.0.1:5000/`即可看到效果。  
在下一章节，将讲解我们做的三个小项目到底发生了什么？
