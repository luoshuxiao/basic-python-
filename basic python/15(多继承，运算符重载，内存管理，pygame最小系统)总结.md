#一.多继承（很多语言都删除了多继承功能）
##1.多继承：让一个类同时继承多个类，类的方法和字段都能继承，但是对象属性只能继承第一个类的对象属性（实际开发一般不用）
   
		class Animal:
		    num=0
		    def __init__(self,name='名字',age=12,color='红毛怪'):
		        self.name = name
		        self.age = age
		        self.color = color
		    def show_info(self):
		        print('我是show')
		class Fly:
		    num1=9
		    def __init__(self,distance=0,speed=0):
		        self.distance = distance
		        self.speed = speed
		    @staticmethod
		    def show():
		        print('飞飞飞飞')
		class Birds(Animal,Fly):
		    pass
##2.类的特点：继承，封装，多态
		
		类的封装：可以对多个数据（属性）或者功能（方法）进行封装
		类的继承：让一个类拥有父类的属性和方法
		类的多态：有继承就有多态（一个类的多种子类）
#二.运算符重载：python中的函数不支持重载 ，多个相同函数名的函数，最后一个会覆盖其他函数
##1.运算符重载：在不同类中实现同一个运算符对象的魔法方法，来让类的方法支持相应的运算
     a.python中使用运算的时候，实质是在电泳相应的魔法方法
     b.python中每一个运算符都对应一个魔法方法
     c.比较运算符中，大于和小于符号，一般只需要重载一个就可以了，另外一个符会自动重载
# 三.内存管理
##1.内存区域：堆区间和栈区间
		
		堆区间内存开辟和释放：手动开辟手动释放  栈区间内存是系统自动开辟释放
		内存管理的是堆区间的内存（python已经封装了相应的内存开辟管理方法）
##2.数据的存储
		a.python中所有的数据都是对象，保存在堆区间里面
		b.python中所有的变量存储的都是存在堆区间中的数据的地址。存了对象地址的变量，又叫对象的引用
		c.默认情况下创建对象就会在堆中开辟空间存储数据，将地址返回；
		    如果是数字，字符串系统不会直接开辟空间，会做缓存，每次使用前会先在缓存中看之前有没有存过，没有存过再开辟空间，存了直接返回之前的数据地址
##3.数据的销毁:通过垃圾回收机制来管理内存的释放（java，c++等也是）
		原理：看一个对象的引用计数是否为0，为0就销毁，否则保留
		引用计数：对象的地址被变量保存（引用）的次数
		垃圾回收机制：每隔一段时间清理内存（清除引用计数为0的对象），并不是一直在清理 
		a.增加对象的引用计数：使用变量存储该对象的地址
		getrefconut(对象) --  获取对象的引用计数 （导入：from sys import getrefconut）
		b.减少对象引用计数：
		删除引用或者让当前对象的引用成为别的对象的引用
#四.pygame最小系统：
			
			import pygame   # 导入pygame模块
			pygame.init()   # 初始化pygame模块
			window = pygame.display.set_mode((400,600))   # 创建一个像素为（400,600）的窗口
			window.fill((255,255,255))  # 渲染背景（白色）
			pygame.dispaly.flip()  # 将渲染的背景显示在窗口上
			while True:
			   for enent in pygame.event.get():  #  检测事件的发生
			      if event.type == pygame.QUIT:  #  事件类型为点击关闭按钮
			           exit()       # 退出程序