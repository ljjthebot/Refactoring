# 长方法
## 征兆与症状
一个方法包含了太多行的代码。通常来说，方法超过十行都应该让你提出疑问。

## 成因
就像《加州旅馆》一样，总是在一个方法中添加东西，但从不删除。由于写比阅读代码容易，直到代码变成一个又丑、又大的怪物时才被察觉到。

从心理上讲，与其创建一个新方法，不如在现有方法中添加代码更快：“只有两行代码，不至于单独创建一个方法吧…” 这意味着又添加了一行，然后又添加了一行，最终形成了一团意义不明的代码。

## 处理方法
作为一个经验法则，如果你感觉有必要在方法内部注释，你应该将这段代码放入一个新的方法中。即使是一行代码。如果方法有一个描述性的名称，无需查看代码，也能了解它的功能。

- **为了缩短方法体的长度，使用提取方法（[Extract Method](../../RefactoringTechniques/ComposingMethods/Extract.md)）。**

如果局部变量和参数妨碍提取方法，使用替换临时变量（[Replace Temp with Query](../../RefactoringTechniques/ComposingMethods/ReplaceTempwithQuery.md)）、引入参数对象（Introduce Parameter Object）或保留整个对象（Preserve Whole Object）。

如果前述的方法都不起作用，尝试通过用方法对象替换方法（Replace Method with Method Object）将整个方法移动到一个单独的对象中。

条件运算符和循环是代码可以移动到一个单独方法的明显线索。对于条件语句，使用分解条件表达式（Decompose Conditional）。如果循环阻碍了，尝试提取方法（Extract Method）。

## 回报
在所有类型的面向对象的代码中，拥有短方法的类存在时间最长。方法或函数越长，理解和维护它就变得越困难。

此外，长方法为不需要的重复代码提供了完美的藏身之处。

## 性能
许多人声称，方法数量的增加会影响性能吗？在几乎所有情况下，影响是如此微不足道，甚至不值得担忧。

而且，现在你有了清晰易懂的代码，如果真的需要，你更有可能找到真正有效的方法来重构代码并获得实际的性能收益。
