# Xcode之插件
虽然Xcode本身就是个大而全的玩意，用它就可以搞定所有的Mac/iOS开发工作。但是程序员的世界就是爱折腾，为了避免重复劳动，使用各种办法来提高效率，插件就是其中一种。

这里将介绍一种叫[Alcatraz](https://github.com/alcatraz/Alcatraz)Xcode插件管理软件，非常简单好用的工具，它本身也是插件。

# Alcatraz 插件管理器
![Alcatraz](https://camo.githubusercontent.com/f4106ea5018bf4beff4c8625b0f3abe528cceb7d/687474703a2f2f616c63617472617a2e696f2f696d616765732f6865616465724032782e706e67)  

## 安装
在终端输入下面命令
```
curl -fsSL https://raw.github.com/alcatraz/Alcatraz/master/Scripts/install.sh | sh
```
成功之后会给你一杯啤酒
> Alcatraz successfully installed!!1!🍻   Please restart your Xcode.

然后重启一下Xcode。就可以看到在Menu — Windows 看到`Package Manager`,打开它，然后就长这个样子

![](https://camo.githubusercontent.com/919efe4e1e53237df51d7010c862bd5c04fd6a70/687474703a2f2f616c63617472617a2e696f2f696d616765732f73637265656e73686f744032782e706e67)

里面有三种东西：Plugins(插件)，Color Themes(颜色主题)，Templates(模板)

选择你想要的东西，点击==INSTALL==按钮开始安装，完成之后会显示红色的==REMOVE==按钮。

## 卸载
打开终端粘贴下面的命令：
```
rm -rf ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins/Alcatraz.xcplugin
```

删除掉Alcatraz安装的所有插件：
```
rm -rf ~/Library/Application\ Support/Alcatraz/
```


# 常用插件

Alcatraz里面常用插件说明

| 插件 | 用途 |
| -- | -- |
| [XToDo](https://github.com/trawor/XToDo) | 注释辅助插件，主要用于收集并列出项目中的TODO,FIXME,`??? |
| [CocoaPods plugin](https://github.com/kattrali/cocoapods-xcode-plugin) | 为CocoaPods添加了一个菜单项 |
| [Peckham](https://github.com/markohlebar/Peckham) | 添加引用文件有时候非常麻烦，如果你需要引入一个pod头文件，Xcode自带的自动补全自然帮不了你，这时候你可以用Peckham插件解决这个问题。Command+Control+P解决所有的引入 |
| [FuzzyAutocomplete](https://github.com/FuzzyAutocomplete/FuzzyAutocompletePlugin) | 代替Xcode的autocomplete，它利用模式匹配算法来解决问题。 |
| [ACCodeSnippetRepository](https://github.com/acoomans/ACCodeSnippetRepositoryPlugin) | 使用它和你的Git库同步，如果你想手动导入一个Snippet需要很麻烦的步骤，通过这个插件你只需要点击几下鼠标。 |
| [XcodeColors](https://github.com/robbiehanson/XcodeColors) | 改变调试控制台颜色，这个插件配合[CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack)使用效果非常好 |
| [VVDocumenter](https://github.com/onevcat/VVDocumenter-Xcode) | 输入三个斜线“///”，自动生成规范化的注释|
| [SCXcodeMiniMap](https://github.com/stefanceriu/SCXcodeMiniMap) | 可以在当前的窗口内创建一个代码迷你地图，并在屏幕上高亮提示 |
| [XAlign](https://github.com/qfish/XAlign) | 代码对齐，Shift + Cmd + X |
| [HOStringSense](https://github.com/holtwick/HOStringSense-for-Xcode) | 经常输入大段文本的时候，如果文本里面有各种换行和特殊字符，经常会让人很头疼，有了HOStringSense，再也不不用为这个问题犯愁了，顺便附送字数统计功能。 |
| [OMColorSense](https://github.com/omz/ColorSense-for-Xcode)| 代码里的那些冷冰冰的颜色数值，到底时什么颜色？如果你经常遇到这个问题，每每不得不运行下模拟器去看看，那么这个插件绝对不容错过。更彪悍的是你甚至可以点击显示的颜色面板，直接通过系统的ColorPicker来自动生成对应颜色代码，再也不用做各种颜色代码转换了！|
| [ClangFormat](https://github.com/travisjeffery/ClangFormat-Xcode) | CLang代码格式化 |
| [CodePilot](https://github.com/macoscope/CodePilot.git) | 代码、图片、文件搜索利器，快捷键CMD + SHIFT +X |


# Xcode更新后插件不能用的解决办法
运行下面的命令
```
find ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins -name Info.plist -maxdepth 3 | xargs -I{} defaults write {} DVTPlugInCompatibilityUUIDs -array-add `defaults read /Applications/Xcode.app/Contents/Info.plist DVTPlugInCompatibilityUUID`
```
