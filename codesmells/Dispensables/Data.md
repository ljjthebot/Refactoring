# 数据类

## 迹象和症状

数据类是指只包含字段和简陋的用于访问它们的方法（getter和setter）的类。这些类仅仅是其他类使用的数据容器。这些类不包含任何额外的功能，并且不能独立地对它们拥有的数据进行操作。

## 问题原因

当一个新创建的类只包含几个公共字段（甚至可能是一些getter/setter）时，这是一种正常情况。但对象的真正力量在于它们可以包含行为类型或对其数据的操作。

## 处理方法

- 如果一个类包含公共字段，请使用封装字段（Encapsulate Field）将它们隐藏，要求只能通过getter和setter进行访问。
- 对于存储在集合中的数据（如数组），使用封装集合（Encapsulate Collection）。
- 检查使用该类的客户端代码。在其中，您可能会发现最好放在数据类本身的功能。如果是这种情况，请使用移动方法（Move Method）和提取方法（Extract Method）将此功能迁移到数据类中。
- 在类填充了经过深思熟虑的方法之后，您可能希望摆脱为数据访问提供过于宽泛的访问权限的旧方法。为此，可以使用移除设置方法（Remove Setting Method）和隐藏方法（Hide Method）。

## 收益

提高了对代码的理解和组织。特定数据的操作现在聚集在一个地方，而不是在整个代码中随意分散。

帮助您发现客户端代码的重复。
