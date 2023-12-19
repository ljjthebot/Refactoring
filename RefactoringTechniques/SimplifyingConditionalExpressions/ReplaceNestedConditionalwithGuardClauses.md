# 使用守卫子句替换嵌套条件

## 问题
您有一组嵌套条件，很难确定代码执行的正常流程。

## 解决方案
将所有特殊检查和边缘情况分离到单独的子句中，并将它们放在主要检查之前。理想情况下，您应该有一个按顺序排列的“平坦”条件列表。

```java
// Java示例
public double getPayAmount() {
  double result;
  if (isDead){
    result = deadAmount();
  }
  else {
    if (isSeparated){
      result = separatedAmount();
    }
    else {
      if (isRetired){
        result = retiredAmount();
      }
      else{
        result = normalPayAmount();
      }
    }
  }
  return result;
}
```

```
public double getPayAmount() {
  if (isDead){
    return deadAmount();
  }
  if (isSeparated){
    return separatedAmount();
  }
  if (isRetired){
    return retiredAmount();
  }
  return normalPayAmount();
}
```

## 为什么要重构
识别“地狱般的条件”相对容易。每个嵌套级别的缩进形成一个箭头，指向痛苦和苦难的方向：

```java
if () {
    if () {
        do {
            if () {
                if () {
                    if () {
                        ...
                    }
                }
                ...
            }
            ...
        }
        while ();
        ...
    }
    else {
        ...
    }
}
```

很难弄清楚每个条件语句的作用以及如何工作，因为代码执行的“正常”流程并不立即显而易见。这些条件语句表明了杂乱无章的演变，每个条件都是作为权宜之计添加的，没有考虑优化整体结构。

为简化情况，将特殊情况分离到单独的条件中，如果守卫子句为真，则立即结束执行并返回空值。实际上，您的任务是使结构平坦。

## 如何重构
尽量消除代码的副作用，这里“将查询与修改分离”可能有助于达到目的。这个解决方案对于下面描述的重排是必要的。

将所有导致调用异常或立即返回值的守卫子句分离出来。将这些条件放在方法的开头。

在重新排列完成并且所有测试都成功完成后，看看是否可以对导致相同异常或返回值的守卫子句使用“合并条件表达式”。
