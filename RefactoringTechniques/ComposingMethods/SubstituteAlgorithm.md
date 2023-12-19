# 替代算法（Substitute Algorithm）

## 问题
想要用一个新算法替代原有的算法。

## 解决方案
用新算法替代原有算法的实现。


```
def foundPerson(people):
    for i in range(len(people)):
        if people[i] == "Don":
            return "Don"
        if people[i] == "John":
            return "John"
        if people[i] == "Kent":
            return "Kent"
    return ""
```

```
def foundPerson(people):
    candidates = ["Don", "John", "Kent"]
    return people if people in candidates else ""
```

## 为何进行重构

逐步重构并非改进程序的唯一方法。有时，一个方法中存在的问题如此严重，以至于更容易将该方法拆分并重新开始。也许您已经找到了一个更简单、更高效的算法。如果是这样，您应该简单地用新算法替换旧算法。

随着时间的推移，您的算法可能会被合并到一个知名库或框架中，而您希望摆脱独立实现，以简化维护工作。

程序的需求可能会发生如此巨大的变化，以至于现有算法无法满足任务的要求。

## 如何进行重构

1. 确保您已经尽可能简化了现有算法。使用“提取方法”将不重要的代码移到其他方法中。算法中的移动部分越少，替换就越容易。

2. 在一个新的方法中创建您的新算法。用新算法替换旧算法并开始测试程序。

3. 如果结果不符，请返回旧实现并比较结果。识别差异的原因。虽然原因通常是旧算法中的错误，但更有可能是新算法中的某些问题。

4. 当所有测试都成功完成时，彻底删除旧算法！
