# Pull Up Field

## 问题
两个类有相同的字段。

## 解决方案
从子类中删除字段，并将其移到超类中。

### Pull Up Field - Before
```java
class Parent {
  // ...
}

class Child1 extends Parent {
  private int commonField;
  // ...
}

class Child2 extends Parent {
  private int commonField;
  // ...
}
```

### Pull Up Field - After
```java
class Parent {
  protected int commonField;
  // ...
}

class Child1 extends Parent {
  // ...
}

class Child2 extends Parent {
  // ...
}
```

## 为什么重构
子类分别增长和发展，导致相同（或几乎相同）的字段和方法出现。

## 优势
消除了子类中字段的重复。

便于随后将重复的方法（如果存在）从子类移动到超类。

## 如何重构
1. 确保在子类中字段用于相同的需求。
2. 如果字段具有不同的名称，请将它们命名为相同的名称，并替换现有代码中对字段的所有引用。
3. 在超类中使用相同名称创建一个字段。请注意，如果字段是私有的，则超类字段应该是受保护的。
4. 从子类中删除字段。
5. 您可能希望考虑为新字段使用 Self Encapsulate Field，以便将其隐藏在访问方法后面。