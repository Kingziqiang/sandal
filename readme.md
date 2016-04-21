# Sandal

sandal取其“檀香”之意，针对移动端站点为前端人员提供了一些基础的重置，常用的`mixin`，如flex布局，等分，水平垂直居中，常用图标等，基于它你可以扩展出更多你需要的组件。

## 如何使用
sandal，分核心文件和扩展文件两种。其中核心文件包括重置样式，`@mixin`，`%`等方便调用；而扩展文件则提供基础原子类class，图标，网格系统。

核心文件提供两个集合文件以供调用，分别为`_function.scss`， `_core.scss`。两者的区别为function仅提供功能，而core除了提供function的功能，还会会生成一份重置样式

扩展文件有三个，分别为`_icons.scss`，`_helper.scss`，`_grid.scss`，可根据需要调用

### npm 调用

#### 安装

    npm install sass-sandal --save-dev

#### 调用

    @import 'node_modules/sass-sandal/core';

    @import 'node_modules/sass-sandal/function';

    @import 'node_modules/sass-sandal/ext/icons';

    @import 'node_modules/sass-sandal/ext/helper';

    @import 'node_modules/sass-sandal/ext/grid';

### 普通使用

在github上下载[sandal](https://github.com/marvin1023/sandal)，解压拷贝到项目目录

    @import 'sandal/core';

    @import 'sandal/function';

    @import 'sandal/ext/icons';

    @import 'sandal/ext/helper';

    @import 'sandal/ext/grid';


## 文件简述

sandal包括两个集合文件（core，function）和两个文件夹（core，ext）。其中core文件夹中为核心基础文件，包括variables，media-queries，mixin，animation，reset；ext文件夹中是一些扩展文件，目前包括svg icons，grid网格系统，helper基础class。

两个集合文件（core，function）导入的都是core中的文件，区别在于core除了提供基本功能之外还会生成一份reset样式，而function则只提供基本功能。至于ext中的文件则属于额外的一些模块扩展，可根据需求导入。

### core文件

#### variables
负责基础变量的文件，如常用的颜色，字体等变量。

#### media-queries
负责响应式断点判断的文件，来自paranoida的[sass-mediaqueries](https://github.com/paranoida/sass-mediaqueries)。

#### mixin
负责功能方面的文件。这里我们大概分成三个部分，一个是混合部分即mixin（主要定义了一些常用的`flex`,`translate`等），一个是placeholder选择器部分即%，最后就是我们的function函数部分。常用的include及extend就是在这里定义的。

#### animation

提供六组简单实用动画：fade-in/out, shrink-in/out, up-in/out, down-in/out，left-in/out，right-in/out。默认不产生样式，通过include调用

### reset
在[normalize](http://necolas.github.io/normalize.css/)的基础上，根据目前我们大家的使用习惯进行了一些归零行动，及基础文字颜色，clearfix，box-sizing等。

### ext文件

#### helper

提供常用的基础class，如overlay, full-width等

#### grid

移动端的网格系统，分为row和col，具体使用参考[3分钟13行代码搭建sass版移动端网格系统](http://imweb.io/topic/570b33f806f2400432c139b3)

#### icons

分为绘制的icon和svg图标两种，可参考icons文件夹中的`icons.html`

![default icon svg](ext/icons/svg-icons.png)

**绘制icon**

- icon颜色一般使用`currentColor`颜色，可以方便设置标签的color颜色来改变
- 对于不变的icon，如radio & checkbox直接设置大小，而一些可变的icon，通过标签的伪元素来绘制，标签本身没有设置大小，可根据实际情况设置大小（设置大点可扩大点击范围），伪元素绘制的会保持水平垂直居中

**svg 图标调用**

从[icomoon](https://icomoon.io/)提取了几个常用的svg图标，使用方法可参考ext/icons/icons.html，这里以home图标为例：

	<svg class="icon icon-home"><use xlink:href="icons.svg#icon-home"></use></svg>

如需改变颜色，可以通过设置css的fill属性来定义

	.icon-home{
		fill:#f00;
	}

最后可根据实际需求对icons.svg进行增删改， 然后使用。

注：使用时请把icons.svg拷贝至images目录或其他目录，方便调用



