# flask中debug、host和port的配置

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
    return 'Hello 中国!'

# 1.debug模式
# 1.1.开启debug模式后，只要修改代码后保存，就会自动重新加载，不需要手动重启项目
# 1.2.如果开发的时候，出现bug，如果开启了debug模式，在浏览器上就可以看到出错信息

# 2.修改host
# 主要作用：让其他电脑能访问到我电脑上的flask项目

# 3.修改port端口号
# 主要作用：如果当前端口被占用，可以修改port端口进行访问

if __name__ == '__main__':
    app.run()

```

