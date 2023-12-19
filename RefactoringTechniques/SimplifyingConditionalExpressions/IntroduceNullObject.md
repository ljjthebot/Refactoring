# 引入空对象

## 问题
由于某些方法返回null而不是真实对象，您的代码中有许多对null的检查。

## 解决方案
不要返回null，而是返回一个表现默认行为的空对象。

```java
// Java示例
if (customer == null) {
  plan = BillingPlan.basic();
}
else {
  plan = customer.getPlan();
}
```

```

class NullCustomer extends Customer {
  boolean isNull() {
    return true;
  }
  Plan getPlan() {
    return new NullPlan();
  }
  // Some other NULL functionality.
}

// 用空对象替换null值。
customer = (order.customer != null) ?
  order.customer : new NullCustomer();

// 将空对象用作正常子类。
plan = customer.getPlan();
```

## 为什么要重构
数十个对null的检查会使您的代码变得更加冗长且难以阅读。

## 缺点
摆脱条件语句的代价是创建一个新的类。

## 如何重构
1. 从涉及的类中创建一个子类，该子类将执行空对象的角色。
2. 在两个类中都创建`isNull()`方法，该方法对于空对象返回true，对于真实类返回false。
3. 查找代码可能返回null而不是真实对象的所有地方。更改代码，使其返回一个空对象。
4. 查找与null比较真实类的变量的所有地方。将这些检查替换为调用`isNull()`。
5. 如果在这些条件语句中运行原始类的方法时，值不等于null，请重新定义这些方法以在空类中插入条件的else部分中插入代码。然后，您可以删除整个条件语句，并通过多态性实现不同的行为。
6. 如果情况不那么简单，方法无法重新定义，请看看是否可以将本应在空值情况下执行的运算符简单提取到空对象的新方法中。在else中调用这些方法作为默认操作。
```