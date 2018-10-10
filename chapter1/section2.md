## 使用模板
同样的复制**hello.html**到和我们的py文件同级的目录下。  
结构如下：
```bash
.
├── hello.html
└── hello.py

0 directories, 2 files

```
打开hello.py
写入以下的内容：
```python
import tornado.ioloop
import tornado.web

class MainHandler(tornado.web.RequestHandler):
    def get(self):
        context = "Hello, world"
        #self.write(context)
        # render 中文意思是，渲染，给予
        # 感觉渲染比较符合翻译的意思吧
        # 当接受到请求后渲染hello.html的内容
        self.render(template_name='hello.html')

if __name__ == "__main__":
    application = tornado.web.Application([
        (r"/", MainHandler),
    ])
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()

```
执行`python hello.py`后。
通过浏览器打开`http://127.0.0.1:8888/`即可看到效果。
