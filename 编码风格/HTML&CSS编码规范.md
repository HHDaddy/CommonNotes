HTML&CSS编码规范  
作者：HHDaddy  
参考：[http://mdo.github.io/code-guide/](http://mdo.github.io/code-guide/)

#黄金定律
-  永远遵循同一套编码规范。
-  不管有多少人共同参与同一项目，一定要确保每一行代码都像是同一个人编写的。

----
##HTML

###语法

- 用两个空格来代替制表符（tab） -这是唯一能保证在所有环境下获得一致展现的方法。
- 对于属性的定义，确保全部使用双引号，绝不要使用单引号。
- 不要在自闭合元素的尾部添加斜线（HTML3、HTML5规范可选，XHTML必选）。
- 不要省略可选的结束标签。
>     <!DOCTYPE html>  
>     <html>  
>        <head>  
>        <title>Page title</title> 
>        </head>  
>      <body>  
>       <img src="images/company-logo.png" alt="Company">  
>       <h1 class="hello-world">Hello, world!</h1>  
>      </body>  
>     </html>  

###HTML5 doctype
为每个 HTML 页面的第一行添加标准模式（standard mode）的声明。

>     <!DOCTYPE html>

###语言属性
根据 HTML5 规范：
强烈建议为 html 根元素指定 lang 属性，以为文档设置正确的语言。
>     <html lang="zh-CN"
>       <!-- ... -->
>     </html

###IE 兼容模式
一直使用`<meta>`，以通知IE采用其所支持的最新模式渲染页面。
>     <meta http-equiv="X-UA-Compatible" content="IE=Edge">

###字符编码
一般采用 UTF-8 编码。
>     <head>
>       <meta charset="UTF-8">
>     </head>

###引入 CSS 和 JavaScript 文件
根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 
`type` 属性，因为 `text/css` 和 `text/javascript` 分别是它们的默认值。
在HTML4中需要显示设置type属性。
>     <!-- External CSS -->
>     <link rel="stylesheet" href="code-guide.css">
>     
>     <!-- JavaScript -->
>     <script src="code-guide.js"></script>

###属性顺序
HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。  

- class  
- id, name  
- data-*  
- src, for, type, href  
- title, alt  
- aria-*, role  

>     <a class="..." id="..." data-modal="toggle" href="#">
>       Example link
>     </a>

###布尔（boolean）型属性
布尔型属性可以在声明时不赋值。XHTML 规范要求为其赋值，但是 HTML5 规范不需要。
>     <input type="text" disabled>
>     <input type="checkbox" value="1" checked> 
>     <select>
>       <option value="1" selected>1</option>
>     </select>

**简单来说，就是不用赋值**。

###减少标签的数量
编写 HTML 代码时，尽量避免多余的父元素。很多时候，这需要迭代和重构来实现。请看下面的案例：
>     <!-- Not so great -->
>     <span class="avatar">
>       <img src="...">
>     </span>
>     
>     <!-- Better -->
>     <img class="avatar" src="...">

###JavaScript 生成的标签
通过 JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。能避免时尽量避免。

##CSS

###语法
- 用两个空格来代替制表符（tab） -这是唯一能保证在所有环境下获得一致展现的方法。  
- 为选择器分组时，将单独的选择器单独放在一行。  
- 为了代码的易读性，在每个声明块的左花括号前添加一个空格。  
- 声明块的右花括号应当单独成行。  
- 每条声明语句的 `:` 后应该插入一个空格。  
- 为了获得更准确的错误报告，每条声明都应该独占一行。
- 所有声明语句都应当以分号结尾。  
- 对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，`box-shadow`）。
- 不要在` rgb()`、`rgba()`、`hsl()`、`hsla()` 或 `rect()` 值的内部的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。  
- 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，`.5` 代替` 0.5`；-`.5px` 代替 `-0.5px`）。  
- 十六进制值应该全部小写，例如，`#fff`。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。  
- 尽量使用简写形式的十六进制值，例如，用 `#fff `代替 `#ffffff`。  
- 为选择器中的属性添加双引号，例如，`input[type="text"]`。  
- 避免为 0 值指定单位，例如，用 `margin: 0;` 代替 `margin: 0px;`。  
>     - /* Bad CSS */
>     .selector, .selector-secondary, .selector[type=text] {
>       padding:15px;
>       margin:0px 0px 15px;
>       background-color:rgba(0, 0, 0, 0.5);
>       box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
>     }
>     
>     /* Good CSS */
>     .selector,
>     .selector-secondary,
>     .selector[type="text"] {
>       padding: 15px;
>       margin-bottom: 15px;
>       background-color: rgba(0,0,0,.5);
>       box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
>     }

###声明顺序
相关的属性声明应当归为一组，并按照下面的顺序排列：

1. Positioning（位置）
2. Box model（盒模型）
3. Typographic（排版）
4. Visual（可视化）

>     .declaration-order {
>       /* Positioning */
>       position: absolute;
>       top: 0;
>       right: 0;
>       bottom: 0;
>       left: 0;
>       z-index: 100;
>     
>       /* Box-model */
>       display: block;
>       float: right;
>       width: 100px;
>       height: 100px;
>     
>       /* Typography */
>       font: normal 13px "Helvetica Neue", sans-serif;
>       line-height: 1.5;
>       color: #333;
>       text-align: center;
>     
>       /* Visual */
>       background-color: #f5f5f5;
>       border: 1px solid #e5e5e5;
>       border-radius: 3px;
>     }

###不要使用 `@import`
与 `<link>` 标签相比，`@import` 指令要慢很多，不光增加了额外的请求次数，还会导致不可预料的问题。

###媒体查询（Media query）的位置
将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。
>     .element { ... }
>     .element-avatar { ... }
>     .element-selected { ... }
>     
>     @media (min-width: 480px) {
>       .element { ...}
>       .element-avatar { ... }
>       .element-selected { ... }
>     }

###带前缀的属性
当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。

>     /* Prefixed properties */  
>     .selector {
>       -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
>       box-shadow: 0 1px 2px rgba(0,0,0,.15);
>     }

###单行规则声明
- 对于只包含一条声明的样式，建议将语句放在同一行。  
- 对于带有多条声明的样式，将声明分为多行。

###注释
- 确保你的代码能够自描述、注释良好并且易于他人理解。  
- 对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。

###class 命名
- class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。   
- class 名称应当尽可能短，并且意义明确；避免过度任意的简写。  
- 使用有意义的名称。  
- 基于最近的父 class 或基本（base） class 作为新 class 的前缀。  
- 使用 .js-* class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。

###选择器
- 对于通用元素使用 class ，这样利于渲染性能的优化。  
- 对于经常出现的组件，避免使用属性选择器（例如，[class^="..."]）。浏览器的性能会受到这些因素的影响。  
- 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3个 。  


