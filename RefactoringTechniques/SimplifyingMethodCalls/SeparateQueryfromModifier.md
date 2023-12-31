# 将查询与修改分离

## 问题

你有一个方法既返回一个值，又在对象内部进行了一些修改吗？

## 解决方案

将该方法拆分为两个独立的方法。正如你所期望的，其中一个应该返回值，而另一个修改对象。

### 将查询与修改分离 - 改前

### 将查询与修改分离 - 改后

## 为什么重构

这种重构技术实现了“命令与查询职责分离”原则。该原则告诉我们要将负责获取数据的代码与负责更改对象内部状态的代码分开。

获取数据的代码称为查询。更改对象可见状态的代码称为修改器。当查询和修改器组合在一起时，你无法在不更改其条件的情况下获取数据。换句话说，你提出一个问题，即使在获取答案的同时也可以更改答案。当调用查询的人可能不知道方法的“副作用”时，这个问题变得更加严重，通常导致运行时错误。

但请记住，副作用仅在修改器更改对象的可见状态的情况下才是危险的。这可以是对象公共接口可访问的字段、数据库中的条目、文件等。如果修改器仅缓存复杂操作并将其保存在类的私有字段中，它几乎不会引起任何副作用。

## 优势

如果你有一个不改变程序状态的查询，你可以随意调用它多次，而不必担心由于调用方法而导致结果意外改变。

## 缺点

在某些情况下，执行命令后获取数据是方便的。例如，当从数据库中删除某些内容时，你可能想知道删除了多少行。

## 如何重构

1. 创建一个新的查询方法来返回原始方法的结果。

2. 修改原始方法，使其仅返回调用新的查询方法的结果。

3. 将所有对原始方法的引用替换为对查询方法的调用。在此行之前立即调用修改器方法，以防止原始方法在条件运算符或循环的条件中使用时产生副作用。

4. 摆脱原始方法中返回值的代码，该方法现在已成为适当的修改器方法。