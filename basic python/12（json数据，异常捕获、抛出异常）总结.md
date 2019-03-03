# 一.json文件
##1.json数据：一种数据格式，满足这种格式的数据就是json数据
    json文件：文件后缀名是.json，并且文件中的内容满足json格式

##2.json格式
###a.一个json中只有一个数据（没有数据也是错）
###b.并且这个数据是json支持的数据类型

 json支持的数据类型：

	  数字类型 --  包含所有的数字，包括整数和小数，负数等（100, 1.2， -4等）
	  字符串  --   使用双引号括起来的字符集（''1323'',''dsagg'',''$%^r''等）
	  布尔   --    true 和 false
	  数组  --  相当于python中的列表，使用中括号括起来，括号里面是json支持的任意类型数据
	                 （[''abc'',''sd222'',333,true]）
	  字典  --   使用大括号括起来，括号里面 是键值对。键一般是字符串，值是json支持的任意类型数据
	  特殊值 -- null(相当于None)
##3.python中有一个内置的模块叫json，用来对json数据处理：json  导入json模块：import json

###a.将json数据转换成python数据

loads(字符串) -- 将json格式的数据 转换成python对应的数据

注意 ： 这个字符串必须是json格式数据（外层引号里面的数据是json）

			数据转换：
			json数据 ：                 python数据：
			数字类型           -->       整型/浮点型
			字符串（双引号）   -->       字符串（单引号）   
			布尔（true/false） -->       布尔（True/False）
			数组               -->       列表
			字典               -->       字典
			null               -->       None

		import json
		#json.loads('''adc''')  #  去掉单引号后的数据必须是json数据
		#json.loads('100')      #  去掉单引号后的数据必须是json数据

###b.将python数据转换成json数据

dumps(数据)  --  将python数据转换成符合json格式的字符串（字符串里面的内容是相应的数据类型）

 注意：最终json数据结果是字符串，字符串里面的内容是json格式数据

		 数据转换：
		 python数据 ：              json数据（字符串）：
		 整型/浮点型        -->       数字类型   
		 字符串（单引号）    -->       字符串（双引号）   
		 布尔（True/False） -->       布尔（true/false）
		 列表/元祖          -->       数组
		 字典               -->       字典
		 None              -->       null

		
	#   添加学生信息（姓名，年龄，电话），添加完成后，将数据保存到json文件中
	#   并且上次添加的信息不会删除，下次在添加实在上次基础上添加
		with open('json2.json',encoding='utf-8') as f:
		    xueshen=list(f.read())
		while True:
		        stu = {'name:':0,'age:':0,'num:':0}
		        stu['name:'] = input('请输入姓名：')
		        stu['age:'] = input('请输入年龄：')
		        stu['num:'] = input('请输入电话：')
		        xueshen.append(stu)
		        n = input('是否继续添加：')
		        if n == '继续':
		            continue
		        else :
		            break
		with open('json2.json','w',encoding='utf-8') as f:
		    c = json.dumps(xueshen)
		    f.write(c)

##4.json文件操作相关方法

json.load(文件对象) --  将文件对象中的数据读出来，并且转成python对应的数据

json.dump(obj,文件对象) -- 将obj数据转成json格式字符串，并且写入到文件对象中

		print('================')
		with open('test.txt', encoding='utf-8') as f:
		    content = json.load(f)
		    print(content, type(content), sep='\n')
		
		
		# with open('new.json', 'w', encoding='utf-8') as f:
		#     json.dump([1, 2, 3], f)
		
		
		def yt_dump(obj, file):
		    with open(file, 'w', encoding='utf-8') as f:
		        strstr = json.dumps(obj)
		        f.write(strstr)
		
		
		yt_dump(['a', 'b', 'c'], 'new.json')
#二.异常捕获
## 1.异常：程序运行当中出现错误，也叫出现异常
##2.异常捕获：让本来会出现异常的位置不出现异常，而是自己去处理这个异常的情况
##3.如何捕获异常：
####a.(捕获所有异常)语法：

			try :
			  代码段1
			except:
			  代码段2
  
		执行过程：执行代码段1，如果代码段1出现异常，首先不崩溃，而是马上执行代码段2（一遇到异常代码马上执行代码段2）
		           如果代码段1没有出现异常，不会执行代码段2
####b.（捕获指定异常）语法：
		try :
		   代码段1
		except 错误类型名 ：
		   代码段2
   
	执行过程：当代码段1中出现指定的错误类型后，才执行代码段2
          
####c. （同时捕获多个异常，对不同异常做出相同反应）语法：
		try :
		  代码段1
		except (错误类型1，错误类型2，错误类型3...):
		  代码段2
		  
		执行过程： 执行代码段1，如果代码段1出现指定异常中的某一种，不崩溃，执行代码段2

			try:
			    print([1,2,3][10])
			except :
			    print('出现异常')
			print('=======')
			
			try :
			    print([1,2,3][5])
			    print(int('as'))
			except (ImportError,IndexError,KeyError,ValueError,LookupError):
			    print('出现多种异常中的一种')

####d. 同时捕获多个异常，对不同的异常做出不同的反应
		try :
		  代码段1
		except 错误类型1：
		   代码段2
		except 错误类型2：
		   代码段3
		except 错误类型3：
		   代码段4
		...
		   
		'''
		'''
###4. try - except - finally

		try :
		  代码段1
		except :
		  代码段2
		finally :
		  代码段3 （一般都是写数据保存类的代码，保存程序崩溃时的数据状态（写遗书））
		  
		执行过程：代码段1和2无论会不会执行，代码段3无论如何都会执行

		try :
		    print([1,2,3][11])
		except ValueError:
		    print('下标越界')
		finally:
		    print('finally!里面的代码段')
		print('最后。。。')

		#  输入成绩，直到输入的数据输入正确为止
		while True:
		    try :
		        score= float(input('请输入成绩：'))
		        break
		    except ValueError :
		        print('输入有误！')
		        #score = float(input('请输入成绩：'))
		# 封装一个函数 ，功能是获取指定文件中的内容（普通文本文件）
		def get_file(files):
		       try :
		         with open('files',encoding='utf-8') as f:
		             coent =f.read()
		             return coent
		       except FileNotFoundError:
		           print('文件路径有误！')
		           return ''

# 三.抛出异常：主动让程序出现异常
##语法：
		raise 错误类型 --  程序执行到raise的时候直接抛出异常
		注意： 错误类型必须是一个类，并且这个类是Exception的子类