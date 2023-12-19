# 用显式方法替换参数

## 问题

一个方法分成多个部分，每个部分根据参数的值运行。

## 解决方案

将方法的各个部分提取为独立的方法，并调用它们而不是原始方法。

```java
// 改前
void setValue(String name, int value) {
  if (name.equals("height")) {
    height = value;
    return;
  }
  if (name.equals("width")) {
    width = value;
    return;
  }
  Assert.shouldNeverReachHere();
}
```

```
// 改后
void setHeight(int arg) {
  height = arg;
}

void setWidth(int arg) {
  width = arg;
}
```

## 为什么重构

包含参数依赖变体的方法变得庞大。每个分支中运行了非平凡的代码，并且很少添加新的变体。

## 优势

提高代码可读性。比如，理解 `startEngine()` 方法的目的比理解 `setValue("engineEnabled", true)` 要容易得多。

## 不适用情况

如果一个方法很少更改，而且在其中不经常添加新的变体，就不要用显式方法替换参数。

## 如何重构

1. 为方法的每个变体创建一个独立的方法。在主方法中根据参数的值运行这些方法。

2. 找到调用原始方法的所有地方。在这些地方，用新的依赖参数的变体调用它们。

3. 当不再存在对原始方法的调用时，删除它。