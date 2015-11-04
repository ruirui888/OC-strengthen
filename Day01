Day01

import和include的区别:

import可以防止头文件的重复包含
include不能防止头文件重复包含

以前在C语言中,#include关于重复包含问题
使用条件编译指令可以防止头文件的重复包含

#ifndef C7________xxx_h
#define C7________xxx_h


#endif
foundation.h引入了,等于把OC的库文件都引入过来了
类库地址: /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/System/Library/Frameworks/

1)#import <foundation>, 告诉编译器找到并处理名为Foundation.h文件,这是一 个系统文件,#import表示将该文件的信息导入到程序中。</foundation>

在C和C++中采用#include指令,在本例中也可以采用#include,而#import是#include改进指令,它 可以防止头文件重复包含问题。

main函数讲解

2)int main(int argc, const char * argv[]),这个方法是程序的入口。参数argc-参数数 目,argv-参数值。

3)@autoreleasepool{ }这是一个自动释放池,用于回收对象的存储空间

4)NSLog是Foundation框架提供的Objective-C日志输出函数,与标准C中的printf函数类似,并可 以格式化输出。 @“Hello, World!”,是代表NSString字符串对象,它是Objective-C常用的字符串类。

5)最后是return 0语句,它表示要终止main的执行,一般情况下0代表正常结束,非0代表异常情况, 这是沿用了C语言的习惯。

打印字符串使用%s NSString创建的字符串 是一个对象,打印需要使用%@

NSLog 和printf的区别：

1，NSLog可以自动换行, 输出调试信息, printf不能. 2，NSLog 函数的参数是一个NSString 对象 3，printf函数的参数是一个字符串常量指针

NS -- > NeXT softWare

@符号的含义：

1，@“” 将双引号的C字符串转换为OC的字符串对象NString; 2，OC中的一个特有标示符，很多关键字前面都加@。

语言特点

源文件对比:

1，C中常见的源文件有.c 和 .h ； 2，OC中常见的源文件有.h 和 .m ;

基本语法对比:

1，数据类型对比： 首先OC兼容C中的所有数据类型； OC新增了boolean类型、block类型、对象类型、特殊类型SEL和nil 等； 另外，C中不兼容OC中新增的类型；

流程控制语句对比；

首先OC兼容了C中所有的流程控制语句；
OC又新增了自己的for in 增强型的循环语句；
//OC中的增强型for循环

for(NSString *str in arr){
    NSLog(@"%@",str);
}
函数和方法定义声明的对比；

//C语言中函数的声明和实现

函数声明: int sum(int a,int b);

函数定义 int sum(int a,int b){ return a+b; }

//OC语言中函数习惯称之为“方法”

方法声明: -(int)sum:(int) a and:(int) b;

方法定义 -(int)sum:(int) a and:(int )b{ return a+b; }

boolean 底层的设计是 无符号的char 取值为 true和false BOOL 取值 YES为真 NO为假

面向对象思想

面向过程和面向对象，都是人们在采用不同的方法来认识和描述这个世界，是认识世界的不同角度。 对象为处理复杂性问题提供了一种新的方式。

在面向过程的眼中，世界的一切都不是孤立的，它们相互紧密联系在一起，缺一不可，相互影响，相互作用并形成一个个具有严格因果律的小系统，而更多的小系统组成了更大的系统，这些系统构成了世界运行的过程。

在面向对象看来这个世界的本质是由对象组成的，平时看上去相互无关的独立对象在不同的驱动力和规则下体现出不同的运动过程，然而这些过程便展现出了我们这个生动的世界。

面向对象和面向过程并不是对立的两种方法，可以说面向对象是包含面向过程，比面向过程更加抽象的一种方法。

面向过程分析方法主要是描述一个流程，找到过程的起点，然后顺藤摸瓜，分析每一个部分，直至达到过程的终点

面向对象设计三个主要特征:

封装，继承，多态

类和对象

什么是类？

通俗一点讲就是 将具有相同属性和行为的实体的向上抽象。
比如：将男人，女人，向上抽象为一类，即为 人；Person类； 将狗，猫，老虎等动物向上抽象为一类，即为动物的类；Animal类等；

什么是对象？

即指现实世界中各种各样的实体。它可以指具体的事物也可以指抽象的事物。

类 --实例化---> 对象(属性,方法)

类和对象的抽象关系：
类和对象是分不开的；
每个对象，一定有自己所属的类；
每个类，一定有自己对应的实例；

类由对象的抽象而来；
对象由类的具体实例而来；

类的成员组成及访问

组成:
成员变量（属性）
成员方法（行为）

成员变量/实例变量/属性

//类的声明
@interface <#class name#> : <#superclass#>
{
    //类的属性
}

    //类的行为  -->  方法(声明)

@end

//类的实现
@implementation <#class#>

<#methods#>  //方法进行实现

@end
对象存储细节

当创建一个对象的时候

Person *p1 = [Person new]，做了三件事情：

向计算机申请内存空间;(栈区)
给实例变量初始化;
返回所申请空间的首地址;
成员访问

前提：成员变量需要用@public修饰符修饰；
(先记住需要用@public修饰)

Car *car1=[Car new];
car1->lunzi = 3; // 使用->来访问；

//方法访问:
Car *car = [Car new];
[car run];

-(void)run; -->   对象方法  由  对象调用
[car run];

+(void)fly  -->   类方法   由   类调用
[Car fly];
