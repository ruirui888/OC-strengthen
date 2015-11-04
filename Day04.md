Day04

文档安装和方法重载:

在线安装 xcode-> 系统偏好设置->Doucument->下载

离线安装

第三方软件:dash

方法重载: 是指在一个类中定义多个同名的方法 在OC中没有重载
static关键字:

在c语言中 static可以修饰 局部变量(延长局部变量的生命周期)、 全局变量(当前变量只能再当前文件中使用) 函数(当前函数只能再当前文件中使用)

在OC中, 不能用来修饰实例变量和方法, 但是可以修饰局部变量, 全局变量

self的理解

self和super:

self理解:自己 谁调用当前方法, self就代表谁.
super代表的是当前类的父类.
self使用在对象方法

比如: 在对象方法中,self代表的是调用当前方法的对象,只有对象才可以调用对象方法

self使用在类方法中

在类方法中, self代表的是当前类,只有类名才可以调用类方法.

//获取当前对象的类: 
Person *p = [Person new];
[p class] = [Person class] = Person
//返回当前类
self访问成员变量

在对象方法中可以通过 self->_speed访问成员变量.

注意:

在对象方法中不要使用self调用自身方法
在类方法中不要使用self调用自身方法
self调用方法

[self 方法名称]; (类方法/对象方法)

继承和派生:

//继承格式:
@interface Cat : Animal

@end
子类拥有父类的所有属性和方法

继承定义: 子类拥有了属性和方法.

派生: 父类向下产生子类的过程称为派生

派生类拥有基类的属性和方法,还有自己派生的新增的属性和方法

方法重写:把父类的方法，在子类中重新给实现了

继承的注意事项:

子类不能定义和父类同名的变量,但是可以继承父类的变量

OC类支持单一继承,不支持多继承

OC类支持多层继承

继承体系中方法调用的顺序

1、在自己类中找
2、如果没有,去父类中找
3、如果父类中没有,就去父类的父类中
4、如果父类的父类也没有,就还往上找,直到找到基类(NSObject)
5、如果NSObject都没有就报错了

实例变量修饰符:

作用范围:

@public(公开的) : 作用于所有的类
@protected(受保护的): 作用于当前类,子类(派生类)
@private(私有的): 作用于当前类
@package(框架级别的): 作用于框架级别的
私有变量&私有方法:

默认情况下实例变量属于@protected修饰.

私有变量定义格式:

在.m文件当中定义

@implementation Person : NSObject
{
    int  age;   //  私有变量
}

// 不在.h文件中声明,  只在.m文件中实现
-(void)run{

    NSLog(@"我是私有方法");
}
@end
私有方法只能在当前文件中使用, 不能被子类继承.

description方法

description方法默认返回对象的描述信息(默认实现是返回类名和对象的内存地址) ;
NSLog(@"%@", objectA);
这会自动调用objectA的descriptong方法来输出ObjectA的提述信息,
重写description方法:
-(NSString *)description{
    return [NSString stringWithFormat:@"狗腿的个数:%d,狗的眼睛个数:%d",_tuiNum, _eyeNum];
}
千万不要在description方法中同时使用%@和self
//同时使用了%@和self,代表要调用self的description方法,
//因此最终会导致程序陷入死循环,循环调用description方法
- (NSString *)description {
    return [NSString stringWithFormat:@"%@", self];
}
