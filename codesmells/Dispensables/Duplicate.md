# 重复代码

## 迹象和症状

两个代码片段看起来几乎相同。

## 问题原因

重复通常发生在多个程序员同时处理同一程序的不同部分时。由于他们正在处理不同的任务，他们可能不知道他们的同事已经编写了类似的代码，可以用于他们自己的需求。

还有更微妙的重复，即特定部分的代码看起来不同，但实际上执行相同的任务。这种重复可能难以发现和修复。

有时重复是有意的。当匆忙赶工以满足截止日期，并且现有代码“几乎正确”时，初学者程序员可能无法抵抗复制和粘贴相关代码的诱惑。在某些情况下，程序员可能只是懒得清理。

## 处理方法

- 如果在同一类的两个或更多方法中找到相同的代码：使用提取方法（Extract Method），并在两个位置都调用新方法。
- 如果在同一层次的两个子类中找到相同的代码：
  - 对两个类都使用提取方法（Extract Method），然后对用于上拉的方法使用上拉字段（Pull Up Field）。
  - 如果重复的代码在构造函数中，使用上拉构造函数体（Pull Up Constructor Body）。
- 如果重复的代码相似但不完全相同，使用形成模板方法（Form Template Method）。
- 如果两个方法执行相同的操作但使用不同的算法，选择最佳算法并应用替代算法（Substitute Algorithm）。
- 如果在两个不同的类中发现重复的代码：
  - 如果这些类不是层次结构的一部分，使用提取超类（Extract Superclass）创建这些类的单一超类，保留所有先前的功能。
  - 如果创建超类困难或不可能，在一个类中使用提取类（Extract Class），并在另一个类中使用新组件。
- 如果存在大量条件表达式并执行相同的代码（仅在条件不同的情况下），通过合并这些运算符到一个单一条件中使用合并条件表达式（Consolidate Conditional Expression），并使用提取方法（Extract Method）将条件放入具有易于理解名称的单独方法中。
- 如果在条件表达式的所有分支中都执行相同的代码：使用合并重复条件片段（Consolidate Duplicate Conditional Fragments）将相同的代码放在条件树外部。

## 收益

合并重复的代码简化了代码结构，使其更短。

简化 + 简短 = 更容易简化和更便宜的维护代码。

## 何时忽略

在极少数情况下，合并两个相同的代码片段可能使代码更不直观和明显。
