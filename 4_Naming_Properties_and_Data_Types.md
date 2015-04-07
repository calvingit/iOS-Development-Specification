#属性与数据类型命名
这一节描述属性，实例变量，常量，异常以及通知的命名约定。

##属性声明与实例变量
属性声明的命名大体上和访问方法的命名是一致的。假如属性是动词或名词，格式如下

```
@property (...) typenounOrVerb;
```
例如：

```
@property (strong) NSString *title;@property (assign) BOOL showsAlpha;
```
如果属性是形容词，名字去掉"is"前缀，但是要特别说明一下符合规范的get访问方法，例如

```
@property (assign, getter=isEditable) BOOL editable;
```
多数情况下，你声明了一个属性，那么就会自动生成对应的实例变量。

确保实例变量名简明扼要地描述了它所代表的属性。通常，你应该使用访问方法，而不是直接访问实例变量（除了在init或者dealloc方法里）。为了便于标识实例变量，在名字前面加个下划线"_"，例如:

```
@implementation MyClass {    BOOL _showsTitle;}
```

在为类添加实例变量是要注意:

* 避免创建 public 实例变量
* 使用 @private,@protected 显式限定实例变量的访问权限
* 如果实例变量别设计为可被访问的,确保编写了访问方法

##常量
常量命名规则根据常量创建的方式不同而大不同。
###枚举常量
