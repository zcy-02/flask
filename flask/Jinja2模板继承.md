# Jinja2模板继承

一个网站中，大部分网页的模块是重复的，比如顶部的导航栏，底部的备案信息。如果在每个页面中都重复的去写这些代码，会让项目变得臃肿，提高后期维护成本。比较好的做法是，通过模板继承，把一些重复性的代码写在父模板中，子模板继承父模板后，再分别实现自己页面的代码。

```html
#父模板
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>这是父模板</title>
</head>
<body>
我是父模板的文字
</body>
</html>
```

```HTML
#子模板
{% extends "base.html" %}
```

```python
@app.route("/child1")
def child1:
    render_template("chilld.html")
```

![image-20230822145456422](https://gitee.com/zcy-02/typora-images/raw/master/img/202308221455608.png)

对于子模版我们需要添加或者修改的地方，我们就再父模板中定义成block，然后在子模板调用即可

```html
#父模板
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>{% block title %} {% endblock %}</title>
</head>
<body>
我是父模板的文字
{% block body %} {% endblock %}
</body>
</html>
```

```html
#子模板
{% extends "base.html" %}

{% block title %}
我是子模板的标题
{% endblock %}

{% block body %}
我是子模板的文字
{% endblock %}
```

![image-20230822181152112](https://gitee.com/zcy-02/typora-images/raw/master/img/202308221811182.png)

