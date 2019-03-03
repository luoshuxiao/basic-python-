#一.分支结构
##1. if语句
###a.语法：
      if 条件语句：
          代码段
###b.说明：
     if       --关键字   
     条件语句  --任何有结果的表达式（不管结果是什么类型）（if后面的条件语句不能写赋值语句）
     ：       --  固定写法（后边第一行代码要有缩进）
     代码段    --和if保持一个缩进的一条或者多条语句
###c.执行过程:
     先判断条件语句的结果是否是Ture,如果是ture就执行冒号后面的代码段，否则不执行如果条件语句的结果不是bool，会将结果先转换为bool再判断

      num = 10
      print('%d 是偶数' %(num))
      if 10:
        print('龙哥是老板')
      if 1:
        print('中国最强')
      num=input('请输入一个整数：')
      if int(num)&1==0:
        print('%d是偶数' %int(num))
   练习：随机产生一个年龄值，如果年龄大于等于18就打印龙哥已经成年,不管年龄多    少，都打印年龄值

    import random
    age = random.randint(0,100)
    if age>=18:
       print('龙哥已经成年')
    print('龙哥已经%s岁了' %(age))
##2.  if  else 语句
###a.语法：
      if 条件语句：
          代码段1
      else:
          代码段2
###b.执行过程：
   条件语句为真，执行代码段1，否则执行代码段2

练习：随机产生一个整数，如果是奇数打印‘xxx是奇数’，否则打印'xxx是偶数'

       import random
       int1 = random.randint(0,1000)
       if int1 & 1 ==0:
            print('%d亿人民币是龙哥的偶数' % int1)
       else :
            print('%d亿人民币是龙哥的是奇数' % int1)
##3. if  elif   else语句
###a.语法：
      if  条件语句1：
           代码段1
      elif 条件语句2:
           代码段2
      elif 条件语句3：
           代码段3
      .............
      else :
           代码段4
###b.执行过程：
   首先判断条件语句1，如果为真，执行代码段1，如果为假，判断条件语句2，

   条件语句2为真，执行代码段2，如果为假，判断条件语句3，以此类推，

   前面所有条件为假，那么执行最后的else后的代码段4

注意：1.后 面的条件的判断前提是前面的条件均不成立

  2.这儿的elif根据情况可以有多个，else也可以省略

练习：根据成绩对成绩进行分段评价：小于60分打印不及格，60到70打印及格，71到89打印良好，90以上打印优秀

      int1 = input('请输入分数')
      if  0<=int(int1) <=60:
        print('你娃娃不及格，回去吃奶吧')
      elif 0<=int(int1)<=70:
          print('你娃娃刚及格，还需用心哦')
      elif 0<=int(int1)<=80:
          print('还可以，勉强过得去')
      elif 0<=int(int1)<=90:
          print('不错，nice')
      elif 0<=int(int1)<=100:
          print('牛逼')
      else :
          print('老板，你大爷的,输错了')     
##4. if  嵌套
     可以在if,elif,else后面的代码中，都可以再写其他的if语句
练习：如果一个数字是偶数就打印偶数，否则打印奇数。如果偶数还能被4整除再打印4的倍数
     
    num =int(int1)
    if num %2 ==0:
       print('分数是偶数')
       if num % 4 ==0:
          print('分数是4的倍数')
       else :
          print('分数不是4的倍数')
    else :
         print('分数是奇数')
         if num % 5 ==0:
            print('分数是奇数，并且是5的倍数')
练习：输入一个字符串，判断第一个字母是否是字母，如果是打印'以字母开头'，如果这个字母是大写的，在打印’大写字母


    str2 = input('输入一个字符串：')
    if 97<= ord(str2[0]) <=122 or 65<=ord(str2[0])<=90:
        print('以字母开头')
        if 65<=ord(str2[0])<=90:
            print('大写字母')
    if str2[0].isalpha():
        print('以字母开头')
        if str2[0].isupper():
            print('字母是大写字母开头')
 练习： 随机生成字母

         char=chr(random.randint(97,122))
         print(char)
#二.for循环
#### python中的循环结构有两种：for循环和while循环
#### 什么时候用循环：某个操作需要重复操作的时候用循环
 
##1.定义
###a.语法：

    for 变量 in  序列：
           循环体
