# Flask连接MySQL数据库

#####  Python操作Mysql驱动

Flask 想要操作数据库，必须要先安装 Python 操作 MySOL的驱动。在Python 中，目前有以下MySQL驱动包。
(1)MySQL-python: 也就是 MySQLdb。是对 C语言操作 MySQL 数据库的一个简单封装。遵循了 PythonDBAPIv2。但是只支持 Python2。(2)mysqlclient:是MySQL-python 的另外一个分支。支持 Pthon3 并且修复了一些 buge是目前为止执行效率最高的驱动，但是安装的时候容易因为环境问题出错。                                                                    (3)pymysql:纯 Python 实现的一个驱动。因为是纯Python 编写的，因此执行效率不如mysqlclient。也正因为是纯 Python 写的，因此可以和 Python 代码无缝衔接。                                                                 (4)mysql-connector-python: MySQL 官方推出的纯 Python 连接 MySQL的驱动，执行效率pymysql还慢。
为了减少出错，提高学习效率，选择用 pymysql作为驱动程序。如果有需要，可以自行考虑移植到 mysqlclient。pymysql 是一个第三方包，因此需要通过以下命令安装。

```
pip install pymysql
```

##### Flask-SQLAlchemy

在 Flask 中，我们很少会使用 pymysql 直接写原生 SQL 语去操作数据库，更多的是通过SQLAlchemy 提供的 ORM 技术，类似于操作普通 Pthon 对象一样实现数据库的增删改查操作，而 Flask-SQLAlchemy 是对 SQLAlchemy 的一个封装，使得在 Flask 中使用SOLAlchemy 更加方便。Flask-SOLAlchemy 是需要单独安装，因为 Flask-SOLAlchemy 依赖SQLAlchemy，所以只要安装了 Flask-SQLAlchemy，SQLAlchemy 会自动安装。安装命令如下：

```
pip install flask-sqlalchemy
```

SQLAIchemy 类似于 Jinja2，是可以独立于 Flask 而被使用的，完全可以在任何 Python程序被使用，SQLAlchey 的功能非常强大

##### 连接Mysql

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy


app = Flask(__name__)

# Mysql所在的主机名
HOSTNAME = "127.0.0.1"
# Mysql监听的端口号，默认为3306
PORT = 3306
# 连接Mysql的用户名
USERNAME = "root"
# 连接Mysql的密码
PASSWORD = "123456"
# Mysql上数据库的名称
DATABASE = "database_learn"

app.config['SQLALCHEMY_DATABASE_URI'] = f"mysql+pymysql://{USERNAME}:{PASSWORD}@{HOSTNAME}:{PORT}/{DATABASE}?charset=utf8mb4"

# 在app.config中设置好连接数据库的信息
# 然后使用SQLAlchemy(app)闯创建一个对象
# SQLAlchemy会自动读取app.config中连接数据库的信息就是【】中的内容

db = SQLAlchemy(app)


# 测试输出（1，）
with app.app_context():
    with db.engine.connect() as conn:
        rs = conn.execute("select 1")
        print(rs.fetchone())



@app.route('/')
def hello_world():
    return 'Hello World!'


if __name__ == '__main__':
    app.run()
```

使用navicat创建数据库database_learn，测试结果如下显示连接成功：

![image-20230830170756991](https://gitee.com/zcy-02/typora-images/raw/master/img/202308301707092.png)
