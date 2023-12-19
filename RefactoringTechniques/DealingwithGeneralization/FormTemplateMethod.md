# 形成模板方法
## 问题
您的子类实现的算法包含相同顺序的相似步骤。

## 解决方案
将算法结构和相同步骤移动到超类中，将不同步骤的实现留在子类中。

## 形成模板方法 - 之前
[形成模板方法 - 之前]

## 形成模板方法 - 之后
[形成模板方法 - 之后]

## 为什么要重构
子类是并行开发的，有时由不同的人编写，这导致了代码重复，错误以及代码维护的困难，因为每个更改都必须在所有子类中进行。

## 好处
代码重复并不总是指简单的复制/粘贴情况。通常，重复发生在更高层次，例如当您有一个用于排序数字的方法和一个用于排序仅通过元素比较而有所不同的对象集合的方法时。通过创建一个模板方法，通过在超类中合并共享的算法步骤，仅在子类中留下差异来消除此重复。

形成模板方法是开闭原则在实践中的一个示例。当出现新的算法版本时，您只需创建一个新的子类；不需要对现有代码进行更改。

## 如何重构
1. 将子类中的算法拆分为描述在单独方法中的组成部分。使用“Extract Method”可以帮助完成此操作。
2. 通过“Pull Up Method”将对所有子类都相同的结果方法移到超类中。
3. 通过“Rename Method”为不相似的方法提供一致的名称。
4. 通过使用“Pull Up Method”将不相似方法的签名移到超类中，将它们的实现留在子类中。
5. 最后，通过“Pull Up Method”将算法的主要方法移到超类中。现在，它应该与超类中描述的实际和抽象的方法步骤一起工作。