###b.说明：
    for --  关键字
    变量 -- 变量名，随便命名（满足变量名的要求）
    in --  关键字
    序列 --  只能是序列类型的数据（字符串，列表，元祖、字典、集合、迭代器、range等）
    循环体 -- 和for保持 一个缩进的一条或者多条语句（需要重复执行的代码）
###c.执行过程：
    让变量去序列中取值，取一个值，执行一次循环体，取完为止（序列中值得个数决定了循环的次数）
    for x in 'abcde':
        print(x)
        print('龙哥是亿万富翁')
##2. range  表示范围
       range(n)--产生一个数字序列，序列中的内容是0到n-1（结果是序列）
       range(m,n) --产生一个从m到n-1的数字序列
       range(m,n,step)--产生一个从m,每次加step，直到n前面的数字序列

       range 一般用在：a.需要产生指定范围的数字序列
                      b.单纯的控制for循环的循环次数
      for num in range(10):
          print(num)
      print('````````')
      for num in range(10,21):
          print(num)
      print('````````')
      for num in range(5,15,3):
          print(num)
      print('````````')

####练习：求1+2+3+4+。。。+100
     he=0      #   先定义一个变量用来放求和的结果
     for num in range(1,101):
         he+=num
     print(he)
     print(num)
####  练习：2+4+6+。。。+100求和
     sum1=0
     for num in range(2,101,2):
         sum1+=num
     print(sum1)
     sum2=0
     for num in range(1,101):
         if num&1==0:
             sum2+=num
     print(sum2)

####练习：写程序统计字符串中数字字符的个数

     str1=input('请输入一串字符：')
     sum1=0
     for num in range(len(str1)):
         if str1[num].isdigit():
             sum1+=1
     print('该字符串中的数字个数为：%d' %(sum1) )

     str1=input('请输入一串字符：')
     sum1=0
     for char in str1:
         if '0'<= char <='9':
             sum1+=1
     print('这个字符串中的数字个数为 %d' % sum1)   
##3. 注意：
      如果for后面的变量取到的值，在循环体里面不使用，那么这个变量命名的时候，用一个_来命名
       for _ in range(100)：  （_下划线表示不需要带入循环的变量） 
#三. while 循环
##1. while 循环
###a.语法：
     while 条件语句：
          循环体
###b.说明：
     while--关键字
     条件语句---有结果的表达式（除了赋值语句，一般表达式都行）
     ： --  固定写法
     循环体-- 和while保持一个缩进的一条或者多跳语句（会被重复执行）
###c. 执行过程：先判断条件语句是否为真，是真就执行循环体，
              执行完循环体再判断条件语句是否为真，为真再执行循环体，以此类推
              直到条件语句判断为假，整个循环结束
     num=1
     while num <= 10:
         print(num)
         num += 1
     print('num=%d' % num)
     print('结束')
####练习：1*2*3*...*10
    sum1=1
    num =1
    while num<=10:
        sum1*=num
        num += 1
    print(sum1)
####  练习：获取字符串中的每一个字符
    str22 = input('请输入一串字符：')
    num=0
    while num < len(str22):
        print('第%d个字符是：%s' %(num+1,str22[num]))
        num+=1
    print('结束')
##2.for 循环和while 循环的选择
（python中for循环能做到的while循环都能做到，相反则不一定）

    使用for循环：
        a.获取序列中的元素（值）
        b.循环次数确定
    使用while循环：
        a.循环次数不确定
        b.死循环

####练习： 程序可以 不断的输出知道输入的值为0为止
    str11=input('请输入：')
    while  str11!='0':
        str11 = input('请输入：')
    print('结束')
#四.循环中的continue/break/else
## 1. continue--continue是一个关键字，只能写在循环体里
    
    功能 ：当循环执行过程当中遇到continue，会结束当次循环，直接进入下次循环的判断。
        （进入下次循环判断：for循环就是用变量取下一个值，while循环就是直接判断条件语句是否是真）

## 2. break--是一个关键字，只能写在循环体里

    功能：当循环过程中遇到，整个循环直接结束
## 3. else
###    a .语法 （仅在python中有，其他语言没有这个用法）
    while 条件语句：
          循环体
    else :
         代码段

    for 变量 in  序列：
         循环体
    else :
       代码段
###    b.执行过程：  不影响原循环的执行过程
            当循环自然死亡的时候，就会执行else后边的代码段
            循环因为遇到break的时候不会执行else后面的代码段

      for x in range(5):
          print(x)
          if x==3:
              break
      else :
          print('for循环结束了')