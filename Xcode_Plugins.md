#Xcode配置
##参数设置
- 空格缩进

	```
	在 XCode -> Preferences -> Text Editing -> Indentation 中进行如下设置：
	Prefer indent using: 选择 Spaces
	Tab key：选择 Intents in leading whitespace
	所有需要填写空格数目的地方都设置成4个
	```
		
	设置成4个，是因为Xcode的默认缩进是4个空格。大量遗留代码也都是采用的缩进4个空格。

- 每行代码的长度

	```
	勾选XCode->Preferences->Text Editing->Editing，并将长度设置成100个字符来打开行宽指示。
	```
	Google倡导的每行80个字符有点少，会带来更频繁的换行，因此增加到100个字符。

##插件管理
使用[Alcatraz](https://github.com/supermarin/Alcatraz)插件来管理其他插件

- 安装Alcatraz


```
 curl -fsSL https://raw.github.com/supermarin/Alcatraz/master/Scripts/install.sh | sh
```

- 卸载Alcatraz

```
 rm -rf ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins/Alcatraz.xcplugin
 rm -rf ~/Library/Application\ Support/Alcatraz/
```
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