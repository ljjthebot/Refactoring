# 代码异味

- **什么？代码怎么会 "有味道"？**
- **嗯，它没有鼻子... 但它确实可能很臭！**

## [死肥仔](bloaters/README.md)

死肥仔是指代码、方法和类的规模变得非常庞大，以至于难以处理。通常，这些异味不会立即显现，而是随着程序的演化而积累（尤其是没有人努力根除它们时）。

- **[长方法](bloaters/LongMethod.md)**
- **[大类](bloaters/LargeClass.md)**
- **[滥用基本类型](bloaters/primitiveObsession.md)**
- **[多参数](bloaters/LongParaList.md)**
- **[数据集聚](bloaters/DataClumps.md)**

## [面向对象滥用者](Object-OrientationAbusers/README.md)

所有这些异味都是面向对象编程原则的不完整或不正确应用。

- **[具有不同接口的替代类](Object-OrientationAbusers/Alternative.md)**
- **[被拒绝的继承](Object-OrientationAbusers/Refused.md)**
- **[开关语句](Object-OrientationAbusers/SwitchStatements.md)**
- **[临时字段](Object-OrientationAbusers/Temporary.md)**

## [阻止变更者](Change/README.md)

这些异味意味着如果你需要在代码的一个地方进行更改，你还必须在其他地方进行许多更改。由此导致程序开发变得更加复杂和昂贵。

- **[发散性变更](Change/Divergent.md)**
- **[并行继承体系](Change/Parallel.md)**
- **[散弹手术](Change/Shotgun.md)**

## [可弃用者](Dispensables/README.md)

可弃用者是指一些毫无意义且不必要的东西，如果去掉它们，代码会变得更清晰、更高效和更易于理解。

- **[注释](Dispensables/Comments.md)**
- **[重复代码](Dispensables/Duplicate.md)**
- **[数据类](Dispensables/Data.md)**
- **[死代码](Dispensables/Dead.md)**
- **[懒惰类](Dispensables/Lazy.md)**
- **[猜测性泛化](Dispensables/Speculative.md)**

## [耦合者](Couplers/README.md)

这个组中的所有异味都促使类之间的耦合过度或展示了如果通过过度委托替代耦合会发生什么。

- **[特征嫉妒](Couplers/Feature.md)**
- **[不适当的亲密关系](Couplers/Inappropriate.md)**
- **不完整的库类**
- **[消息链](Couplers/Message.md)**
- **[中间者](Couplers/Middle.md)**
