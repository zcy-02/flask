# jinja2加载静态文件

##### 1、加载静态图片

```python
@app.route('/static')
def static_demo():
    return render_template("static.html")
```

![image-20230823160121703](https://gitee.com/zcy-02/typora-images/raw/master/img/202308231601794.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<img src="{{ url_for('static', filename='images/ironman.jpg') }}" alt="">
</body>
</html>
```

![image-20230823160222370](https://gitee.com/zcy-02/typora-images/raw/master/img/202308231602568.png)

##### 2、加载css文件

![image-20230823160736592](https://gitee.com/zcy-02/typora-images/raw/master/img/202308231607664.png)

```css
body{
    background-color: pink;
}
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
</head>
<body>
<img src="{{ url_for('static', filename='images/ironman.jpg') }}" alt="">
</body>
</html>
```

![image-20230823160833810](https://gitee.com/zcy-02/typora-images/raw/master/img/202308231608013.png)

##### 3、加载js文件

加载一个小弹窗

```js
alert("我是my.js中执行的")
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
    <script src="{{ url_for('static', filename='js/my.js') }}"></script>
</head>
<body>
<img src="{{ url_for('static', filename='images/ironman.jpg') }}" alt="">
</body>
</html>
```

![image-20230823161417720](https://gitee.com/zcy-02/typora-images/raw/master/img/202308231614783.png)