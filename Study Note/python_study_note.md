# python

1. 如何优雅地打开文件？

   ​

   `with open('*.txt','w') as file_name：`

   等价于：

   `try:`

   ​    `file_name=open('*.txt','w')`

   `except:`

   ​	`pass`

   `finally:`

   ​	`file_name.close()`



2. `@property`

   是一种修饰符，使得类方法可以像一个类属性一样使用



3. CGI(Common Gateway Interface)通用网关接口，允许WEB服务器运行一个服务器端程序



4. MVC(Model-View-Controller)模型-视图-控制器模式允许你使用一种可维护的方式设计和构建一个WEB应用
   * Model模型用来存储Web应用的数据
   * View视图用来显示Web应用的用户界面
   * Controller控制器将所有代码与编程逻辑“粘合”在一起



5. 标准库cgitb模块，允许在浏览器中查看CGI编码错误。

   可使用cgitb.enable()打开CGI跟踪



6. global 设置全局变量



7. 将json数据转换为字典数据的方法：

`import json`

`json.loads(line) for line in open(path) 	# path为json数据的路径`



8. 如何优雅地创建列表？

   ` dataid=[rec[id] for rec in records]`

   ​


9. 如何利用python自带的标准库 collections 优雅地计数？

   ` from collections import defaultdict`

   `counts=defaultdict(int)`

   `for x in data:`

   ​	`counts[x]+=1`

10. 如何利用python自带的标准库 collections 优雅地找出TOP10来？

    `>>>from collections import Counter`

    `>>>counts=Counter(list_name)`

    `>>>counts.most_common(10)`

11. `[on_true] if [expression] else [on_false]`

    exp:

    `>>>x,y=50,25`

    `small=x if x<y else y`

12. `array[start : stop : [step] ]`

    a[::]实际是一个slice类对象，把列表切片，从start开始到stop

    exp:

    `In [31]: a=[1,2,3,4,5,6,7,8,9]`	#列表下标从0开始

    `In [32]: a[1:]`	#从列表第2个到最后一个
    `Out[32]: [2, 3, 4, 5, 6, 7, 8, 9]`

    `In [33]: a[:1]`	#从列表第一个到第2个(不包括第2个)
    `Out[33]: [1]`

    `In [34]: a[-1:]`	#从列表倒数第一个到最后一个
    `Out[34]: [9]`

    `In [35]: a[:-1]`	#从列表第一个到倒数第一个（不包括倒数第一个）
    `Out[35]: [1, 2, 3, 4, 5, 6, 7, 8]`

    `In [37]: a[1:6:2]`	# 从列表第2个到列表第7个，步长为2，不包括第7个
    `Out[37]: [2, 4, 6]`

    在这里使用[::-1]可以将原列表逆序输出

    `In [47]: a[::-1]`
    `Out[47]: [9, 8, 7, 6, 5, 4, 3, 2, 1]`

13. 使用isinstance（）方法可以判断某一对象是否是某个特定类型的实例。

    exp:

    `>>>a=5`

    `>>>isinstance(a,int)`

    <<<True

    `>>>isinstance(a,(int,float))`

    `<<<True`

14. 在字符串前加r可以在字符串中使用\，相当于C#中的@

15. python中可以使用占位符%

    exp:

    `In [43]: temp='%.2f %s are worth $%d'`

    `In [44]: temp % (4.56,'sb',12)`
    `Out[44]: '4.56 sb are worth $12'`

