## Tornado  
tornado(龙卷风)，作为python的web框架。  
它属于**小而精**，非常强，但想对于其它两款框架，有一个缺点。  
它的社区支持非常少，这个话题留到后面的演示的时候就知道了。  
### hello.py  
把终端切换到web_project/chapter0/tornado_learn目录下  
`cd web_project/chapter0/tornado_learn`  
创建一个hello.py。  
写入以下的内容。  
```python
import tornado.ioloop
import tornado.web

class MainHandler(tornado.web.RequestHandler):
    def get(self):
        context = "Hello, world"
        self.write(context)

if __name__ == "__main__":
    application = tornado.web.Application([
        (r"/", MainHandler),
    ])
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()

```  
执行`python hello.py`。  
然后在浏览器输入`http://127.0.0.1:8888/`   
就可以看到**Hello, world**。  
原理方面，还是留到后面的总结来讲。
