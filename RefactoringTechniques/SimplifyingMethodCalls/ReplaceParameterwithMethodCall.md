# 用方法调用替换参数

## 问题

调用查询方法并将其结果作为另一个方法的参数传递，而该方法本身可以直接调用该查询。

## 解决方案

尝试在方法体内部进行查询调用，而不是通过参数传递值。

```java
// 改前
int basePrice = quantity * itemPrice;
double seasonDiscount = this.getSeasonalDiscount();
double fees = this.getFees();
double finalPrice = discountedPrice(basePrice, seasonDiscount, fees);

// 改后
int basePrice = quantity * itemPrice;
double finalPrice = discountedPrice(basePrice);
```

## 为什么重构

长参数列表难以理解。此外，对这些方法的调用通常类似于一系列级联，具有曲折而令人兴奋的值计算，难以导航，但必须传递给方法。因此，如果可以使用方法计算参数值，请在方法内部进行计算并摆脱参数。

## 优势

摆脱不必要的参数并简化方法调用。这些参数通常不是为当前项目创建的，而是为未来可能永远不会出现的需要而创建的。

## 缺点

将来可能需要参数用于其他需求...这可能迫使你重写方法。

## 如何重构

确保获取值的代码不使用当前方法的参数，因为在另一个方法内部将无法使用它们。如果是这样，移动代码是不可能的。

如果相关代码比单个方法或函数调用复杂，请使用“提取方法”将此代码隔离在新方法中，并使调用变得简单。

在主方法的代码中，将所有对正在替换的参数的引用替换为获取该值的方法的调用。

使用“移除参数”来消除现在未使用的参数。