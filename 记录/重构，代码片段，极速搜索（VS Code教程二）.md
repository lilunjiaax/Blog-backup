### 快速修复和重构
- 参数预览：查看某个函数有哪些参数，光标在函数括号内，按下：Ctrl + Shift + Space即可预览参数![参数预览](http://jvlunl.xyz/upload/2019/12/%E5%8F%82%E6%95%B0%E9%A2%84%E8%A7%88-06f802ddaacf4436979c8753cf9c35a1.png)
- 重构：想修改一个函数或者变量的名字时候，我们只需把光标放到函数或者变量名上，然后按下 F2，就可以修改多处
## 代码片段（code snippet）
> 代码片段是对常用代码的一个抽象，它保留了大部分不变的代码，然后把需要经常变动的部分，换成变量，这样等下次调用它的时候，只需要把这些变量换成我们需要的就可以了。
- 查看代码片段情况：Ctrl+Shift+P ，然后输入Configure User Snippets来查看配置用户代码片段![代码片段1](http://jvlunl.xyz/upload/2019/12/%E4%BB%A3%E7%A0%81%E7%89%87%E6%AE%B51-31405e5061d44870a1172d602033bc10.png)
- 代码片段示例如下：
```javascript
"Print to console": {
	"prefix": "log",
	"body": [
		"console.log('$1');",
		"$2"
	],
	"description": "Log output to console"
}
```
&emsp;&emsp;一个代码片段必须包含"prefix"和"body"两个字段，"description"是可选的。“prefix” 的作用是，当我们在编辑器里打出跟 “prefix” 一样的字符时，我们就能在建议列表里看到这个代码片段的选项，然后我们按下 Tab 键，就能够将这个代码片段的 “body” 里面的内容插入到编辑器里。如果这个代码片段有 “description” 这个属性的话，那么我们还能够在建议列表的快速查看窗口里看到这段“description”。

- 使用方法：当输入 "log" 时，会自动有描述提示，提示内容是"description"的value值，然后直接 Tab 就可以。
- Tab Stop："body"里面的 $1 , $2 就是Tab Stop，意思是，当我们按下 Tab 键之后，光标移动到的位置。当这段代码片段被插入到编辑器后，编辑器会把光标移动到$1所在的位置，然后如果你再按一次 Tab 键，光标则会立刻移动到 $2的位置。Tab 是移动到下一个位置，Shift+Tab是移动到**上一个**位置

### 代码折叠
- VS Code 通过对花括号的匹配来决定哪些代码块是能够被折叠
- 折叠光标所在代码段的最内层，Ctrl+Shift+**左方括号**
- 展开光标所在代码段的最内层，Ctrl+Shift+**右方括号**
- 关于递归和多层级折叠展开问题，试过之后发现不是很有好
- **按语义折叠**：之前的折叠方法只是依赖大括号，语义折叠可以自定义折叠区域，利用region标签可以实现较好的折叠。例：
```java
import java.lang.*;
public class Main {
    // region Main
    public static void main(String[] args) {
        System.out.println("hahha");
    }
    // endregion
}
```
![语义折叠](http://jvlunl.xyz/upload/2019/12/%E8%AF%AD%E4%B9%89%E6%8A%98%E5%8F%A0-da381f81d500481b967cd223fa339543.png)
## 代码搜索
- 单文件搜索：Ctrl + F，然后可以Enter和Shift+Enter进行切换对象
- 单文件搜索：光标停留在要搜索的单词上，按下F3即可唤出搜索框（且此word已在搜索框中），按F3向下跳，Shift+F3向上跳
- 搜索框选项，![搜索框选项](http://jvlunl.xyz/upload/2019/12/%E6%90%9C%E7%B4%A2%E6%A1%86%E9%80%89%E9%A1%B9-e8cd2799447e47deb389a54cb0f96f1f.png)
&emsp;&emsp;1. Aa，表示区分大小写，vscode默认是不区分大小写的，快捷键是Alt+C
&emsp;&emsp;2. Ab|，表示全单词匹配，快捷键是Alt+W
&emsp;&emsp;3. .* 表示正则匹配，快捷键是Alt+R，注意正则表达式使用的是 JavaScript 的正则引擎。
&emsp;&emsp;4. 这三个功能的快捷键的配置，它们分别使用了 Case、Word 和 Regular Expression 的第一个字母作为快捷键的一部分
&emsp;&emsp;5. 在搜索窗口关闭按钮的左侧，有一个特别的图标，表示可以在选中的文本中进行查找，先选中一段文本，然后Ctrl+F就可以查找文本

## 代码替换