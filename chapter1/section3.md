## Flask
在你存放flask的hello的目录下创建一个名为**templates**的目录。  
把hello.html复制到里面去。
目录结构如下：
```bash
├── hello.py
├── __pycache__
│   └── hello.cpython-36.pyc
└── templates
    └── hello.html

2 directories, 3 files

```   
hello.py的内容如下。
```python
from flask import Flask
from flask import render_template

app = Flask(__name__)

@app.route('/')
def hello_world():
    #return 'Hello, World!'
    return render_template('hello.html')
```
使用命令`flask run`  
并在浏览器中打开`http://127.0.0.1:5000/`即可看到效果。  
