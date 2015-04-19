#开发小贴士和技巧
##初始化
###类初始化
在 initialize 类方法中,能够编写实现一些延迟执行且只被一次的代码,initialize 类方法是由运行时系统在该类响应任何其他消息之前调用的。典型的应用是在其中设置类的版本信息。运行时系统向每个类发送initialize 消息,即使该类没有实现 initialize,也会调用其基类的某个 initialize 方法。因此一个类的initialize 方法可能会因为存在继承类的缘故被执行多次。因此有必要使用一定的技巧来防止只执行一次的代码被多次执行。比如使用 dispatch_once()：
```
+ (void)initialize {    static dispatch_once_t onceToken = 0;    dispatch_once(&onceToken, ^{        // the initializing code    }}```
注意:因为运行时会发送initialize 给每个类，所以子类有可能调用initialize。如果子类没有实现initialize，那么将结束在父类调用中。如果你特别需要在相关类中执行initialize方法，那可以使用下面的方法，而不是dispatch_once:
```
if (self == [NSFoo class]) {    // the initializing code}```
不应当显式调用 initialize 方法。如果你需要激活 initialize 方法,使用 [NSImage self] 形式的调用。