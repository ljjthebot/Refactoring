# Switch语句

## 迹象和症状

你有一个复杂的开关操作符或一系列的if语句。

## 问题原因

在面向对象的代码中，相对较少使用switch和case操作符是面向对象代码的特征之一。通常，单个switch的代码可能分散在程序的不同地方。当添加新条件时，你必须找到所有的switch代码并进行修改。

作为一个经验法则，当你看到switch时，应该考虑多态性。

## 处理方法

为了隔离switch并将其放入正确的类中，你可能需要使用提取方法（Extract Method）然后再移动方法（Move Method）。

如果switch基于类型代码，例如切换程序的运行时模式，使用替换类型代码为子类（Replace Type Code with Subclasses）或替换类型代码为状态/策略（Replace Type Code with State/Strategy）。

在指定了继承结构之后，使用替换条件语句为多态性（Replace Conditional with Polymorphism）。

如果操作符中没有太多的条件，而它们都调用相同的方法，只是参数不同，那么多态性将是多余的。在这种情况下，你可以将该方法拆分为多个较小的方法，使用替换参数为显式方法（Replace Parameter with Explicit Methods）并相应地更改switch。

如果条件选项中有一个为null，使用引入Null对象（Introduce Null Object）。

## 收益

改善了代码的组织结构。

## 何时忽略

当switch操作符执行简单操作时，没有理由进行代码更改。

通常，工厂设计模式（工厂方法或抽象工厂）使用switch操作符来选择创建的类时，可以忽略。
