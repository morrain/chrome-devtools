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