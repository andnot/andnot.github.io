---
layout: post
title: LyX Tips
category: research
---


## 数学

- 快捷键`Ctrl+M`进入数学公式编辑环境（该快捷键也可将选中的文本直接转化为公式样式），`Ctrl+Shift+M`可在行内公式和独行公式之间切换；按反斜杠键`\`后输入TeX代码可以快速输入各种数学符号或算符（如连积运算`\prod`）。

- 如果要转录 MathType 中的公式，需要在MathType的「剪切和复制选项」中选中「转换其他文字（AMSLaTeX）」，同时下面两个复选框留空，这样就可以直接复制出 latex 代码；在LyX中只需选中粘贴的代码，按`Ctrl+M`快捷键即可转换为公式。

- 数学公式环境：`Ctrl+space`，出现一个间隔，此时连按`space`，会在不同间隔长度间切换；`Ctrl+Alt+space`直接插入一个词间空格。

- 数学变量的粗体（如向量、矩阵）应使用`\boldsymbol`环境，快捷键为`Ctrl+Alt+B`。

	- `\bm`也可输入粗体数学符号，不过需要加载「bm」包；
	- 尽量不要使用快捷键`Ctrl+B`，它会生成`\mathbf`环境，这不是数学变量的显示格式，此外还有可能会出现大写希腊字母无法显示的问题。

- 斜体大写希腊字母在前面加`var`，如`\varGamma`（需要amsmath宏包）。

- 多行公式，快捷键`Ctrl+Enter`进入下一行进行编辑。

- 按`Alt+M，N`可以快速插入公式编号，按`Alt+M，Shift+N`可仅对当前行插入编号。

- 多行公式整体编号，菜单插入「Split环境」，或手动在公式环境里前后插入TeX代码（快捷键`Ctrl+L`）：`\begin{split}`以及`\end{split}`。

- 多行公式添加子公式编号，手动在公式环境前后中插入TeX代码：`\begin{subequations}`以及`\end{subequations}`；也可在subequations环境前面加入`\addtocounter{equation}{-1}`代码使得子公式紧跟上一个公式编号。

- 插入-「公式」-「宏」，可以自动化输入复杂公式；注意公式名字不要加数字。

- 替换公式中的内容，需要使用「高级查找替换」（快捷键`Ctrl+Shift+F`），并且在替换窗口中按`Ctrl+M`建立数学环境，之后才能完成替换（另外建议勾选「区分大小写」）。详见：<http://www.lyx.org/trac/ticket/9028>。

	- 在「高级查找替换」的「设置」选项卡中选上「Search only in maths」，则可以仅仅在数学公式中查找/替换（还要选上「Ignore format」）。

- 自定义数学算子，可使用`\mathop{}`命令。

- 当打开数学公式的「即时预览」功能后，若某个公式不能在编辑器中渲染显示（其余公式可以渲染显示），则其也无法编译PDF，这可以作为检查TeX公式是否能输出到PDF的方法。

---

## 其他

- 标题提升等级要由后向前，降低等级则要由前向后。

- article文档类没有`\chapter`环境，只有book和report才有。

- 「编辑」-「粘贴最近」，可以选择粘贴最近几次的复制或剪贴内容。

- 插入的任何对象（图片、BiBTeX文件等）的路径不要含有空格或括号等多余字符，否则导出的LaTeX代码将无法成功编译。

- 文件名尽量不要含有中文，因为Windows文件编码系统不是UTF-8，故基于UTF-8编码的XeTeX套件（包括TeXWorks）可能会出错。

- LyX文件名不要含有特殊字符，否则有可能无法编译PDF。

- 「带名称的定理」环境需要插入TeX代码[定理name]来显示名称。

- 按定理、定义等类别不同编号的定理应选用「Theorems (AMS, Numbered by Type)」包。

- 注意LyX界面输入引号后会进行转译，""会变成“”，此时直接复制LyX界面中的引号到另一个程序，可能会出现乱码，这也许是LyX「所见即所想」特性的一个副作用；若要输出不弯曲的双引号，则需键入`\textquotedbl`；也可从一个文本编辑器中（或更简单地直接从LyX的TeX环境中）复制已有的引号过来；或者在使用`fontenc`宏包（`\usepackage[T1]{fontenc}`）的前提下直接在TeX环境中键入`"`。详见：<http://tex.stackexchange.com/questions/223070/how-can-i-input-normal-quotes-in-lyx>。

