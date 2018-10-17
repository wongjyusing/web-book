## Tornado  
把之前的代码复制一份，包括html文件。  
到另一个目录下进行练习。  
打开hello.py文件。  
写入如下内容：
```python
import tornado.ioloop
import tornado.web

class MainHandler(tornado.web.RequestHandler):
    def get(self):
        context = "Hello, world"
        #self.write(context)
        self.render(template_name='hello.html')

class HelloHandler(tornado.web.RequestHandler):
    def get(self,name):
        context = f"Hello, {name}"
        self.write(context)


class HiHandler(tornado.web.RequestHandler):
    def get(self,name):
        context = f"Hi, {name}"
        #self.write(context)
        self.render(template_name='hi.html',context=context)

if __name__ == "__main__":
    application = tornado.web.Application([
        (r"/", MainHandler),
        (r'/hello/(?P<name>[\w-]+)',HelloHandler),
        (r'/hi/(?P<name>[\w-]+)',HiHandler),
    ])
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```  
新建一个名为hi.html的文件。  
写入如下内容:
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
通过浏览器打开`http://127.0.0.1:8888/hello/python`  
然后，打开`http://127.0.0.1:8888/hi/ruby`  
好了，现在请大家把上面链接最后的后缀，python或者ruby替换成你的英文名试一下。
