# 内联临时变量（Inline Temp）

## 问题
存在一个临时变量，只赋值了一个简单表达式的结果，而无其他用途。

## 解决方案
用表达式本身替换对变量的引用。


```
def hasDiscount(order):
    basePrice = order.basePrice()
    return basePrice > 1000
```

```
def hasDiscount(order):
    return order.basePrice() > 1000
```

# 为何进行重构

内联局部变量几乎总是作为“用查询替换临时变量”或为“提取方法”铺平道路的一部分而使用。

## 好处

这种重构技术本身几乎没有什么好处。然而，如果变量被赋值为方法的结果，通过摆脱不必要的变量，可以在一定程度上提高程序的可读性。

## 缺点

有时，看似无用的临时变量用于缓存昂贵操作的结果，该结果在多个地方被重复使用。因此，在使用此重构技术之前，请确保简单性不会以性能为代价。

## 如何进行重构

1. 找到所有使用该变量的地方。不使用变量，而是使用先前赋给它的表达式。

2. 删除变量的声明及其赋值行。