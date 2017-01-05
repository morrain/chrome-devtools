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

