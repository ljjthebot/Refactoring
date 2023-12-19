# 添加参数

## 问题

方法缺乏执行某些操作所需的数据。

## 解决方案

创建一个新参数以传递必要的数据。

### 添加参数 - 改前

### 添加参数 - 改后

## 为什么重构

当需要对一个方法进行更改，而这些更改需要添加先前不可用的信息或数据时。

## 优势

在添加新参数和添加一个包含方法所需数据的新私有字段之间进行选择。当你需要一些偶尔或经常变化的数据，而没有必要一直保存在对象中时，使用参数是更好的选择。在这种情况下，重构将是划算的。否则，添加一个私有字段，并在调用方法之前填充它。

## 缺点

添加新参数总是比删除它更容易，这就是为什么参数列表经常膨胀到令人发指的大小的原因。这种味道被称为长参数列表。

如果需要添加新参数，有时这意味着你的类不包含必要的数据，或者现有的参数不包含必要的相关数据。在这两种情况下，最好的解决方案是考虑将数据移动到主类或其他类中，这些类的对象已经可以从方法内部访问。

## 如何重构

1. 查看方法是否在超类或子类中定义。如果方法存在于这些类中，你需要在这些类中重复所有步骤。

2. 下一个步骤是在重构过程中保持程序功能的关键步骤。通过复制旧方法并向其添加必要的参数来创建一个新方法。将旧方法的代码替换为对新方法的调用。你可以将任何值插入新参数（例如，对于对象可以是null，对于数字可以是零）。

3. 查找对旧方法的所有引用并将它们替换为对新方法的引用。

4. 删除旧方法。如果旧方法是公共接口的一部分，则无法执行此步骤。在这种情况下，将旧方法标记为已弃用。