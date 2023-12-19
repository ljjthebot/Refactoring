# 膨胀代码
膨胀代码指的是在代码、方法和类别方面已经变得如此庞大，以至于难以处理。通常，这些不良特征不会立即显现出来，而是随着程序的演进而逐渐累积（特别是在没有人努力清除它们的情况下）。

## [长方法 (Long Method)](bloaters/LongMethod.md)
长方法指的是包含过多代码行的方法。通常来说，任何超过十行的方法都应该引起你的关注并开始提出问题。

## [庞大类别 (Large Class)](bloaters/LargeClass.md)
庞大类别指的是包含许多字段、方法或代码行的类别。

## [原始痴迷 (Primitive Obsession)](bloaters/primitiveObsession.md)
原始痴迷是指在简单任务中使用基本数据类型（例如货币、范围、用于电话号码的特殊字符串等），而不是使用小型对象。
还包括在编码信息中使用常量（例如使用常量 USER_ADMIN_ROLE = 1 来指代具有管理员权限的用户）。
此外，还包括在数据数组中使用字符串常量作为字段名称。

## [长参数列表(Long Parameter List)](bloaters/LongParaList.md)
指的是一个方法拥有超过三到四个参数。

## [数据团 (Data Clumps)] (bloaters/DataClumps.md)
有时代码的不同部分包含相同的变量组（例如连接到数据库的参数）。这些数据团应该被重构为它们自己的类。