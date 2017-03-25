<!-- toc -->


## JavaScript 调试指南

本节将全面介绍谷歌开发者工具的新特性以及新的调试流程，基本的调试方法请参考[代码调试](代码调试.md)。

### 逐步执行

#### Step over line of code

当逐步执行的过程中遇到函数时，该函数又与调试的问题没什么关系，我们并不关心函数内部执行结果时，我们可以点击**Step over**摁钮![](/assets/debug/step-over.png)执行完该函数，而无需跳入函数内部执行。如下图蓝框所示：

![](/assets/debug/d68e3d905e8d01b2.png)


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

当逐步执行到一个函数，我们关心内部执行情况时，点击**Step into**摁钮![](/assets/debug/step-into.png)，进入函数内部逐步执行。如下图蓝框所示：

![](/assets/debug/d599df677a59f192.png)

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

当代码逐步执行到一个和所调试问题无关的函数内部时，点击**Step out**摁钮![](/assets/debug/step-out.png)跳出该函数，中断在函数调用处的下一行。如下图蓝框所示：

![](/assets/debug/81f55dcf8f6920e7.png)

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

当调试一个非常长的函数时，很多的代码与所调试的问题并无关系，当然你可以一行一行逐步执行到可能与所调试问题有关系的那一行，当然你还可以在那一行设置代码行断点，然后点击**Resume Script Execution**![](/assets/debug/resume-script-execution.png)恢复代码执行，直到中断到刚才设置的代码行断点。其实，有更快捷的方法。
在刚才设置断点的那一行代码右击，菜单中选择**Continue to Here**，谷歌开发者工具会恢复代码执行到该行，然后中断下来。

![](/assets/debug/4ce654328261717c.png)

#### 调用栈回退

当程序中断时，在调用栈面板(关于调用栈请参考[逐步执行](逐步执行.md))函数名上右击，选择**Restart Frame**，程序将回退到所选函数的第一行进行中断，此功能可以达到回退代码执行的功能，对于不小心代码执行过头的情况，能很方便的回退过去重新执行。

例如：假设代码中断在位置A处，通过**Restart Frame**后，代码会中断在B处。接着可以从B处理重新开始逐步执行。

```
function factorial(n) {
  var product = 0; // B
  for (var i = 1; i <= n; i++) {
    product += i;
  }
  return product; // A
}
```
![](/assets/debug/restart-frame.png)

#### 恢复代码执行

点击**Resume Script Execution**摁钮![](/assets/debug/resume-script-execution.png)，恢复代码执行，只到遇到下一个断点，如果有的话。

![](/assets/debug/97c8e6ed79083138.png)