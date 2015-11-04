Day02

无参数方法声明 -(返回值)方法名;

有参数方法声明 -(返回值)方法名1:(参数类型) 参数名;

-(返回值)方法名1:(参数类型) 参数名 and:(参数类型2) 参数名2;

举例: -(void)info:(NSString *name) andAge:(int)age;

注意:冒号是方法名的一部分

实例变量书写规范

@interface Person : NSObject
{
    //类的属性
    int _age;
    NSString *_name;

}
@end
//-----------------------对象存储细节

当创建一个对象的时候：Person *p1 = [Person new] 做了三件事情： 1.1，申请堆内存空间； 1.2，给实例变量初始化 1.3，返回所申请空间的首地址;

实例变量保存在堆区

对象方法保存在代码区

一个类可以创建多个对象；

#pragma mark 指令

功能:对代码分组,方便代码查找和导航

使用格式: #pragma mark -

#waring 等待处理的功能,或者是未完成的功能

函数和对象方法的区别

-(void)run;

(1) 对象方法的实现在@implementation...@end中
对象方法的声明只能写在 @interface...@end中间

(2) 对象方法都以-号开头

(3) 对象方法只能由对象来调用

(4) 函数属于整个文件,可以写在文件中的任何位置,包括@implementation...@end中,但写在 @interface...@end会无法识别,函数的声明可以在main函数内部也可以在main函数外部。

(5) 对象方法归对象所有

函数: void run(){}

(1) 所有的函数都是平行的
(2) 函数不存在隶属关系
(3) 使用的时候可以直接调用
(4) 不可以访问对象中的成员变量
常见错误汇总

1) @interface @end和@implementation @end不能嵌套包含

2) 只有类的声明没有类的实现 只有@interface没有@implementation时,程序编译能够通过,但是执行报错

3) 漏写@end

4) 两个类的对象声明顺序(可以把顺序打乱)

5) 成员变量没有写在{}里 错误的

6) 方法的声明写在了{}里面 错误的

7) 在声明时不能对类的成员变量进行初始化,请注意成员变量不能脱离对象而独立存在

8) 方法无法像函数那样的调用

9) 成员变量和方法不能用static等关键字修饰,不要和c语言混淆

10) 类的实现可以写在main函数后面,在使用之前只要有声明就可以

注意：#warning 列举这些常见错误,是为了告诉大家要往正确的方向去学习去编写代码.把自己编写代码的习惯更正过来

对象和方法之间的关系

-(返回值)方法名1:(参数类型) 参数名;

(1)，对象作为方法的参数
-(void) displayPerson:(Person *)person{
  NSLog("姓名:%@",person->name);
}
(2)，对象作为方法的返回值
-(Person *)changePerson:(Person *)person{
  person->name = @"唐僧";
  return person;
}
关联关系(之后还会着重讲)

人拥有狗这个成员变量

@interface Person : NSObject
{
@public
    Dog *_dog;  //null      关联关系    Person对象里面拥有了一个Dog对象
}

......

Person *p = [Person new];
//给p一个dog
p->_dog = d1;  //人拥有d1这只狗
对象作为方法参数的连续传递

练习方法

1----看到题目 写代码 允许写伪代码作为提示
2----看着题目 写伪代码 写完伪代码 可以尝试敲代码
3----copy题目 copy伪代码 尝试去写代码
4----打开现成代码 看懂这个代码 对着敲 至少也得敲2遍 */
结构体作为类的实例变量。给结构体赋值的三种方法：

typedef struct {

    //年
    int year;
    //月
    int month;
    //日
    int day;

}MyDate;
// 第一种：直接赋值，并强转；
stu->_birthday =(MyDate){1983,12,12};//直接赋值，并强转；
// 第二种：先定义，然后在赋值
MyDate d1 = {1981,11,11}; //定义结构体变量的同时进行初始化     
stu->_birthday = d1;
// 第三种方法，逐个赋值
stu->_birthday.year = 2014;  
stu->_birthday.month = 12;  
stu->_birthday.day = 11;
