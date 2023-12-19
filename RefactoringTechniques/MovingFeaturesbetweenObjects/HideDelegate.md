# 隐藏委托（Hide Delegate）

## 问题
客户端通过对象 A 的字段或方法获取对象 B。然后客户端调用对象 B 的方法。

## 解决方案
在类 A 中创建一个新方法，将调用委托给对象 B。现在客户端不知道也不依赖于类 B。

## 为何进行重构

首先，让我们看一下术语：

- 服务器是客户端直接访问的对象。
- 委托是客户端所需功能的最终对象。

调用链出现在客户端从另一个对象请求对象，然后第二个对象请求另一个对象，依此类推。这些调用序列涉及客户端在类结构中导航。对这些相互关系的任何更改都将需要在客户端进行更改。

## 优势
隐藏了客户端对委托的调用。客户端代码对对象之间的关系细节知之甚少，对程序进行更改就会更容易。

## 缺点
如果需要创建大量的委托方法，服务器类可能成为一个不需要的中间层，导致中间人过多。

## 如何进行重构
对于客户端调用的委托类方法，创建一个在服务器类中将调用委托给委托类的方法。

更改客户端代码，使其调用服务器类的方法。

如果您的更改使客户端不再需要委托类，可以从服务器类中删除对委托类的访问方法（最初用于获取委托类的方法）。