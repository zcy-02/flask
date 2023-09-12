# ORM模型与表的映射

##### ORM模型

对象关系映射(Object·Relationship:Mapping)，简称 ORM，是一种可以用 Python 面向对象的方式来操作关系型数据库的技术，具有可以映射到数据库表能力的 Python 类我们称之为 ORM 模型。一个 ORM 模型与数据库中一个表相对应，ORM 模型中的每个类属性分别对应表的每个字段，ORM 模型的每个实例对象对应表中每条记录。ORM 技术提供了面向对象与 SOL 交互的桥梁，让开发者用面向对象的方式操作数据库，使用 ORM 模型具有以下优势。
(1)开发效率高:几乎不需要写原生 SQL 语，使用纯 Python 的方式操作数据库，大大的提高了开发效率。“
(2)安全性高:ORM 模型底层代码对些常见的安全问题，比如 SQL 注入做了防护,比直接使用 SOL语句更加安全。
(3)灵活性强: Flask-SQLAchemy 底层支持 SOLite、MySOL、Oracle、PostgreSOL等关系型数据库，但针对不同的数据库，ORM 模型代码几乎一模一样，只需修改少量代码，即可完成底层数据库的更换。

代码如下：

```python
class User(db.Model):
	_tablename_- ="user"
    id = db.Column(db.Integer，primary_key=True，autoincrement=True)
	# varchar，nul=0
	username = db.Column(db.String(100)，nullable=False)
	password = db.Column(db.String(100)，nullable=False)
# user = User(username="法环在徒张三”"password='111111')
# sql: insert user(username，password) values('法外狂徒张三'，111111');
with app.app_context():
	db.create_all()
```

运行结果：

![image-20230830172724010](https://gitee.com/zcy-02/typora-images/raw/master/img/202308301727133.png)