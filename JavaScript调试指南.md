## JavaScript 调试指南

本节将全面介绍谷歌开发者工具的新特性以及新的调试流程，基本的调试方法请参考[代码调试](代码调试.md)。

### 逐步执行

#### Step over line of code

当逐步执行的过程中遇到函数时，该函数又与调试的问题没什么关系，我们并不关心函数内部执行结果时，我们可以点击**Step over**摁钮![](https://developers.google.com/web/tools/chrome-devtools/javascript/imgs/step-over.png)执行完该函数，而无需跳入函数内部执行。如下图蓝框所示：

![](http://p1.bqimg.com/582863/d68e3d905e8d01b2.png)


例如：假设你现在正在调试如下代码，现在执行到A，点击**Step over**，谷歌开发者工具会执行完B和C的代码，然后中断在D的位置。

```
function updateHeader() {
  var day = new Date().getDay();
  var name = getName(); // A
  updateName(name); // D
}
function getName() {
  var name = app.first + ' ' + app.last; // B
  return name; // C
}
```

#### Step into line of code 

当逐步执行到一个函数，我们关心内部执行情况时，点击**Step into**摁钮![](https://developers.google.com/web/tools/chrome-devtools/javascript/imgs/step-into.png)，进入函数内部逐步执行。如下图蓝框所示：

![](http://p1.bqimg.com/582863/d599df677a59f192.png)

例如：假设逐步执行到A，点击**Step into**摁钮，谷歌开发者工具会进入到getName函数内部，中断在B位置，然后逐步执行。

```
function updateHeader() {
  var day = new Date().getDay();
  var name = getName(); // A
  updateName(name);
}
function getName() {
  var name = app.first + ' ' + app.last; // B
  return name;
}
```
#### Step out of line of code

当代码逐步执行到一个和所调试问题无关的函数内部时，点击**Step out**摁钮![](https://developers.google.com/web/tools/chrome-devtools/javascript/imgs/step-out.png)跳出该函数，中断在函数调用处的下一行。如下图蓝框所示：

![](http://p1.bpimg.com/582863/81f55dcf8f6920e7.png)

例如：假设代码执行到A，点击**Step out**，谷歌开发者工具会执行完getName函数中剩下的代码，然后中断在C的位置。


```
function updateHeader() {
  var day = new Date().getDay();
  var name = getName();
  updateName(name); // C
}
function getName() {
  var name = app.first + ' ' + app.last; // A
  return name; // B
}
```
#### 执行到指定行

当调试一个非常长的函数时，很多的代码与所调试的问题并无关系，当然你可以一行一行逐步执行到可能与所调试问题有关系的那一行，当然你还可以在那一行设置代码行断点，然后点击**Resume Script Execution**![](https://developers.google.com/web/tools/chrome-devtools/images/resume-script-execution.png)恢复代码执行，直到中断到刚才设置的代码行断点。
