# 引入参数对象

## 问题

你的方法包含一组重复的参数。

## 解决方案

将这些参数替换为一个对象。

### 引入参数对象 - 改前

### 引入参数对象 - 改后

## 为什么重构

在多个方法中经常遇到相同的参数组。这导致参数本身以及相关操作的代码重复。通过将参数合并到单个类中，您还可以将处理这些数据的方法移动到该类中，从而使其他方法摆脱这段代码。

## 优势

更可读的代码。与杂乱无章的参数相比，你看到的是一个具有可理解名称的单一对象。

散布在这里和那里的相同参数组会创建它们自己的代码重复：虽然相同的代码没有被调用，但经常会遇到相同的参数组和参数。

## 缺点

如果只将数据移到一个新类中，而不打算将任何行为或相关操作移到那里，这就开始有点像数据类。

## 如何重构

1. 创建一个新类来表示你的参数组。使类不可变。

2. 在要重构的方法中使用“添加参数”，这是你的参数对象将被传递的地方。在所有方法调用中，将从旧方法参数创建的对象传递给这个参数。

3. 现在，逐个从方法中删除旧参数，在代码中用参数对象的字段替换它们。在替换每个参数后测试程序。

4. 完成后，查看是否有必要将方法的一部分（有时甚至整个方法）移动到参数对象类中。如果是这样，请使用“移动方法”或“提取方法”。