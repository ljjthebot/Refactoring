# 用方法对象替换方法（Replace Method with Method Object）

## 问题
存在一个长方法，其中本地变量纠缠在一起，无法应用“提取方法”。

## 解决方案
将方法转化为一个独立的类，使得本地变量成为类的字段。然后，可以在同一类内将方法拆分为多个方法。


```
class Order:
    # ...
    def price(self):
        primaryBasePrice = 0
        secondaryBasePrice = 0
        tertiaryBasePrice = 0
        # Perform long computation.
```


```
class Order:
    # ...
    def price(self):
        return PriceCalculator(self).compute()


class PriceCalculator:
    def __init__(self, order):
        self._primaryBasePrice = 0
        self._secondaryBasePrice = 0
        self._tertiaryBasePrice = 0
        # Copy relevant information from the
        # order object.

    def compute(self):
        # Perform long computation.
```

## 为何进行重构

方法过长，由于本地变量相互交织在一起，很难将其分离。

第一步是将整个方法隔离到一个单独的类中，并将其本地变量变成类的字段。

首先，这允许在类级别上隔离问题。其次，它为将一个庞大且笨重的方法拆分成更小的方法铺平了道路，这些方法原始类的目的可能无法容纳。

## 好处

将一个长方法隔离到自己的类中可以阻止该方法变得庞大。这还允许在类内将其拆分为子方法，而无需在原始类中添加实用方法。

## 缺点

添加了另一个类，增加了程序的总体复杂性。

## 如何进行重构

1. 创建一个新类。根据正在重构的方法的目的进行命名。

2. 在新类中，创建一个私有字段，用于存储对先前位于方法中的类的实例的引用。如果需要，可以用它从原始类中获取一些必需的数据。

3. 为方法的每个本地变量创建一个单独的私有字段。

4. 创建一个构造函数，接受方法的所有本地变量的值作为参数，并初始化相应的私有字段。

5. 声明主方法，并将原始方法的代码复制到其中，将本地变量替换为私有字段。

6. 通过创建一个方法对象并调用其主方法来替换原始类中原始方法的主体。
