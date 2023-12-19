# 重构：用符号常量替换魔法数

## 问题

您的代码使用一个具有特定含义的数字。

## 解决方案

用一个具有人类可读名称的常量替换这个数字，以解释该数字的含义。

### 重构前
```java
double potentialEnergy(double mass, double height) {
  return mass * height * 9.81;
}
```

### 重构后
```java
static final double GRAVITATIONAL_CONSTANT = 9.81;

double potentialEnergy(double mass, double height) {
  return mass * height * GRAVITATIONAL_CONSTANT;
}
```

## 为何要进行重构

魔法数是源代码中遇到的一个具有特定含义但并不明显的数值。这种“反模式”使得理解程序和重构代码更加困难。

当需要更改此魔法数时，会遇到更多困难。查找和替换不适用于此：相同的数字可能在不同的地方用于不同的目的，这意味着您必须验证使用此数字的每一行代码。

## 优势

符号常量可以作为值含义的活文档。

更改常量的值要比在整个代码库中搜索此数字容易得多，而不会意外更改其他地方用于不同目的的相同数字。

减少在代码中重复使用数字或字符串。当值复杂而长时，这一点尤其重要（例如 3.14159 或 0xCAFEBABE）。

## 注意事项

并非所有数字都是魔法的。

如果数字的目的很明显，则无需替换它。经典示例是：

```java
for (i = 0; i < count; i++) { ... }
```

## 替代方案

有时可以用方法调用替换魔法数。例如，如果您有一个表示集合中元素数量的魔法数，则无需使用它来检查集合的最后一个元素。而是使用获取集合长度的标准方法。

有时，魔法数被用作类型代码。假设您有两种类型的用户，并且在类中使用数字字段来指定它们是哪一种：管理员是 1，普通用户是 2。

在这种情况下，应使用以下其中一种重构方法来避免类型代码：

- 用类替换类型代码（Replace Type Code with Class）
- 用子类替换类型代码（Replace Type Code with Subclasses）
- 用状态/策略替换类型代码（Replace Type Code with State/Strategy）

## 如何进行重构

1. 声明一个常量并将魔法数的值分配给它。

2. 查找魔法数的所有提及。

3. 对于找到的每个数字，请仔细检查此特定情况中的魔法数是否对应于常量的目的。如果是，请用常量替换该数字。这是一个重要的步骤，因为相同的数字可能表示完全不同的事物（并且分别替换为不同的常量，视情况而定）。