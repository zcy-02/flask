# jinja2模板渲染以及html文件传参

```python
from flask import Flask, render_template

app = Flask(__name__)


@app.route('/')
def hello_world():
    return render_template("index.html")

# html文件渲染和传参
@app.route('blog/<blog_id>')
def blog_detail(blog_id):
    return render_template('blog_detail.html', blog_id=blog_id, username='zua')

if __name__ == '__main__':
    app.run()

```

我们可以在template中创建html文件并在里面写前端代码，只需在.py文件中使用render.template调用html文件并传入相应的参数即可，具体代码如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>博客详情</title>
</head>
<body>
    <p>您的用户名是：{{ username }}</p>
    <h1>你访问的博客详情是：{{ blog_id }}</h1>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ZUA</title>
</head>
<body>
    <h1>郑州航空航天大学</h1>
</body>
</html>
```

