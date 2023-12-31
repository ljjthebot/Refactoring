# 重命名方法

## 问题

方法的名称未能说明方法的功能。

## 解决方案

重新命名方法。

### 重命名方法 - 改前

### 重命名方法 - 改后

## 为什么重构

也许一个方法从一开始就命名得不好，例如，有人匆忙创建了这个方法，并没有妥善命名它。

或者，该方法一开始命名得很好，但随着功能的增长，方法的名称不再是一个良好的描述符。

## 优势

提高代码可读性。尽量给新方法取一个反映其功能的名称，比如 `createOrder()`，`renderCustomerInfo()` 等。

## 如何重构

1. 查看方法是否在超类或子类中定义。如果是的话，你必须在这些类中重复所有步骤。

2. 下一个方法是在重构过程中保持程序功能的重要方法。创建一个新方法并为其取一个新名称。将旧方法的代码复制到新方法中。删除旧方法的所有代码，然后在其位置插入对新方法的调用。

3. 查找所有对旧方法的引用并将它们替换为对新方法的引用。

4. 删除旧方法。如果旧方法是公共接口的一部分，则不要执行此步骤。相反，将旧方法标记为已弃用。