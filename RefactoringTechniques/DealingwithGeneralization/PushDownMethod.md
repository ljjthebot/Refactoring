# Push Down Method

## 问题
在超类中实现的行为只由一个（或几个）子类使用？

## 解决方案
将此行为移到子类中。

### Push Down Method - Before
```java
class Animal {
  void makeSound() {
    // Common implementation for all animals
  }
}

class Cat extends Animal {
  // ...
}

class Dog extends Animal {
  void makeSound() {
    // Dog-specific implementation
  }
}
```

### Push Down Method - After
```java
class Animal {
  void makeSound() {
    // Common implementation for all animals
  }
}

class Cat extends Animal {
  // Cat-specific implementation
}

class Dog extends Animal {
  // ...
}
```

## 为什么重构
最初，某个方法被设计为适用于所有类，但实际上只在一个子类中使用。当计划中的功能未能实现时，就会出现这种情况。

在部分提取（或移除）类层次结构的功能后，可能会留下仅在一个子类中使用的方法，也可能出现这种情况。

如果您发现一个方法被多个子类需要，但不是全部子类，可能有必要创建一个中间子类，并将方法移到其中。这样可以避免将方法下推到所有子类中导致的代码重复。

## 优势
提高类的一致性。方法位于您期望看到它的位置。

## 如何重构
1. 在子类中声明方法，并从超类中复制其代码。
2. 从超类中删除该方法。
3. 查找使用该方法的所有位置，并验证它是否从必要的子类调用。