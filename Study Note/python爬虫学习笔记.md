#python爬虫学习笔记
##1.BeautifulSoup库里的四个对象：
1. `bsObj=BeautifulSoup(html,"html.parser")`中的bsObj
2. 标签Tag对象
3. NavigableString对象。用来表示标签里的文字
4. Comment对象。用来查找HTML文档的注释标签，`<!--像这样的-->`

## 2.导航树

### 1.注意子标签（Children）和后代标签（descendants)的不同

* 例：如`bsObj.div.findAll.children`会找出当前标签的的子标签，若使用`bsObj.div.findAll.descendants`则会找出当前标签的所有后代标签，即子标签的子标签的……

### 2.兄弟标签

* 使用next_siblings()可以查找当前标签开始的往下的所有兄弟标签的内容
* 同理还有previous_siblings()函数

### 3.父标签

* parents和parent有时也会用到

### 3.findAll()和get_text()

* findAll()会包含标签一块显示出来，如：`<td>$15.00</td>`
* 使用findAll().get_text()则只显示内容，如：`$15.00`

## 4.正则表达式(Regular Expressiong)

* 见[正则表达式](/Users/tangchao/Documents/python学习笔记/正则表达式.md)。
* python中要使用正则表达式，需import re模块

## 5.获取标签属性

用attrs可以获取它的全部属性，比如一个<img src="http://.......">标签

可以用

`imges=bsObj.findAll("img")`

 `for image in images:`

​	`print(image.attrs["src"])`

获得<img>标签的src属性

## 6.lambda表达式

BeautifulSoup允许我们把特定函数类型当做findAll的参数。唯一的限制条件是这些函数必须把一个标签作为参数且返回结果是布尔类型。BS用这个函数来评估它遇到的每个标签对象，最后把评估结果为"真"的标签保留，把其他标签剔除。

* 例：

  `soup.findAll(lambda tag: len(tag.attrs)==2)`

  这行代码会获取有两个属性的标签。

## 7. 与BS同类的其他库：

* lxml
* HTML parser


***

# API

## 1. 一个可以知道IP地址的API：

> http://freegeoip.net/json/ip地址

## 2.HTTP从网络服务获取信息的四种方式：

* GET

  用来访问一个IP地址时使用GET方法。

  使用该方法时，信息包含在URL中，点击链接时，一般会使用该方法

* POST

  用来提交表单，创建对象和信息

* PUT

  用来更新对象或信息

* DELETE

  用来删除对象或信息

***

# 数据存储

## 1. 下载图片

可以使用urllib.request里的urlretrieve()函数

先使用

`imageLocation=bsObj.find("img")["src"]`

找到图片，然后使用

`urlretrieve(imageLocation,"logo.jpg")`

下载图片，并以logo.jpg为名保存图片

## 2.CSV（Comma-Separater Values,逗号分隔值）

* CSV是存储表格数据的常用文件格式。python里也有csv模块


* 在打开文件时可以使用encoding=来改变编码格式。如`f=open("file_name.csv","r",encoding="utf-8")`
* 如果csv文件第一行是像Name,Time一类的。可以使用DictReader()方法。接上面的例子：`dictReader=csv.DictReader(f)`。该方法会把CSV文件每一行转换成python的字典对象返回，而不是列表对象。

## 3.Python连接MySQL

`import pymysql`

`conn=pymysql.connect(host='127.0.0.1',port=3306,user='root',password='123',db='mysql',charset='utf8')`		//连接数据库

`cur=conn.cursor()`		//创建光标

`cur.execute('USE scraping')`	//选择数据库

`cur.execute('sql语句')`	//执行sql语句

`print(cur.fetchone())` 	//cur.fetchone()返回最近一次cur执行的语句

***

这段程序有两个对象：1. 连接对象（conn）；2. 光标对象（cur）

* 一个连接可以有很多个光标，一个光标跟踪一种状态（stage）信息。
* 如果有多个数据库，且需要向所有数据库写内容，就需要多个光标来处理。

***

[PyMySQL标准文档](http://legacy.python.org/dev/peps/pep-0249/)

## 4.用python发送 email

`import smtplibfrom email.mime.text import MIMETextmailto_list = ['XXX@xxx.com']  # 收件人(列表)mail_host = "smtp.163.com"  # 使用的邮箱的smtp服务器地址mail_user = "name"  # 用户名mail_pass = "pwd"  # 密码mail_postfix = "postfix"  # 邮箱的后缀def send_mail(to_list, sub, content):    me = "hello" + "<" + mail_user + "@" + mail_postfix + ">"    msg = MIMEText(content, _subtype='plain')    msg['Subject'] = sub    msg['From'] = me    msg['To'] = ";".join(to_list)  # 将收件人列表以‘；’分隔    try:        server = smtplib.SMTP()        server.connect(mail_host)  # 连接服务器        server.login(mail_user, mail_pass)  # 登录操作        server.sendmail(me, to_list, msg.as_string())        server.close()        return True    except Exception as e:        print(str(e))        return Falsefor i in range(5):  # 发送五封，不过会被拦截的。。。    if send_mail(mailto_list, "hello", "haha!"):  # 邮件主题和邮件内容        print("done!")    else:        print("failed!")`





