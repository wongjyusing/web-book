## 路由  
路由的概念就不用文皱皱的说法了。   
我们把一个网站比喻成是一个小区。  
网站的域名相当于是小区的名字，地址。  
举个例子，我现在的域名是[porksuimai.com](http://www.porksuimai.com/#/)，里面有博客列表，教程列表、关于等内容。相当于是小区的门牌号。  
每个门牌号对应的功能可能都不相同。  
例如说，一号楼是住宅区、二号楼是会所、三号楼是商场、四号楼是住宅区……   
结合代码来讲，这里用tornado的代码作为演示：
```python
import tornado.ioloop
import tornado.web
# 中文
class ChinaHandler(tornado.web.RequestHandler):
    def get(self):
        context = "你好 世界"
        self.write(context)

# 英文
class USAHandler(tornado.web.RequestHandler):
    def get(self):
        context = "Hello, world"
        self.write(context)

# 日文
class JapanHandler(tornado.web.RequestHandler):
    def get(self):
        context = "こんにちは、世界"
        self.write(context)



if __name__ == "__main__":
    application = tornado.web.Application([
        (r"/", ChinaHandler),
        (r"/china", ChinaHandler),
        (r"/usa", USAHandler),
        (r"/japan", JapanHandler),
    ])
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()

```
现在我们定义了中英日的三种方法，四个路由路径。  
把项目运行起来看一下效果。  
假如，我们输入一个不存在的路径会怎样？？  
报错，返回404。  
简单来说，路由就是用来分配网站的地址。  
## 传参  
上一章节讲过，假如我们有许多页面，该怎么办？？  
写一堆html和一直手动定义路由？？  
这个时候就需要传参。这个需要结合代码来实现。   
这次采取的是**CS50(Computer Science 50)** 公开课用到的例子。  
你好，xxxx  
