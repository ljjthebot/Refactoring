# 条件分解

## 问题
您有一个复杂的条件语句（if-then/else或switch）。

## 解决方案
将条件语句的复杂部分分解为单独的方法：条件部分、then部分和else部分。

```java
// Java示例
if (date.before(SUMMER_START) || date.after(SUMMER_END)) {
  charge = quantity * winterRate + winterServiceCharge;
}
else {
  charge = quantity * summerRate;
}

```


```java
// 分解后的Java示例
if (isSummer(date)) {
  charge = summerCharge(quantity);
}
else {
  charge = winterCharge(quantity);
}
```

## 为什么要重构
代码越长，理解起来就越困难。当代码充满条件语句时，理解变得更加困难：

- 在忙于弄清楚then块中的代码时，可能会忘记相关的条件是什么。
- 在解析else块时，可能会忘记then块中的代码是做什么的。

## 好处
通过将有条件的代码提取到具有清晰名称的方法中，您使将来维护代码的人（比如说，两个月后的您）的生活变得更容易。

这种重构技术也适用于条件语句中的短表达式。字符串`isSalaryDay()`比用于比较日期的代码更漂亮和更具描述性。

## 如何重构
通过“提取方法”（Extract Method）将条件语句提取到单独的方法中。

然后，对then块和else块重复此过程。
```