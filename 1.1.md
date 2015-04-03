# 一般原则

####清晰性
* 最好是既清晰又简短,但不要为简短而丧失清晰性

| 代码 | 点评 |
| -- | -- |
| insertObject: atIndex: | 好 |
| insert: at: | 不清晰：要插入什么？“at”表示什么？|
| removeObjectAtIndex: | 好 |
| removeObject:| 这样也不错,因为方法是移除作为参数的对象 |
| remove: | 不清晰：要移除什么? |

* 名称通常不缩写,即使名称很长,也要拼写完全（禁止拼音！！！）

| 代码 | 点评 |
| -- | -- |
| destinationSelection: | 好 |
| destSel: | 不好|
| setBackgroundColor: | 好 |
| setBkgdColor:| 不好 |

你可能会认为某个缩写广为人知,但有可能并非如此,尤其是当你的代码被来自不同文化和语言背景的开发人员所使用时。

* 然而,你可以使用少数非常常见,历史悠久的缩写。请参考“[可接受的缩略名](#)”一节

* 避免使用有歧义的 API 名称,如那些能被理解成多种意思的方法名称

| 代码 | 点评 |
| -- | -- |
| sendPort: | 是发送端口还是返回一个发送端口？ |
| displayName: | 是显示一个名称还是返回用户界面中控件的标题？ |

####一致性
* 尽可能使用与Cocoa编程接口命名保持一致的名称。如果你不太确定某个命名的一致性，请浏览一下头文件或参考文档中的范例。
* 在使用多态方法的类中，命名的一致性非常重要，在不同类中实现相同功能的方法应该具有相同的名称。

| 代码 | 点评 |
| -- | -- |
| - (int) tag | 在 NSView，NSCell，NSControl 中有定义 |
| - (void)setStringValue:(NSString *) | 在许多Cocoa类中有定义 |
更多请看 [函数参数](#)


#前缀

通常，软件会被打包成一个框架或多个紧密相关的框架(如 Foundation 和 Application Kit 框架)。但由于Cocoa没有像C++一样的命名空间概念，所以我们只能用前缀来区分软件的功能范畴，防止命名冲突。

* 类名和常量应该始终使用三个字母的前缀（例如 NYT），因为两个字母的前缀是苹果SDK先使用的，但 Core Data 实体名称可以省略。为了代码清晰，常量应该使用相关类的名字作为前缀并使用驼峰命名法。

下面是常见的苹果官方的前缀
 
| 前缀 | Cocoa 框架 |
| -- | -- |
| NS | Foundation |
| NS | Application Kit |
| AB | Address Book |
| IB | Interface Builder|

比如在我们的APP中蓝牙模块（Bluetooth low energy）管理类  
```objective-c
@interface BLEManager : NSObject
@property (assign) BLEDeviceType deviceType;
@end
```
#书写约定
在为 API 元素命名时,请遵循如下一些简单的书写约定
* 对于包含多个单词的名称,不要使用标点符号作为名称的一部分或作为分隔符(下划线,破折号等);
  此外,大写每个单词的首字符并将这些单词连续拼写在一起。请注意以下限制:

 * 方法名小写第一个单词的首字符,大写后续所有单词的首字符。方法名不使用前缀。如: fileExistsAtPath:isDirectory: 如果方法名以一个广为人知的大写首字母缩略词开头,该规则不适 用,如:NSImage 中的 TIFFRepresentation
 * 函数名和常量名使用与其关联类相同的前缀,并且要大写前缀后面所有单词的首字符。如: NSRunAlertPanel，NSCellDisabled
 * 避免使用下划线来表示名称的私有属性。苹果公司保留该方式的使用。如果第三方这样使用可能会导致命名冲突,他们可能会在无意中用自己的方法覆盖掉已有的私有方法,这会导致严重的后 果。请参考“[私有方法](#)”一节以了解私有 API 的命名约定的建议

