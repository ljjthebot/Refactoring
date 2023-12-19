# 内联方法（Inline Method）

## 问题
当方法体比方法本身更明显时，使用此技术。

## 解决方案
用对方法的调用替换为方法的内容，并删除方法本身。


```Python
class PizzaDelivery:
    # ...
    def getRating(self):
        return 2 if self.moreThanFiveLateDeliveries() else 1
  
    def moreThanFiveLateDeliveries(self):
        return self.numberOfLateDeliveries > 5
```

```Python
class PizzaDelivery:
  # ...
  def getRating(self):
    return 2 if self.numberOfLateDeliveries > 5 else 1
```     

## 为何进行重构

一个方法仅仅是委托给另一个方法。单独看，这种委托并不是问题。但是当存在许多这样的方法时，它们变成了一个令人困惑的纠结，难以梳理。

通常情况下，方法最初可能并不是太短，但随着对程序的更改而变得短小起来。因此，不要犹豫于摆脱那些已经失去用处的方法。

## 好处

通过最小化不必要的方法数量，使代码更为直观。

## 如何进行重构

1. 确保该方法没有在子类中重新定义。如果方法被重新定义，请避免使用此技术。

2. 查找对该方法的所有调用。将这些调用替换为方法的内容。

3. 删除该方法。
