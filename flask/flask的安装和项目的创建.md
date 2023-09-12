# flask的安装和项目的创建

##### 安装：

win + r进入命令行输入：pip install flask(要求在环境变量中配置好python和stricp，否则命令行不能执行pip命令)

##### 创建一个flask项目：

```python
# 从flask这个包中导入Flask类
from flask import Flask

# 使用Flask类创建一个app对象
# __name__:代表当前app.py这个模块
# 1.以后出现bug，它可以帮助我们快速定位
# 2.对于寻找模版文件，有一个相对路径
app = Flask(__name__)

# 创建一个路由和视图函数的映射
# /表示根路由
@app.route('/')
def hello_world():
    return 'Hello World!'


if __name__ == '__main__':
    app.run()
```

![image-20230415143510487](C:\Users\volet\AppData\Roaming\Typora\typora-user-images\image-20230415143510487.png)