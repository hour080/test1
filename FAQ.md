* python的帮助： help(str)  可以查看str字符类的帮助信息。
* python没有括号来表明语句块，而是采用缩进来表示这一语法。
* 一定要用自然字符串处理正则表达式。否则会需要使用很多的反斜杠。例如，后向引用符可以写成'\\1'或r'\1'。 
* for循环的区间是半开区间：range(1,5,2)给出[1,3]。记住，range 向上延伸到第二个数，即它不包含第二个数。
* print语句的结尾使用了一个 逗号 来消除每个print语句自动打印的换行符。
* 列表的sort方法来对列表排序。需要理解的是，这个方法影响列表本身，而不是返回一个修改后的列表——这与字符串工作的方法不同。
    这就是我们所说的列表是 可变的 而字符串是 不可变的 。
* 因为从文件读到的内容已经以换行符结尾，所以我们在print语句上使用逗号来消除自动换行。最后，我们用close关闭这个文件。
* 安全使用  and-or  技巧: (1 and [a] or [b] )[0]  
    由于 [a] 是一个非空列表，所以它决不会为假。即使 a 是 0 或者 '' 或者其它假值，列表 [a] 也为真，因为它有一个元素。
    在 Python 语言的某些情况下 if 语句是不允许使用的，比如在 lambda 函数中。
* 从notepad++执行python代码：cmd /k python "$(FULL_CURRENT_PATH)" & PAUSE & EXIT  然后 run -> run设置快捷键
* python 3 开始默认utf-8的编码模式，因此在2.x版本下要注意字符编码的问题：
    #!/usr/bin/python
    #coding:utf-8           #如果出现编码问题，需在开头加上这句
    movies=[]
    print('movies List的长度是：'+str(len(movies)))      #注意不像java隐式类型转换，要str显示转换类型
* 转置一个元组：
    a = (1,2,3,4,5)
    b = list(a)[::-1]
    print b   #[5, 4, 3, 2, 1]
    或者直接调用revered函数：
    >>> a = (1,2,3,4,5)
    >>> aa=tuple(reverse(a))
    >>> print (aa)
    (5, 4, 3, 2, 1)
    >>> 
* *和**作为参数列表的区别：
    不定长参数 *para,**para
    参数格式为 *para 表示接受一个元组
    为 **para 表示接受一个字典
    *para要在**para之前
* 三元表达式推荐写法：foo = val1 if condition else val2
* 为啥[""]为真而("")为假呢
    那是因为 ("") 是空的字符串，而不是元组对象。 而前者则是一个 list 对象。
* python的颜色设置：
    def inred( s ):
        return "%s[31;2m%s%s[0m"%(chr(27), s, chr(27))
    print 'this is a very '+inred('important')+' thing'    
* 有人知道以lambda作为参数的函数应该怎么写？可以用lambda作回调处理的
    def test(a,b):
    return a(b)
    test(lambda a:a+1, 1)
    是这种还是在test里返回函数？
    那直接用函数做参数行吗？
    当然可以
    不用把java的思维带进来，python里函数也是可传递的 
* json.dumps在默认情况下，对于非ascii字符生成的是相对应的字符编码，而非原始字符，例如：
    >>> import json
    >>> js = json.loads('{"haha": "哈哈"}')
    >>> print json.dumps(js)
    {"haha": "\u54c8\u54c8"}
    解决办法很简单:
    >>> print json.dumps(js, ensure_ascii=False)  
    {"haha": "哈哈"}  
* 关于python打印乱码的问题：
    （1）、print list 出现：a1\xc7\xc9\xba\xc3\xd3\xc3\xb5\xc4\xd2\xf4\xc1\xbf\xbf\xd8\xd6
    （2）、print str 正常
    原因：
    在执行 print 时，如果是一个字符串，就直接输出。如果是其它的对象，python会调用这个对象的 __str__ 或 __repr__
    来进行处理，对象list本身不是一个字符串，你要打印它，python会自动调用 repr(list) 来处理，这样就生成 list
    所表示的字符串，然后打印出来了。所以你看到的是 list 的字符串表示。其中的字符串都转为 \x这种内码表示形式了。
    例如：
    >>> a={}
    >>> a["abc"]="中国"
    >>> print a
    {'abc': '\xe4\xb8\xad\xe5\x9b\xbd'}
    >>> print a["abc"]
    中国
    >>>
    （3）、print会解释内嵌换行符，以友好显示 （P198）
    >>>bytes = open('datafile.txt').read()
    >>>bytes
    "apam\n43\n"
    >>>print bytes
    apam
  
