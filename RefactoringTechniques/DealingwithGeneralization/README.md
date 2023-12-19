# 处理泛化

抽象化有一组自己的重构技术，主要涉及沿类继承层次结构移动功能，创建新的类和接口，以及替换继承与委托之间的关系，反之亦然。

## [Pull Up Field](PullUpField.md)
**问题：** 两个类有相同的字段。

**解决方案：** 从子类中删除字段，并将其移到超类中。

## [Pull Up Method](PullUpMethod.md)
**问题：** 您的子类具有执行相似工作的方法。

**解决方案：** 使这些方法相同，然后将它们移到相关的超类中。

## [Pull Up Constructor Body](PullUpConstructorBody.md)
**问题：** 您的子类具有构造函数，其中的代码大部分相同。

**解决方案：** 创建一个超类构造函数，并将在子类中相同的代码移到其中。在子类构造函数中调用超类构造函数。

## [Push Down Method](PushDownField.md)
**问题：** 行为在超类中实现，只被一个（或几个）子类使用？

**解决方案：** 将此行为移动到子类中。

## [Push Down Field](PushDownMethod.md)
**问题：** 一个字段仅在几个子类中使用？

**解决方案：** 将字段移到这些子类中。

## [Extract Subclass](ExtractSubclass.md)
**问题：** 一个类具有仅在某些情况下使用的特性。

**解决方案：** 创建一个子类，并在这些情况下使用它。

## [Extract Superclass](ExtractSuperclass.md)
**问题：** 您有两个具有共同字段和方法的类。

**解决方案：** 为它们创建一个共享的超类，并将所有相同的字段和方法移到其中。

## [Extract Interface](ExtractInterface.md)
**问题：** 多个客户端正在使用类接口的相同部分。另一种情况：两个类的接口的一部分是相同的。

**解决方案：** 将这部分相同的接口移到其自己的接口中。

## [Collapse Hierarchy](CollapseHierarchy.md)
**问题：** 您有一个类层次结构，其中一个子类几乎与其超类相同。

**解决方案：** 合并子类和超类。

## [Form Template Method](FormTemplateMethod.md)
**问题：** 您的子类实现了包含相似步骤的算法，步骤的顺序相同。

**解决方案：** 将算法结构和相同步骤移动到一个超类中，将不同步骤的实现留在子类中。

## [Replace Inheritance with Delegation](ReplaceInheritancewithDelegation.md)
**问题：** 一个子类仅使用其超类的一部分方法（或不可能继承超类数据）。

**解决方案：** 创建一个字段，并在其中放置一个超类对象，将方法委托给超类对象，并摆脱继承。

## [Replace Delegation with Inheritance](ReplaceDelegationwithInheritance.md)
**问题：** 一个类包含许多简单的方法，这些方法都委托给另一个类的所有方法。

**解决方案：** 将该类变为一个委托继承者，这使得委托方法变得不必要。