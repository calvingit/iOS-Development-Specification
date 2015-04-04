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
