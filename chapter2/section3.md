# Flask
复制之前的项目到另外一个目录下。  
打开hello.py文件。  
写入如下内容：
```python
from flask import Flask
from flask import render_template

app = Flask(__name__)

@app.route('/')
def hello_world():
    #return 'Hello, World!'
    return render_template('hello.html')

@app.route('/hello/<name>')
def hello_xxxx(name):
    context = f'hello,{name}'
    #return 'Hello, name!'
    return context

@app.route('/hi/<name>')
def hi_xxxx(name):
    context = f'hi,{name}'
    return render_template('hi.html',context=context)
```
在templats目录下新建一个hi.html文件。  
写入如下内容。  
```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <meta charset="utf-8">
        <title>{{ context }}</title>
    </head>
    <body>
        <p>{{ context }}</p>
    </body>
</html>
```
然后运行项目。  
通过浏览器打开`http://127.0.0.1:5000/hello/python`  
然后，打开`http://127.0.0.1:5000/hi/ruby`  
好了，现在请大家把上面链接最后的后缀，python或者ruby替换成你的英文名试一下。
