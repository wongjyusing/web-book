## 总结  
其实刚才三种框架的演示都是实现同一种功能：**路由传入参数**    
这里想说明的原理是，一个网站的，不同页面的内容是由路由控制的。  
不同的路由指向不同的内容。当然也可以多个路由指定一种方法。  
而传入的参数可以用作**索引**。  
例如，现在你有一个数据库。  
你可以通过路由传入的参数作为**索引**数据库来索引出内容。  
当然，这个假设是说这个索引是数据库某个字段的id值。  
## 例子  
新建一个名为books,py的文件
```python
import tornado.ioloop
import tornado.web

class MainHandler(tornado.web.RequestHandler):
    def get(self):

        context = "Hello, world"
        #self.write(context)
        self.render(template_name='hello.html')


class BookHandler(tornado.web.RequestHandler):
    def get(self,book):
        books = {
            'python':{'price':'45.00'},
            'ruby':{'price':'36.00'},
            'javascript':{'price':'40.00'},
        }
        context = books[book]
        #self.write(context)
        self.render(template_name='book.html',context=context)

if __name__ == "__main__":
    application = tornado.web.Application([
        (r"/", MainHandler),
        (r'/(?P<book>[\w-]+)',BookHandler),
    ])
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```  
新建一个book.html文件
```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <meta charset="utf-8">
        <title>{{ context }}</title>
    </head>
    <body>
        <p>价格：{{ context['price'] }}</p>
    </body>
</html>
```
运行books.py后。  
在浏览器输入`http://127.0.0.1:8888/python`  
或者`http://127.0.0.1:8888/ruby`  
看一下效果。  
