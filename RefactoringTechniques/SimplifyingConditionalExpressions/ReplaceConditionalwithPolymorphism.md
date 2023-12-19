
# 使用多态替换条件表达式

## 问题
您有一个条件表达式，根据对象类型或属性执行各种操作。

## 解决方案
创建与条件表达式中的分支匹配的子类。在这些子类中，创建一个共享方法，并将条件表达式相应分支的代码移动到该方法中。然后，用相关的方法调用替换条件表达式。结果是根据对象类别实现多态性，获得正确的实现。

```java
// Java示例
class Bird {
  // ...
  double getSpeed() {
    switch (type) {
      case EUROPEAN:
        return getBaseSpeed();
      case AFRICAN:
        return getBaseSpeed() - getLoadFactor() * numberOfCoconuts;
      case NORWEGIAN_BLUE:
        return (isNailed) ? 0 : getBaseSpeed(voltage);
    }
    throw new RuntimeException("Should be unreachable");
  }
}
```

```
abstract class Bird {
  // ...
  abstract double getSpeed();
}

class European extends Bird {
  double getSpeed() {
    return getBaseSpeed();
  }
}

class African extends Bird {
  double getSpeed() {
    return getBaseSpeed() - getLoadFactor() * numberOfCoconuts;
  }
}

class NorwegianBlue extends Bird {
  double getSpeed() {
    return (isNailed) ? 0 : getBaseSpeed(voltage);
  }
}

// 在客户端代码的某处
speed = bird.getSpeed();
```

## 为什么要重构
如果您的代码包含根据对象的以下因素执行各种任务的运算符：

- 对象实现的类或接口
- 对象字段的值
- 对象方法调用的结果

那么这种重构技术可以帮助您。如果出现新的对象属性或类型，则需要在所有类似的条件表达式中搜索并添加代码。因此，如果在对象的所有方法中散布着多个条件表达式，则此技术的好处将倍增。

## 好处
这种技术遵循“告诉别问”原则：与其询问对象的状态，然后根据这个状态执行操作，不如直接告诉对象它需要做什么，让它自己决定如何做。

消除重复的代码。您摆脱了许多几乎相同的条件表达式。

如果需要添加新的执行变体，您只需添加一个新的子类，而无需触及现有代码（开闭原则）。

## 如何重构
### 准备重构
对于这种重构技术，您应该准备一个包含替代行为的类层次结构。如果没有这样的层次结构，请创建一个。其他技术将有助于实现这一目标：

- 使用子类替代类型码。将为特定对象属性的所有值创建子类。这种方法简单但不够灵活，因为您无法为对象的其他属性创建子类。
- 使用状态/策略替代类型码。将为特定对象属性创建一个类，并从中为该属性的每个值创建子类。当前类将包含对该类型对象的引用，并将执行委托给它们。

以下步骤假定您已经创建了类层次结构。

### 重构步骤
1. 如果条件表达式位于执行其他操作的方法中，请执行“提取方法”。
2. 对于类层次结构的每个子类，请重新定义包含条件表达式的方法，并将相应条件分支的代码复制到该位置。
3. 从条件表达式中删除此分支。
4. 重复替换步骤，直到条件表达式为空。然后删除条件表达式并将方法声明为抽象的。
```