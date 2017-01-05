## 编辑DOM

谷歌开发者工具**Elements**面板展示了当前页面的DOM树结构。

**简而言之**

* DOM 定义了页面的结构，每一个DOM结点，是页面上的一个元素。例如，div/p等。
* 通过**Elements**面板中呈现的DOM结构可以直接实时编辑DOM中结点的内容。
* 不过需要注意的是，实时的改动并不会保存到源文件，页面刷新后会被丢弃。
* 通过DOM断点，监视DOM变动

### 检视元素
 
在**Elements**面板，可以审查当前页面DOM树上的任意元素。选择任意元素后，可以审查应用其上的样式。
 
 ![](http://p1.bqimg.com/582863/79e9c30fcf0663fb.gif)
 
审查元素的方法不止一种，例如：

1. 在任意页面元素上右击，选择**审查元素**选项。如下图
![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/right-click-inspect.png)

2. 在谷歌浏览器中，使用快捷键`Ctrl + Shift + C `(Windows)或者`Cmd + Shift + C` (Mac)，直接打开谷歌开发者工具，并且使之处于审查元素状态，然后移动鼠标，谷歌开发者工具自动高亮鼠标下面的元素，确定要选择的元素后，在上面点击后退出审查元素模式，同时在**Elements**面板中高亮显示所选择的元素。

3. 在已经打开谷歌开发者工具的情况下，点击**审查元素**摁钮![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/inspect-icon.png)进入审查元素模式，重复**步骤2**。

4. 在控制台面板使用[inspect](命令行.md)方法，例如 `inspect(document.body)`。

### DOM树导航

可以通过鼠标或者键盘对DOM树中的节点进行展开和折叠操作。

折叠的节点，左侧有一个指向右方的箭头：![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/collapsed-node.png)

展开的节点，左侧有一个指向下方的箭头：![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/expanded-node.png)

* 使用鼠标
   * 单击一次，高亮此节点
   * 展开结点：在选中节点上双击或者点击左侧的箭头
   * 收起结点：点击左侧箭头
* 使用键盘
   * **Up Arrow**选中上面一个节点
   * **Down Arrow**选中下面一个节点
   * **Right Arrow**展开折叠的节点。再摁一次，选中该节点的第一个孩子节点。
   * **Left Arrow**收起展开的节点。
   
#### 导航面包屑

在**Elements**面板下方显示当前选中节点的面包屑。

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/breadcrumb-body.png)

当前选中的节点呈高亮蓝色。左边是当前选中节点的父节点，左边的左边是父节点的父节点，类推直到根节点。

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/breadcrumb-footer.png)

通过点击面包屑中的节点能快速定位到祖先结点。

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/breadcrumb-trail.png)

谷歌开发者工具能够在导航面包屑中显示足够长的路径，当长到整个状态栏显示不下的时候，会显示省略号，点击省略号，会显示被隐藏的部分。

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/breadcrumb-ellipsis.png)

### 打开更多操作菜单

通过**更多操作**菜单，我们可以和DOM结点进行多种交互操作。可以通过在DOM节点上右击，或者点击当前选择节点左侧的**更多操作**摁钮来打开**更多操作**菜单。如下图所示：

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/more-actions-menu.png)


### 编辑DOM结点以及属性

通过如下途径编辑：

* 直接在节点以及属性上双击
* 高亮节点，按**Enter**键，然后按**Tab**键，直到想要修改的属性被选中。
* 打开**更多操作**菜单，选择**Add Attribute**或者**Edit Attribute**选项。其中**Edit Attribute**是上下文敏感的，点击哪个属性编辑哪个属性。

> 编辑结束后，关闭标签会自动更新。

#### 以HTML格式编辑DOM节点及其子结点

* 打开**更多操作**菜单，选择**Edit as HTML**选项
* **Ctrl+Enter** (Windows / Linux) 或者  **Cmd+Enter** (Mac) 保存修改后的结果
* **ESC**键退出编辑模式，不保存所做的更改

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/edit-as-html.png)

