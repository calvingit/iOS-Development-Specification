#方法命名

##一般性原则
为方法命名时,请考虑如下一些一般性规则:
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
- (id)initWithFrame:(CGRect)frameRect;//NSView, UIView.- (id)initWithFrame:(NSRect)frameRect mode:(int)aMode  cellClass:(Class)factoryId numberOfRows:(int)rowsHigh numberOfColumns (int)colsWide;//NSMatrix, a subclass of NSView
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

* 如果属性是用名词描述的,则命名格式为:```- (void) setNoun:(type)aNoun;- (type) noun;
```例如:```- (void) setgColor:(NSColor *)aColor;
- (NSColor *) color;```* 如果属性是用形容词描述的,则命名格式为: 

```- (void) setAdjective:(BOOL)flag;- (BOOL) isAdjective;```例如:
```- (void) setEditable:(BOOL)flag;
- (BOOL) isEditable;
```
* 如果属性是用动词描述的,则命名格式为:(动词要用现在时时态) 

```
- (void) setVerbObject:(BOOL)flag;- (BOOL) verbObject;
```
例如:
```- (void) setShowAlpha:(BOOL)flag; 
- (BOOL) showsAlpha;
```


