# 临时字段

## 迹象和症状

临时字段仅在特定情况下获取其值（因此仅在对象需要时），在这些情况之外，它们是空的。

## 问题原因

通常，临时字段是为了在需要大量输入的算法中使用而创建的。因此，程序员决定在类中为这些数据创建字段，而不是在方法中创建大量的参数。这些字段仅在算法中使用，在其他时间未被使用。

这种代码很难理解。你期望在对象字段中看到数据，但由于某种原因，它们几乎总是为空。

## 处理方法

可以通过提取类（Extract Class）将临时字段及其所有操作代码放入一个单独的类中。换句话说，你正在创建一个方法对象，达到与执行用方法对象替换方法（Replace Method with Method Object）相同的结果。

引入Null对象（Introduce Null Object）并将其整合到原来用于检查临时字段值存在性的条件代码的位置。

## 收益

更好的代码清晰度和组织结构。