### 移动DOM节点

点击要移动的节点，拖动它进行移动，到目标位置后松开即可。

![](http://i1.piimg.com/582863/69cfc0cbf1860a32.gif)

### 删除DOM节点

* 打开**更多操作**菜单，选择**Delete Node**选项
* 选中节点，然后按**Delete**键

### 滚动到可视区域

当鼠标hover或者选中一个DOM节点时，视窗内相应节点会被高亮。如果该结点此时滚动到视窗外，你会看到一个提示。如果该节点在视窗上方，刚提示在视窗顶部，如果该节点在视窗下方，刚提示在视窗底部。如下图所示，在**Elements**面板中选择的元素在视窗下方。

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/below-viewport.png)

打开**更多操作**菜单，选择**Scroll into View**选项，便可将选中的元素滚动到视窗可视区域。

### 设置DOM断点

设置DOM断点，可以方便的调试复杂的JavaScript应用。例如，JavaScript脚本正在修改一个DOM节点的样式，通过设置属性修改的DOM节点，可以中断JavaScript脚本的操作，再通过调用栈能快速的定位问题。可设置如下三种类型的DOM断点：**子树修改**、**属性修改**、**节点移除**。

#### 子树修改

当DOM节点的子节点被删除、移动或者新增加子节点。**子树修改**类型的DOM断点会被触发。例如，如果在`main-content`节点上设置了该断点，如下代码会触发该断点。

`var element = document.getElementById('main-content');`

`//modify the element's subtree.`

`var mySpan = document.createElement('span');`

`element.appendChild( mySpan );`

#### 属性修改

当DOM节点的属性(`class、id、name等等`)被JavaScript修改时触发。

`var element = document.getElementById('main-content');`

`// class attribute of element has been modified.`

`element.className = 'active';`

#### 节点移除

当节点被移除时触发。

`document.getElementById('main-content').remove();`

### DOM断点操作

**Elements**面板和**Sources**面板均提供管理操作DOM断点的窗口。在DOM断点窗口中，列举了所有设置的DOM断点，每个断点有DOM结点的标识符和DOM断点类型。如下图所示

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/dom-breakpoints-pane.png)

可通过如下方式操作列表中的DOM断点：

* **Hover**DOM断点上的DOM节点标识符，会在页面中高亮该节点，用于指示该节点在页面中的位置。
* 点击会选中相应DOM节点
* 点击左侧的checkbox会切换启用和禁用该断点的状态

DOM断点触发发，该DOM断点会被高亮。调用栈窗口会显示中断的原因，如下图所示：

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/breakpoint-reason.png)

### 查看DOM节点的事件监听

在**Event Listeners**窗口可以查看选中节点的事件监听。如下图所示

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/event-listeners-pane.png)

可见，第一级显示了被注册了事件监听的事件类型，如click。点击事件类型左侧的箭头，展开显示了所有事件处理器。事件处理器用一个类似CSS选择器一样的元素标识符进行标识，如`document`、`button#call-to-action`。如果相同元素上注册了多个事件处理器，这里会一一列举出来。

点击元素识别符左侧的展开箭头，可以查看事件处理器的属性。

属性名 | 属性描述
---|---
handler | 事件处理函数，右击选择'显示函数定义'选项，可以查看函数定义（如果存在源代码的话）
useCapture | bool值，指明addEventListener函数中是否设置useCapture

> 谷歌浏览器插件可能会在DOM元素上添加DOM事件。如果你发现很多并不是页面代码添加的事件，你可以使用隐身窗口打开你的页面。隐身窗口会默认阻止插件的运行。

#### 查看祖先的事件监听

当**Ancestors**被勾上时，当前选择节点祖先上注册的事件监听也会显示在列表中。

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/ancestors-enabled.png)

当**Ancestors**未被勾上时，列表中只显示当前选择节点上注册的事件监听。

![](https://developers.google.cn/web/tools/chrome-devtools/inspect-styles/imgs/ancestors-disabled.png)