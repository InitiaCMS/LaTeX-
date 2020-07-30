# LaTeX入门

### 第一章 熟悉LaTeX

### 第二章 组织你的文本

#### 2.1 文字与符号

##### 2.1.1 字斟句酌

>1、重音命令，以字母 o 为例
>
>![image-20200729092252963](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729092252963.png)



>2、LaTeX中的特殊字母
>
>![image-20200729092356431](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729092356431.png)



>3、如果要输入希腊字母和西里尔字母：
>
>```text
>\usepackage[greek,english]{babel}
>```
>
>使用英语和希腊语，其中后一个参数表示英语是默认语言，此时希腊语就可以用ASCII字符代替：
>
>```text
>\textgreek{abcde}
>```

>4、取消连字可以使用空的分组，或借用\/命令
>
>```text
>shelfful shelf{}ful shelf\/ful
>```

>5、**正确使用标点**
>
>* 引号在LaTeX中用`'和'两个符号表示。单引号用一遍，双引号用两遍。如果遇到单引号与双引号连续出现的情形，则在中间用 \, 命令分开：
>
>  ```text
>  ``\,`A' or `B?'\,'' he asked.
>  ```
>
>  
>
>* 符号 - 单独使用是连字符（hyphen）；两个连用是en dash；三个连用是em dash，即破折号
>
>* 西文的省略号（ellipsis）使用 \ldots 或 \dots 命令产生
>
>* 句中使用省略号，前后加空格最好放入数学模式
>
>  ```text
>  She $\ldots$ she got it.
>  ```
>
>* 句末使用省略号，四个点
>
>  ```text
>  I've no idea\ldots.
>  ```
>
>* 其他标点符号
>
>  ![image-20200729102346809](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729102346809.png)

>6、空格与换行
>
>* 以字母命名的宏，后面的空格会被忽略，可以使用’\ ‘，表示两个普通单词间的空格距离；也可以在命令后加一个空的分组{}，有时也可以把命令用一个分组包裹起来
>
>  ```latex
>  \TeX ing
>  
>  \TeX\ ing
>  
>  \TeX{}ing
>  
>  {\TeX}ing
>  ```
>
>* 带子 ~ （ties），TeX禁止在这种空格之间分行，可以用来表示一些不宜分开的情况，例如：
>
>  ![image-20200729103122173](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729103122173.png)
>
>* LaTeX 把大写字母后的点看作是缩写标记，把小写字母后的点看作是句子结束，并对他们使用不同的间距；使用’\ '指明正常空格或小写缩写后的空格，用'\@'指明是大写字母后句末
>
>  ```latex
>  Thiker et al.\ made the double play.
>  
>  Roman number 
>  ```
>
>* 整体禁止标点后不同的间距，使用命令：
>
>  ```latex
>  \frenchspacing
>  ```
>
>* 个别时候需要忽略汉字与其他内容之间自动产生的空格，可以把汉字放进一个盒子里面：
>
>  ```latex
>  \mbox{条目}-a 不同于条目-b
>  %条目-a 不同于条目 -b
>  ```
>
>* 完全禁用汉字与其他内容之间的空格，使用命令：
>
>  ```latex
>  \CJKsetecglue{}
>  汉字word
>  %汉字word
>  ```
>
>* `\phantom` 命令
>
>  ```latex
>  幻影\phantom{参数}速速隐形
>  幻影参数速速显形
>  %幻影   速速隐形
>  %幻影参数速速显形
>  ```
>
>  类似还有 `\hphantom` 和 `\vphantom` 分别表示水平方向和垂直方向的幻影
>
>* 空行，用 \\ \ 换行，用 \par 分段

##### 2.1.2 特殊符号

>1、正文中常用的部分特殊符号，最简单的方法是在UTF-8编码下直接输入符号![image-20200729111251885](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729111251885.png)

##### 2.1.3 字体

>1、字号font，字体编码font encoding，字体族font family，字体形状font shape，字体系列font series
>
>* 预定义的字体族有三种, roman family、sans serif family and typewriter family
>
>  ![image-20200729112709089](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729112709089.png)
>
>* 预定义的字体形状有四种, upright shape(roman shape)、italic shape、slanted shape and small capitals shape
>
>  ![image-20200729112839785](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729112839785.png)
>
>* 预定义的字体系列有 medium 和 bold extended 两种：
>
>  ![image-20200729113018120](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729113018120.png)
>
>* ![image-20200729113108948](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729113108948.png)
>
>* 使用 `\textnormal{}` 和 `\normalfont` 命令把字体设置为“普通格式”，默认情况下相当于 `\rmfamily` `\mdseries` `\upshape`, 适用于在复杂环境中恢复普通字体
>
>  ![image-20200729165757760](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729165757760.png)
>
>* 对于中文字体，一般只使用不同的字体族进行区分。在xeCJK 和 CJK宏包机制下，中文字体的选择命令和西文字体是分离的，选择中文字体族使用 `\CJKfamily` 命令，如：
>
>  ![image-20200729172508587](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729172508587.png)
>
>* 在默认情况下针对 Windows 常用字体配置了的四种字体族：song、hei、kai、fs, ctex提供了简化的命令:
>
>  ![image-20200729172650743](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729172650743.png)
>
>* LaTeX提供了更原始的命令
>
>  ```latex
>  \fontencoding{编码}
>  \fontfamily{族}
>  \fontseries{系列}
>  \fontshape{形状}
>  \fontsize{大小}{基本间距}		%纯数字，单位是 pt
>  ```
>
>  在命令后加` \selectfont` 命令使它们生效:
>
>  ![image-20200729173212126](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729173212126.png)
>
>  也可以使用 `\usefont{编码}{族}{系列}{形状}` 一次性选择某个字体，如：
>
>  ![image-20200729173329318](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729173329318.png)

> 2、使用更多字体
>
> * 现代方法，在 XeLaTeX 中，主要使用 fontspec 宏包来调用字体：
>
>   ```latex
>   \setmainfont[<可选选项>]{<字体名>}
>   \setsansfont[<可选选项>]{<字体名>}
>   \setmonofont[<可选选项>]{<字体名>}
>   ```
>
>   例如：
>
>   ![image-20200729174335742](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729174335742.png)

>3、强调文字命令: `\emph`
>
>![image-20200729182301469](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729182301469.png)
>
>在西文中通常使用意大利体表示夹在正文中的强调语句
>
>粗体强调: `\textbf`
>
>![image-20200729182431191](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729182431191.png)
>
>下划线强调: `\underline`
>
>![image-20200729182510647](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729182510647.png)
>
>但是 `\underline` 命令的下划线部分不能换行, 而且下划线与文字的距离不整齐. ulem 宏包的 `\ulem` 命令解决了这些问题, 使用并且把默认的 `\emph` 命令也改为使用下划线的方式
>
>![image-20200729183341955](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729183341955.png)
>
>如果不希望下划线代替标准的 \emph 命令, 可以给 ulem 宏包加 normalem 参数, 或使用 `\normalem` 和 `\ULforem` 命令切换两种强调
>
>![image-20200729183529643](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729183529643.png)
>
>CJKfntef 宏包对汉字也提供了类似的功能，同时也进行了一些扩充:
>
>![image-20200729183627363](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729183627363.png)

##### 2.1.4 字号与间距

>1、![image-20200729184506547](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729184506547.png)
>
>![image-20200729184539507](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729184539507.png)
>
>`\normalize` 的大小为 10pt, 这个数值表示字体中一个 \quad 的长度
>
>2、可使用命令 `\linespread{<因子>}` 来设置实际行距为基本行距的倍数

##### 2.1.5 水平间距与盒子

>1、TeX 中的长度单位:
>
>* pt point 点(欧美传统排版的长度单位, 有时叫做“磅”)
>* pc pica(1 pc = 12 pt, 相当于四号字大小)
>* in inch 英寸(1 in = 72.27 pt)
>* bp big point 大点(在 PostScript 等其他电子排版领域的 point 都指大点, 1 in = 72bp)
>* cm centimeter 厘米(2.54cm = 1 in)
>* mm millimeter 毫米(10 mm = 1cm)
>* dd didot point(欧洲大陆使用, 1157 dd = 1238 pt)
>* cc cicero(欧洲大陆使用, pica 的对应物, 1 cc = 12 dd)
>* sp scaled point(TeX 中最小的长度单位, 所有长度都是它的倍数, 65536 sp = 1 pt)
>* em 全身(字号对应的长度, 等于一个 \quad 的长度, 也称为"全方". 本义是大写字母 M 的宽度)
>* ex x-height(与字号相关, 由字体定义. 本义是小写字母 x 的高度)

>2、盒子
>
>```latex
>\mbox{cannot be broken}
>```
>
>\makebox 与 \mbox 类似, 但有两个可选参数, 指定盒子的宽度和对齐方式:
>
>```text
>\makebox[<宽度>][<位置>]{<内容>}
>对齐参数可取 c(中)、l(左)、r(右)、s(分散), 默认居中
>```
>
>![image-20200729190322010](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729190322010.png)

#### 2.2 段落与文本环境

##### 2.2.1 正文段落

>1、在段落前使用 \noindent 命令可以禁用缩进; 如果要在本来没有缩进的地方使用缩进, 可以用 \indent 命令产生一个长为 \parident 的缩进

>2、段落最明显的属性是对齐方式, LaTeX 的段落默认的是两端均匀对齐的.
>
>`\raggedright` , 命令设置段落左对齐(ragged right 意为右边界参差不齐)
>
>类似地, 右对齐使用 `\raggedleft` 命令, 居中使用 `\centering` 命令. 右对齐常常用于排版签名、日期、格言警句等; 居中的段落则有强调的意味

##### 2.2.2 文本环境

>1、quote 环境与 quotation 环境
>
>![image-20200729195830128](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729195830128.png)
>
>![image-20200729195839768](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729195839768.png)

>2、摘要环境 abstract 是 article 和 report 文档类定义的, 它产生一个类似 quotation 的小号字环境, 并增加标题:
>
>![image-20200729200811577](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729200811577.png)
>
>![image-20200729200909442](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729200909442.png)

##### 2.2.3 列表环境

>1、编号的 enumerate 环境
>
>![image-20200729223655838](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729223655838.png)

>2、不编号的 itemize 环境
>
>![image-20200729223726235](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729223726235.png)

>3、description 环境: 使用 `\item` 命令时的可选参数作为条目的关键字
>
>![image-20200729223851476](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729223851476.png)

>4、条目都以 `\item` 命令开头. 使用 `\item` 命令的可选参数可以临时手工设置编号或标志符号, 如:
>
>![image-20200729224044579](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729224044579.png)

##### 2.2.4 定理类环境

>
>
>

##### 2.2.5 抄录和代码环境

>1、`\verb` 命令
>
>```latex
>\verb<符号><抄录内容><符号>
>```
>
>在 `\verb` 后, 起始的符号和末尾的符号相同, 两个符号之间的部分将使用打字机字体逐字原样输出:
>
>![image-20200729225152918](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729225152918.png)
>
>2、`\verb*` 命令则可以使输出的空格可见:
>
>![image-20200729225255217](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729225255217.png)

>3、大段抄录使用 verbatim 环境:
>
>![image-20200729225343742](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200729225343742.png)
>
>4、同样可以使用 verbatim* 环境使输出空格可见

>5、程序代码与 listings

##### 2.2.6 tabbing 环境

##### 2.2.7 脚注与编注

>1、脚注 
>
>使用 `\footnote{<脚注内容>}` 产生脚注. 产生一个阿拉伯数字的上标作为编号, 脚注内容出现在页面底部, 以 `\footnotesize` 的自豪输出.
>
>![image-20200730095947068](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200730095947068.png)
>
>2、脚注通常只能用在一般的正文段落中, 不能用于表格、左右盒子等受限的场合; 此外, 脚注也不能直接用在 `\section` 等章节命令的参数中, 也不能用在 `\pardox` 中; 不过可以把脚注用在 minipage 环境中, 此时脚注产生在盒子底部, 使用局部的编号
>
>![image-20200730100349595](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200730100349595.png)

>3、边注: 在单面模式 onecolumn 中, 边注在页面的右侧; 在双面模式 twocolumn 下, 边注在页面的外侧(即奇数页在右, 偶数页在左). `\marginpar` 命令可以带一个可选参数, 设置出现在偶数页左侧的边注, 而原来的参数表示在右侧的边注, 例如:
>
>![image-20200730102528452](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200730102528452.png)
>
>4、可以使用命令 `\reversemarginpar` 改变边注的左右(或内外)位置, 或者用命令 `\normalmarginpar` 复原边注的左右位置

##### 2.2.8 垂直边距与垂直盒子

>1、类似用 `\space` 和 `hspace*` 生成水平间距, 可以用 `\vspace{<长度>}` 和 `\vspace*{<长度>}` 生成垂直间距. 垂直间距也是弹性距离, 可以用 `\vfill` 表示 `\vspace{fill}` 
>
>2、`\vspace` 的参数可以是长度的值, 也可以是像 `\parskip` 、`\itemsep` 这样的长度变量; `\smallskip`、`medskip`、`\bigskip`分别表示较小的、中间的和较大的垂直间距:
>
>![image-20200730103547540](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200730103547540.png)

>尽管我一直这样相信——“即使后悔，当下也是最好的，当下就是最好的”，但我还是不免为自己所做过的傻事心痛、后悔。因为原谅这一切的勇气是别人给的，我只能做出选择。
>
>心痛。

#### 2.3 文章的结构层次

##### 2.3.1 标题和标题页

>![image-20200730110304539](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200730110304539.png)
>
>1、`\author` 定义的参数可以分行, 一般第一行是作者姓名, 后面是作者的单位、联系方式等. 如果文档有多个作者, 则多个作者之间用 `\and` 分隔, 例如:
>
>![image-20200730110523391](C:\Users\Chen\AppData\Roaming\Typora\typora-user-images\image-20200730110523391.png)

