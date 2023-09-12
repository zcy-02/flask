# jianja2模板过滤器的使用

#### 定义

过滤器：当我们使用一个变量时，可能会使用某个函数先对变量进行处理渲染，这个过程就是过滤器。

在模板中的使用方式是通过管道符号（|）来获取的

#### jinja2内置过滤器

![image-20230706112353650](C:/Users/volet/AppData/Roaming/Typora/typora-user-images/image-20230706112353650.png)

![image-20230706112447185](C:\Users\volet\AppData\Roaming\Typora\typora-user-images\image-20230706112447185.png)

![image-20230706112518600](C:\Users\volet\AppData\Roaming\Typora\typora-user-images\image-20230706112518600.png)

![image-20230706112646336](C:\Users\volet\AppData\Roaming\Typora\typora-user-images\image-20230706112646336.png)

#### jinja2自定义过滤器

![image-20230706112934159](C:\Users\volet\AppData\Roaming\Typora\typora-user-images\image-20230706112934159.png)

#### 过滤器的使用

```python
@app.route("/filter")
def filter_demo():
    user = User(username="知了", email="xx@qq.com")
    return render_template("filter.html", user=user)
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>过滤器demo</title>
</head>
<body>
{{user.username}}-{{user.username|length}}
</body>
</html>
```

运行结果rt

![image-20230706113229616](https://gitee.com/zcy-02/typora-images/raw/master/img/202307111702030.png)