- BiBTeX题录信息中不可出现中文引号。

- 若需要按照「作者-年份」显示参考文献，则在「参考书目」选项卡中选取「Natbib」并设置相应的Natbib风格；「Default style」中填上 plainnat；处理程序选为「bibtex」。

- BiBTeX导入Noteexpress使用时，注意条目间须有空行，可以在notepad++中替换`}\n@`为`}\n\n@`；导出BiBTeX时可设为「UTF-8 without BOM」。

- 学术文档通常要求三线表格，LaTeX中需要调用`booktabs`包，而LyX可以自动载入，只要在表格设置的「边框」选项卡中选择「正式」样式即可，三线表格的具体形式也可在此进行细调。

- 若希望插入算法列表，导言区需要加入`\usepackage{algorithm}`以及`\usepackage{algorithmic}`，正文需要插入TeX代码，并按照algorithm包的写法输入；一个简便的方法是先在LyX中以普通列表形式写好算法，然后在对应的TeX源码中将所有的`\item`都替换为`\STATE`（注意每个字母都大写），再添上算法标题、标签等即可；尽量避免使用LyX自定义的「算法」环境，以减少非标准TeX代码的产生。若需要更改algorithm列表的字体大小，则在`\begin{algorithm}`语句后添加`\algsetup{linenosize=\tiny} 	\scriptsize`，其中参数`tiny`也可更换为其他字体大小。

- 双栏插图可以在浮动图首选项中设为「跨列」，若两幅图并列可设为「文本宽度」的45%。

- 非跨列插图最好以页宽为基准，毕竟大多数时候页面宽度变化不大（以A4和letter为主），而文本宽度则会随不同模板有较大改变；列宽和行宽也尽量少用。

- 插图按章节编号，在导言区加入`\numberwithin{figure}{section}`

- 若使用pafLaTeX编译，导言区需要加入`\usepackage{epstopdf}`，否则eps插图不能正确显示。

- 中英文混合编辑时，尽量使用CTeX文档类，并调用XeTeX输出PDF，这样可以保证中文和英文之间自动加上空格。

- 有时候编译错误，报错信息中出现`\selectlanguage`字样或乱码，这种情况往往是由于文本的语言属性不同导致。由于LyX正文界面看上去是正常的（仅仅在文档TeX源码中会出现`\selectlanguage`之类的内容），因此这个问题相当隐蔽。这种情况多发生在从其他LyX文档复制内容，当两文档语言属性不同时（比如两个文档分别为英文和中文），就会出错。解决方法是，先将内容复制到一个空白文档内，然后在「文档」首选项中「语言」选项内调整为目标文档的语言后，再复制到目标文档。正常情况下，复制过去的文本不会显示多余的下划线。

- 某些投稿系统支持Postscript文件格式，可通过以下方式获得（在cmd环境下操作）： `latex <filename>.tex` 可以得到对应的dvi文件，再输入  `dvips <filename>.dvi` 就可以得到ps文件了；有参考文献的情况下需要加上BibTeX编译（`bibtex <filename>`，注意只有文件名，不带后缀）；通常以上几条命令应按如下顺序进行：`latex` -> `bibtex` -> `latex` -> `latex` -> `dvips`，其中紧跟bibtex的两条latex命令用来处理参考文献和文档中的交叉引用。

- 对于字体无法嵌入问题，可以用Ghostscript转换，例如：
`"C:\Program Files (x86)\gs\gs9.14\bin\gswin32c" -dSAFER -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dPDFSETTINGS=/printer -dCOMPatibilityLevel=1.4 -dMaxSubsetPct=100 -dSubsetFonts=true -dEmbedAllFonts=true -sOutputFile=<filename>.pdf <filename>.ps`

    - 若需要改变纸张尺寸，可加入PAPERSIZE命令，如`-sPAPERSIZE=letter `；
	- 如果安装的Ghostscript是64位版本，则目录应改为「Program Files」，例如`"C:\Program Files\gs\gs9.16\bin\gswin64c"`。

---

> P.S. 
LyX的中文配置可参考我写的另一篇博文（不定期更新）：<http://andnot.github.io/LyX中文配置Tips>。


