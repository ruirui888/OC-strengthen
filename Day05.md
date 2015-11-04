Day05

多态

多态概念，定义

什么是多态:
多态就是某一类事物的多种形态；
表现形式：
Animal *ani = [Dog new];
多态条件：
1.有继承关系
2.有方法的重写
多态代码实现：

//实例化猫的对象
Animal *animal  = [Cat new]; //父类的指针指向子类对象；
[animal eat];
实例化狗的对象

animal = [Dog new]; //父类的指针指向子类对象。
[animal eat];
多态注意点：

1) 如果存在多态,父类是可以访问子类特有的方法
假设子类Dog 有一个特有的方法bark
Animal *an2 = [Dog new];//编译时看等号左边，运行时看等号右边
[(Dog*)an2 bark]; //把父类的指针,强制类型转换
2) 如果不存在多态,父类是不可以访问子类特有的方法的
Animal *an3 = [Animal new];
[(Dog*)an3 bark]; //错误的,不能强制转换
类对象

1，类的本质其实也是一个对象(类对象)；
类对象

类对象在程序运行时一直存在。
类对象是一种数据结构,存储类的基本信息:类大小,类名称,类的版本以及消息与函数的映射表等
每一个对象都包含一个指向其类对象的isa指针。
2、类对象如何获取

通过实例对象获取
Dog *d1 = [Dog new];
Dog *d2 = [Dog new];
Class c =   [d1 class];
Class c2 = [d2 class];
通过类名获取(类名其实就是类对象)
Class c3 = [ Dog  class ];
因为类对象在整个程序中只存在一份， 所以 c = c2 = c3
3.类对象的使用

1)可以用来调用类方法 ：
//获取类对象
Class c1 = [Person class];
//使用类对象调用类方法
[c1 test]; // test是一个+号方法
2)可以用来实例化实例对象， 并且调用对象方法
//获取类对象
Class c1 = [Person class];
//使用类对象创建实例对象
Person *p = [c1 new];
[p test];  // -test 调用对象方法

类对象只能使用在等号右边
类对象存储细节
通过打印地址分析测试：类对象存在数据段；

5.SEL类型
SEL是一种新的数据类型。和id、class一样。

Person *p = [Person new];
SEL s1 = @selector(test);
[p performSelector:s1];
点语法

传统setter, getter方法
-(void)setAge:(int)age{
    _age = age;
}

-(int)age{
    return _age;
}
点语法
本质上展开之后相当于调用setter, getter方法
p.age = 10;  展开之后等价于   [p setAge:10];  // setter方法

NSString *name = p.age; 等价于NSString *name = [p name]; // getter方法
对象. 成员变量  展开之后到底是setter方法, 还是getter方法, 看在等号的左边还是右边,
如果是等号左边就是setter方法, 在等号右边是getter方法
点语法陷阱 ：
//在set方法使用self.
- (void)setAge:(int)newAge {
    self.age = newAge;
}
点语法注意
点语法的本质是方法的调用,而不是访问成员变量,当使用点语法时,编译器会自动展开成相应的方法。
切记点语法的本质是转换成相应的set和get方法,如果没有set和get方法,则不能使用点语 法。
四.@property&@synthesize

@property的语法：
使用:
@property int age;

@property特性:

1，@property只能写在@interface @end中。

2，@property 用来自动生成成员变量age的get/set方法声明(xcode4.4以前) 。

3，xcode4.4以后property做了增强 不但帮助我们自动生成get/set方法的声明还帮助我们自动生成get/set方法的实现 。

4，告诉编译器，要生成的get/set方法声明的成员变量类型是int 。

5，如果没有手动声明成员变量,perperty会在.m文件中自动帮我们生成一个开头的成员变量

@synthesize用法:

@synthesize age; 表示生成.h中变量age的get和set方法的实现
@synthesize 给指定的实例变量赋值。 @synthesize age = _age;
注意;
如果是@synthesize的话， 变量名要先在.h文件中声明。
@property，@synthesize这两个可以配合使用，用于简化set和get方法的定义和实现。

重写setter, getter方法: 只能重写setter, 或者getter方法中的一个 如果重写两个会报错.

动态类型

动态类型: 运行的时候确定的类型

动态绑定： 动态绑定是基于动态类型的：
基于动态类型，在某个实例对象被确定后，其类型便被确定了。该对象对应的属性和响应的消息也被完全确定，这就是动态绑定。
动态绑定所做的，即是在实例所属类确定后，将某些属性和相应的方法绑定到实例上。

动态加载：
动态创建类Class,动态添加Class成员变量与成员函数,动态变量赋值与取值，动态函数调用等;

内省（Introspection）是面向对象语言和环境的一个强大特性，Objective-C和Cocoa在这个方面尤其的丰富。 内省是对象揭示自己作为一个运行时对象的详细信息的一种能力。这些详细信息包括对象在继承树上的位置，对象是否遵循特定的协议，以及是否可以响应特定的消息。

1、isKindOfClass:Class
判断实例对象是否是这个类或者这个类的子类的实 例。

2、isMemberOfClass:Class
判断是否是这个类的实例。

3、+(BOOL) isSubclassOfClass:classObj
判断类是否是指定类的子类。

4、respondToSelector:selector
确定对象是否可以对某个SEL做出响应

5、+(BOOL) instancesRespondToSelector:
判断类是否有这个方法。此方法是类方法, 不能用在类的对象

6、conformsToProtocol:protocol
检查对象是否符合协议，是否实现了协议中所有的必选方法。
