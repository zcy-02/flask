# jinja2控制语句

#### if语句

```python
@app.route("/control")
def control_statement():
    age = 17
    return render_template("control.html")
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>控制语句demo</title>
</head>
<body>
{% if age>18 %}
  <div>你已满18周岁，可以进入</div>
{% elif age==18 %}
  <div>你刚满18周岁，需要人陪同进入</div>
{% else %}
  <div>你未满18周岁，不能进入</div>
{% endif %}
</body>
</html>
```

结果：

![image-20230707111712972](https://gitee.com/zcy-02/typora-images/raw/master/img/202308071023690.png)

#### for循环

```python
@app.route("/control")
def control_statement():
    age = 17
    books = [{
        "name": "三国演义",
        "author": "罗贯中"
    },{
        "name": "水浒传",
        "author": "施耐庵"
    }]
    return render_template("control.html", age=age, books=books)

```

```html
{% for book in books %}
    <div>图书名称：{{book.name}}，图书作者：{{book.author}}</div>
{% endfor %}
```

注意：jinja2中的for循环没有break语句，只能循环所有内容

![image-20230707113058014](https://gitee.com/zcy-02/typora-images/raw/master/img/202308071024168.png)