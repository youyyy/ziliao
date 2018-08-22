1.检查函数参数
原因：参数尽可能通用
不检查的隐患：
（1）抛异常
（2）正常执行，结果错误
（3）正常返回，引起某个对象错误，以后更难查bug
解决方案：
（1）在方法体的开头对参数进行检查
（2）用Javadoc的@throws说明可可能抛出的异常
（3）非公有方法使用assert检查参数
断言默认关闭，-ea启动。
例外：
如果检查代价大或者计算过程中已经隐含了有效检查

注意：异常转翻

例子：上次没有检查传过来的cookie是否未空

2.保护性拷贝
为了避免内部信息遭到修改

总结：使用时考虑是否容忍传进来的对象发生改变
注意：非0数组可变，
可以被子类化的参数对象不适用clone
重点：对象内部的组件尽量保证是不可变的


3.谨慎设计方法签名
命名规范
方法不要太复杂：一个方法最好完成一个功能
参数不要太长：
缩短参数：a.分解方法	b.创建辅助类	c.builder模式
参数类型优先返回接口
boolean参数优先返回枚举类型

其实现在用到的很多返回类型都是用的枚举，

4.慎用重载
覆盖是规范，重载是例外
个人观点：避免写、有参数类型是可变参数的、重载函数


5.慎用可变参数
（1）Arrays.asList()参数是可变参数
没有add和remove
Arrays.asList(int[] a) ///可变参数，打印下来是是对象的值，乱码,但是如果值是String的数组，就可以
Array.toString()

6.返回非null数组和集合，不返回null
数组集合尽量不返回null

7.写文档注释
@param
@return
@throw

{@code}
{@literal}包含html的特殊符号
注意泛型、枚举、注解要说明

8.使用Optional
解决空指针异常
1.ofnullable()可以接受null，不报异常
2.orElse()如果是空，返回默认值
3.orElseThrow()
4.get()用来获取option里面的值
5.ifPresent() 可以接受Consumer参数

集合、映射、流、数组这些要尽量返回空的
比较注重性能的地方还是返回null好一点