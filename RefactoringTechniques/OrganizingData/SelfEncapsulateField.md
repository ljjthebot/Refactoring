# 自我封装字段

自我封装与普通的字段封装不同：这里介绍的重构技术是针对私有字段执行的。

## 问题

在类内部直接访问私有字段。

## 解决方案

为字段创建一个 getter 和 setter，然后只使用它们来访问字段。

```
class Range {
  private int low, high;
  boolean includes(int arg) {
    return arg >= low && arg <= high;
  }
}

```

```
class Range {
  private int low, high;
  boolean includes(int arg) {
    return arg >= getLow() && arg <= getHigh();
  }
  int getLow() {
    return low;
  }
  int getHigh() {
    return high;
  }
}
```

## 为何要进行重构

有时，在类内部直接访问私有字段并不够灵活。您可能希望在进行第一次查询时初始化字段值，或者在分配新值时对字段执行某些操作，或者在子类中以各种方式执行所有这些操作。

## 优势

间接访问字段是通过访问方法（getter 和 setter）对字段进行操作。这种方法比直接访问字段更加灵活。

首先，您可以在设置或接收字段数据时执行复杂的操作。懒初始化和字段值验证可以轻松地在字段的 getter 和 setter 中实现。

其次，更为关键的是，您可以在子类中重新定义 getter 和 setter。

您可以选择根本不实现字段的 setter。字段值仅在构造函数中指定，从而使字段在整个对象生命周期内无法更改。

## 缺点

当使用直接访问字段时，代码看起来更简单、更易读，尽管灵活性减弱。

## 如何进行重构

1. 为字段创建一个 getter（和可选的 setter）。它们应该是受保护的或公共的。

2. 找到对字段的所有直接调用，并将它们替换为 getter 和 setter 的调用。