# 提取超类
## 问题
您有两个具有相同字段和方法的类。

## 解决方案
为它们创建一个共享的超类，并将所有相同的字段和方法移动到其中。

## 提取超类 - 之前
[提取超类 - 之前]

## 提取超类 - 之后
[提取超类 - 之后]

## 为什么要重构
代码重复的一种形式是当两个类以相同的方式执行类似的任务，或以不同的方式执行类似的任务时。对象通过继承提供了一种内置机制，可以简化这种情况。但是，通常这种相似性直到创建类时才被注意到，因此后来必须创建一个继承结构。

## 好处
代码去重。共同的字段和方法现在只“存在”于一个地方。
## 不适用情况
不能将此技术应用于已经有超类的类。

## 如何重构
1. 创建一个抽象超类。
2. 使用"Pull Up Field"、"Pull Up Method"和"Pull Up Constructor Body"将共同功能移动到超类。首先处理字段，因为除了共同字段，您还需要移动在共同方法中使用的字段。
3. 在客户端代码中寻找可以用新类替换子类的地方（例如在类型声明中）。