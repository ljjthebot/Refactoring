# 方法的构造

大部分的重构工作都致力于正确地构造方法。在大多数情况下，过长的方法是问题的根源。这些方法内部的代码复杂性隐藏了执行逻辑，使得方法变得难以理解，甚至更难修改。

这一组重构技术旨在简化方法，消除代码重复，并为未来的改进铺平道路。

## 提取方法（Extract Method）

**问题：** 存在可以组合在一起的代码片段。

**解决方案：** 将这段代码移到一个新的独立方法（或函数）中，并用对该方法的调用替换原来的代码。

## 内联方法（Inline Method）

**问题：** 当方法体比方法本身更明显时，使用此技术。

**解决方案：** 用方法的内容替换对方法的调用，并删除方法本身。

## 提取变量（Extract Variable）

**问题：** 存在难以理解的表达式。

**解决方案：** 将表达式或其部分放入单独的、易于理解的变量中。

## 内联临时变量（Inline Temp）

**问题：** 存在一个临时变量，只赋值了一个简单表达式的结果，而无其他用途。

**解决方案：** 用表达式本身替换对变量的引用。

## 用查询替换临时变量（Replace Temp with Query）

**问题：** 将表达式的结果存储在本地变量中，以备将来在代码中使用。

**解决方案：** 将整个表达式移到一个单独的方法中，并从中返回结果。在代码中使用该方法查询结果，而不使用变量。必要时将新方法合并到其他方法中。

## 分割临时变量（Split Temporary Variable）

**问题：** 存在一个用于在方法内部存储各种中间值的本地变量（除了循环变量）。

**解决方案：** 为不同的值使用不同的变量。每个变量只负责一件特定的事情。

## 移除对参数的赋值（Remove Assignments to Parameters）

**问题：** 在方法体内将某个值赋给了参数。

**解决方案：** 使用本地变量代替参数。

## 用方法对象替换方法（Replace Method with Method Object）

**问题：** 存在一个长方法，其中本地变量纠缠在一起，无法应用提取方法。

**解决方案：** 将方法转化为一个独立的类，使得本地变量成为类的字段。然后，可以在同一类内将方法拆分为多个方法。

## 替换算法（Substitute Algorithm）

**问题：** 想要用新算法替换现有算法？

**解决方案：** 用新算法替换实现算法的方法体。