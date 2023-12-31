# 在对象之间移动特性（Moving Features between Objects）

即使您以不太理想的方式在不同类之间分配功能，仍有希望。

这些重构技术展示了如何安全地在类之间移动功能、创建新类，并隐藏对公共访问的实现细节。

## [移动方法（Move Method）](MoveMethod.md)
**问题：** 一个方法在另一个类中的使用次数比在自己的类中还要多。
**解决方案：** 在使用该方法最多的类中创建一个新方法，然后将旧方法的代码移至新方法中。将原方法的代码转换为对另一个类中的新方法的引用，或者完全删除它。

## [移动字段（Move Field）](MoveField.md)
**问题：** 一个字段在另一个类中的使用次数比在自己的类中还要多。
**解决方案：** 在一个新类中创建一个字段，并将所有使用旧字段的地方重定向到新字段。

## [提取类（Extract Class）](ExtractClass.md)
**问题：** 一个类的工作相当于两个类，导致代码尴尬。
**解决方案：** 相反，创建一个新类，将负责相关功能的字段和方法放入其中。

## [内联类（Inline Class）](InlineClass.md)
**问题：** 一个类几乎什么都不做，也不负责任何事情，而且不计划为其添加任何额外的职责。
**解决方案：** 将该类的所有功能移至另一个类中。

## [隐藏代理（Hide Delegate）](HideDelegate.md)
**问题：** 客户端通过从对象 A 的字段或方法获取对象 B，然后调用对象 B 的方法。
**解决方案：** 在类 A 中创建一个新方法，将调用委托给对象 B。现在客户端对类 B 一无所知，也不依赖于它。

## [移除中间人（Remove Middle Man）](RemoveMiddleMan.md)
**问题：** 一个类有太多的方法仅仅是委托给其他对象。
**解决方案：** 删除这些方法，让客户端直接调用最终的方法。

## [引入外加方法（Introduce Foreign Method）](IntroduceForeignMethod.md)
**问题：** 一个实用程序类不包含您需要的方法，而且您不能将该方法添加到类中。
**解决方案：** 在客户端类中添加该方法，并将实用程序类的对象作为参数传递给它。

## [引入本地扩展（Introduce Local Extension）](IntroduceLocalExtension.md)
**问题：** 一个实用程序类不包含您需要的一些方法。但您不能将这些方法添加到该类中。
**解决方案：** 创建一个包含这些方法的新类，并使其成为实用程序类的子类或包装器。
