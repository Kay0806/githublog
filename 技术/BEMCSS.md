## BEM —— 一种 CSS 命名方式

BEM 是 Block-Element-Modifier 的缩写，是一种**很丑陋**的 CSS 命名方式，没错，**很丑陋**。其最终的命名效果是类似这样的：

	.navigation {}
	.navigation__item {}
	.navigation__item--active{}
	.sub-navigation {}
	.sub-navigation__item {}
 
你可以看到奇丑无比的「双下划线」（__）和「双连接线」（--），不过一会你就知道它们的作用了。

## 块与元素（Blocks & Elements）

![图1](http://imgcache.oa.com/photos/26191/e97978647395be2cd93b69ba10eac23a.jpg)


BEM 这种巧妙的命名方法让你的CSS类对其他开发者来说更加透明而且更有意义。BEM代表块（Block），元素（Element），修饰符（Modifier）。上图很好地解释了什么是块，什么是元素。


就一个页面来说，开发者其实知道它是由一些方形的「块」构成的。「元素」是块的一部分，具有某种功能。元素是依赖上下文的：它们只有处于他们应该属于的块的上下文中时才是有意义的。「修饰符」则表示块或元素的一些状态，如 hover、active 和 disabled 等。

对这些块和元素进行组织，对开发是很有帮助的。进行组织的第一步就是命名。

BEM中，一个项目中的块名必须是唯一的，明确指出它所描述的是哪个块。相同块的实例可以有相同的名字。一个块范围内的一种元素的名字也必须是唯一的。一种元素可以重复出现多次。

## 命名

BEM 的命名并无明确的规定，简单的示例如下：

	.block{}
	.block__element{}
	.block--modifier{}

你也可以加上前缀：

	l-header {}
	c-dropdown {}
	u-textCenter {}
	js-hook {}

其中 l （layout），表示布局相关的元素；c 是组件；u 是工具类；js 是留给 JS 的钩子，永远不应该出现在 CSS 中。

* 一个块（或者一个元素）必须有一个唯一的类名。
* HTML元素不能用作 CSS 选择器（如.menu td），因为这样的选择器并非是完全上下文无关的。
* 避免使用级联（cascading）选择器（如.menu .item），原因同上。

## 好处

BEM的关键是光凭名字就可以告诉其他开发者某个标记是用来干什么的。通过浏览HTML代码中的 class 属性，你就能够明白模块之间是如何关联的：有一些仅仅是组件，有一些则是这些组件的子孙或者是元素,还有一些是组件的其他形态或者是修饰符。不信看看下面的类名：

	.person{}
	.person__hand{}
	.person--female{}
	.person--female__hand{}
	.person__hand--left{}	

如果采用常规的写法：

	.person{}
	.hand{}
	.female{}
	.female-hand{}
	.left-hand{}

你可以明显看出，各类名少了一些「关联」。当然你可以通过类名的组合来透露它们的关联：

	.person{}
	.person > .hand{}
	.person.female {}
	.person .female-hand{}
	.person .left-hand{}

但你要知道级联会破环上下文，而子代选择器又依赖与 DOM 结构。

再看看一个搜索框的写法。常规命名可能是这样：

	<form class="site-search  full">
		<input type="text" class="field">
		<input type="submit" value ="Search" class="button">
	</form>	

用 BEM 命名是这样：

	<form class="site-search  site-search--full">
		<input type="text" class="site-search__field">
		<input type="submit" value ="search" class="site-search__button">
	</form>

## 用不用 BEM？

通常人们会认为 BEM 这种写法难看。但你应该能发现 BEM 虽然难看，但是它很「易读」。如果只是「看起来有点怪」而事实上是一种有效的手段，那么我们在开发就可以考虑一下它。

另一点需要知道的是，没必要永远遵守 BEM，怎么舒服怎么来就好。例如一个 logo（它是 header 里的一个元素），我们可以用 BEM 写成：

	.header{}
	.header__logo{}	

也可以直接给一个 .logo 类名。

有朝一日，我们需要改一下 logo，那么又可方便的用上 BEM 了：

	.logo{}
	.logo--chunjie{} /*春节 logo */

## 参考

* [BEM 思想之彻底弄清 BEM 语法](http://www.w3cplus.com/css/mindbemding-getting-your-head-round-bem-syntax.html)
* [BEM 的 50 道阴影](http://www.w3cplus.com/css/fifty-shades-of-bem.html)
