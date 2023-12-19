# 用测试替代异常

## 问题
在一个简单的测试可以完成工作的地方，您抛出了一个异常？

## 解决方案
将异常替换为条件测试。

### Java
```java
double getValueForPeriod(int periodNumber) {
  try {
    return values[periodNumber];
  } catch (ArrayIndexOutOfBoundsException e) {
    return 0;
  }
}
```
```

double getValueForPeriod(int periodNumber) {
  if (periodNumber >= values.length) {
    return 0;
  }
  return values[periodNumber];
}
```

## 为什么重构
异常应该用于处理与意外错误相关的不规则行为。它们不应该用作测试的替代品。如果可以通过简单地在运行之前验证条件来避免异常，则应该这样做。异常应该保留给真正的错误。

例如，您进入了一个雷区并触发了那里的一颗地雷，导致异常；异常被成功处理，您被抬升到雷场之外的安全地带。但是通过简单地阅读雷区前面的警告标志，您本可以避免这一切。

## 优势
有时一个简单的条件语句可能比异常处理代码更明显。

## 如何重构
1. 为边缘情况创建一个条件测试，并将其移到try/catch块之前。
2. 将catch部分内的代码放入这个条件中。
3. 在catch部分中，放置用于抛出通常的未命名异常的代码，并运行所有测试。
4. 如果在测试期间没有抛出异常，则删除try/catch运算符。