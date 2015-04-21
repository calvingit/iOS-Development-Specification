#方法命名

##一般性原则
为方法命名时,请考虑如下一些一般性规则:

* **方法名不要使用 `new` 作为前缀。**
* 小写第一个单词的首字符,大写随后单词的首字符,不使用前缀。请参考“书写约定”一节。有两种例 外情况:1,方法名以广为人知的大写字母缩略词(如 TIFF or PDF)开头;2,私有方法可以使用统一的前缀来分组和辨识,请参考“私有方法”一节
* 表示对象行为的方法,名称以动词开头:

```
- (void) invokeWithTarget:(id)target:
- (void) selectTabViewItem:(NSTableViewItem *)tableViewItem
```

名称中不要出现 do或does,因为这些助动词没什么实际意义。也不要在动词前使用副词或形容词修饰。

* 如果方法返回方法接收者的某个属性,直接用属性名称命名。不要使用 get，除非是间接返回一个或多个值。请参考“访问方法”一节。

| 代码 | 点评 |
|--|--|
| - (NSSize) cellSize; | 对 |
| - (NSSize) calcCellSize; | 错 |
| - (NSSize) getCellSize;| 错 |

* 参数要用描述该参数的关键字命名

| 代码 | 点评 |
|--|--|
|- (void) sendAction:(SEL)aSelector to:(id)anObject forAllCells:(BOOL)flag;|对 |
| - (void) sendAction:(SEL)aSelector  :(id)anObject  :(BOOL)flag; | 错 |

* 参数前面的单词要能描述该参数。 

| 代码 | 点评 |
|--|--|
| - (id) viewWithTag:(int)aTag;  | 对 |
| - (id) taggedView:(int)aTag; | 错 |

* 细化基类中的已有方法:创建一个新方法,其名称是在被细化方法名称后面追加参数关键词

```
- (id)initWithFrame:(CGRect)frameRect;//NSView, UIView.
```
* 不要使用 and 来连接用属性作参数的关键字

| 代码 | 点评 |
|--|--|
| - (int)runModalForDirectory:(NSString *)path file:(NSString *)name types:(NSArray *)fileTypes; | 对 |
|- (int)runModalForDirectory:(NSString *)path andFile:(NSString *)name andTypes:(NSArray *)fileTypes;| 错 |

虽然上面的例子中使用 add 看起来也不错,但当你方法有太多参数关键字时就有问题。

* 如果方法描述两种独立的行为,使用 and 来串接它们

```
- (BOOL) openFile:(NSString *)fullPath withApplication:(NSString NSWorkspace *)appName andDeactivate:(BOOL)flag;//NSWorkspace.
```

#访问方法
访问方法是对象属性的读取与设置方法。其命名有特定的格式依赖于属性的描述内容。

* 如果属性是用名词描述的,则命名格式为:
```
- (NSColor *) color;

```

- (BOOL) isEditable;
```


```
- (void) setVerbObject:(BOOL)flag;
```


- (BOOL) showsAlpha;
```
* 不要使用动词的过去分词形式作形容词使用

```
* 可以使用情态动词(can, should, will 等)来提高清晰性,但不要使用 do 或 does

```
- (void) setCanHide:(BOOL)flag;             //对
- (void) setDoseAcceptGlyphInfo:(BOOL)flag; //错 
- (BOOL) doseAcceptGlyphInfo;               //错
```
* 只有在方法需要间接返回多个值的情况下,才使用 get

```
- (void) getLineDash:(float *)pattern count:(int *)count phase:(float *)phase;  //NSBezierPath
```
像上面这样的方法,在其实现里应允许接受 NULL 作为其 in/out 参数,以表示调用者对一个或多个返回 值不感兴趣。

#委托方法
委托方法是那些在特定事件发生时可被对象调用,并声明在对象的委托类中的方法。它们有独特的命名约

```
```

* 冒号紧跟在类名之后(随后的那个参数表示委派的对象)。该规则不适用于只有一个 sender 参数的方法

```

* 上面的那条规则也不适用于响应通知的方法。在这种情况下,方法的唯一参数表示通知对象

```
- (void) windowDidChangeScreen:(NSNotification *)notification;
```

* 用于通知委托对象操作即将发生或已经发生的方法名中要使用 did 或 will 

```
- (void) browserDidScroll:(NSBrowser *)sender;
```




- (NSArray *)elements;
- (NSArray *)layoutManagers;


- (void) removeElementAtIndex:(int)index;
```
集合方法的实现要考虑如下细节:
* 当被插入的对象需要持有指向集合对象的指针时,通常使用 set... 来命名其设置该指针的方法,且不 要 retain 集合对象。比如上面的 insertLayerManager:atIndex: 这种情形,NSLayoutManager 类使 用如下方法:

```
- (void) setTextStorage:(NSTextStorage *)textStorage; 
- (NSTextStorage *)textStorage;
```
通常你不会直接调用 setTextStorage:,而是覆写它。

```
- (void) addChildWindow:(NSWindow *)childWin ordered:(NSWindowOrderingMode)place;
- (void) removeChildWindow:(NSWindow *)childWin;
```
#方法参数
命名方法参数时要考虑如下规则:

...action:(SEL)aSelector 
..alignment:(int)mode 
...atIndex:(int)index 
...content:(NSRect)aRect 
...doubleValue:(double)aDouble 
...floatValue:(float)aFloat 
...font:(NSFont *)fontObj 
...frame:(NSRect)frameRect 
...intValue:(int)anInt
...keyEquivalent:(NSString *)charCode




