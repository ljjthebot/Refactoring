# 提取变量（Extract Variable）

## 问题
存在一个难以理解的表达式。

## 解决方案
将表达式或其部分放入单独的、易于理解的变量中。

```Python
def renderBanner(self):
    if (self.platform.toUpperCase().indexOf("MAC") > -1) and \
       (self.browser.toUpperCase().indexOf("IE") > -1) and \
       self.wasInitialized() and (self.resize > 0):
        # do something
```

```
def renderBanner(self):
    isMacOs = self.platform.toUpperCase().indexOf("MAC") > -1
    isIE = self.browser.toUpperCase().indexOf("IE") > -1
    wasResized = self.resize > 0

    if isMacOs and isIE and self.wasInitialized() and wasResized:
        # do something
```

# 为何进行重构

提取变量的主要原因是通过将复杂表达式分解为其中间部分，使其更易理解。这些部分可能是：

- `if()` 操作符的条件或在基于 C 的语言中的 `?:` 操作符的一部分
- 没有中间结果的长算术表达式
- 长的多部分行

如果你发现提取的表达式在代码的其他地方被使用，提取变量可能是执行提取方法的第一步。

## 好处

- 更易读的代码！尽量为提取的变量取一个能够清晰宣告变量目的的好名字。更易读，少一些啰嗦的注释。选择像 `customerTaxValue`、`cityUnemploymentRate`、`clientSalutationString` 等这样的名称。

## 缺点

- 代码中存在更多的变量。但这可以通过更容易阅读的代码来抵消。

- 在重构条件表达式时，请记住编译器很可能会进行优化，以最小化建立结果值所需的计算量。例如，如果有以下表达式 `if (a() || b())`... 当方法 `a` 返回 `true` 时，程序不会调用方法 `b`，因为结果值仍将是 `true`，不管 `b` 返回什么值。

然而，如果将此表达式的部分提取为变量，则这两个方法将始终被调用，这可能会影响程序的性能，特别是如果这些方法执行一些繁重的工作。

## 如何进行重构

1. 在相关表达式之前插入一行，并在那里声明一个新变量。将复杂表达式的一部分赋值给此变量。

2. 用新变量替换表达式的那部分内容。

3. 对表达式的所有复杂部分重复这个过程。
