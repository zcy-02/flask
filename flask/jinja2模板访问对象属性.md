# jinja2模板访问对象属性

#### 1.访问类中对象的值

创建一个类并在index文件中返回他：

```python
class User:
    def __init__(self,username,email):
        self.username = username
        self.email = email

@app.route('/')
def hello_world():
    user = User(username="zua", email="xx@qq.com")
    return render_template("index.html", user=user)
```

就可以在index文件中调用user类的对象

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ZUA</title>
</head>
<body>
    <h1>郑州航空航天大学</h1>
    {{user.username}} / {{user.email}}
</body>
</html>
```

#### 2.访问字典中的对象

```python
@app.route('/')
def hello_world():
    user = User(username="zua", email="xx@qq.com")
    person = {
        "username": "张三",
        "email": "zhangsan@qq.com"
    } #创建字典
    return render_template("index.html", user=user, person=person)#在index文件中返回他

```

然后直接可以在index文件中调用它

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ZUA</title>
</head>
<body>
    <h1>郑州航空航天大学</h1>
    <div>{{user.username}} / {{user.email}}</div>
    <div>{{person['username']} / {{person.username}}}</div>#两种访问的方式
</body>
</html>
```

