Day06

id和instancetype类型区别

id和instancetype都可以用来作为方法的返回值

id可以用来定义类型,instancetype不能用来定义类型 id obj; instancetype obj2; // 错误

instancetype可以精确返回值类型

动态类型检测

判断某个对象是否是类的实例对象，或者子类的实例对象（对象和类） isKindOfClass使用格式：[对象 isKindOfClass 类对象];
BOOL isInstance = [ani isKindOfClass:[Animal class]];

isMemberOfClass 判断对象是否是指定类的实例对象（对象和类） 格式： [对象 isMemberOfClass: 类对象] BOOL isInstance = [dog isMemberOfClass:[Animal class]];
3、判断类是否是指定类的子类(类和类之间的关系) 格式： [类A isSubclassOfClass:类B]; BOOL isSub = [Dog isSubclassOfClass:[Animal class]];

响应方法

Bool isInstace = [p respondsTosesector:@selector(run)]; // 没有参数 -(id) performSelector:selector(应用selector指定的方法) NSObject的方法 // 一个参数 -(id) performSelector:selector withObject:object(应用selector指定的方法,传递参数 object) // 二个参数 -(id) performSelector:selector withObject:object1 withObject:object2(应用selector指 定的方法,传递参数object1和object2)

构造方法

创建对象:Person *p=[Person new]; new方法内部做了3件事情: (1)使用alloc方法来分配存储空间(返回分配的对象); (2)使用init方法来对象进行初始化。 (3)返回对象的内存首地址。

可以把new方法拆开如下: (1).调用类方法+alloc分配存储空间,返回未经初始化的对象 Person p1=[Person alloc]; (2).调用对象方法-init进行初始化,返回对象本身 Person p2=[p1 init]; (3).以上两个过程整合为一句: Person *p=[[Person alloc] init];

(1)init方法就是构造方法,是用来初始化对象的方法,称为构造初始化。

(2) alloc 向某个类发送alloc消息的结果 ，为该类分配内存(对象的内存地址已经有了),以存放该类的全部实例变量 。

注意 一个刚刚分配的对象并不能立即使用 , 需要先初始化该对象,然后才能使用它 , 但由于未进行初始化, 随后可能出现一些不可预测的行为.

重写构造方法

[super init]的作用:先调用父类的初始化方法，对从父类继承过来的成员变量进行初始化。初始化完了之后，返回我当前的对象指针。
重写构造方法注意事项： 构造方法使用注意 (1)子类拥有的成员变量包括自己的成员变量以及从父类继承而来的成员变量,在重写构造方法的时候 应该首先对从父类继承而来的成员变量先进行初始化。 (2)原则:先初始化父类的,再初始化子类的。 (3)重写构造方法的目的:为了让对象方法一创建出来,成员变量就会有一些固定的值。 (4)注意点:先调用父类的构造方法[super init]; 再进行子类内部成员变量的初始化。
3.构造方法应用场景： 如果对象中的一些属性需要在初始化的时候就需要有值, 可以使用构造方法来完成.

自定义构造方法

自定义构造方法的规范 (1)一定是对象方法,以减号开头 (2)返回值一般是id类型或者instancetype类型 (3)方法名一般以initWith开头

自定义构造方法的实现

- (instancetype)init
{
    self = [super init];
    if (self) {
        // 要初始化的成员变量.

    }
    return self;
}
举例:

- (instancetype)initWithName:(NSString *)name andAge:(int)age;
{
    self = [super init];
    if (self) {
        // 要初始化的成员变量.
        _name = name;
        _age = age;
    }
    return self;
}
自定义构造方法的使用注意 (1). 自己做自己的事情 (2). 父类的方法交给父类的方法来处理,子类的方法处理子类自己独有的属性
使用场景 如果对象被创建的时候, 需要对里面某些属性进行初始化(设置), 这个时候就可以使用构造方法
