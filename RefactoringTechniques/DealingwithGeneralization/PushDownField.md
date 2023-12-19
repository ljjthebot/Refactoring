# Push Down Field

## 问题
一个字段仅在少数几个子类中使用？

## 解决方案
将该字段移到这些子类中。

### Push Down Field - Before
```java
class Animal {
  protected String species;
}

class Cat extends Animal {
  // Cat-specific code
}

class Dog extends Animal {
  // Dog-specific code
}
```

### Push Down Field - After
```java
class Animal {
  // Empty superclass
}

class Cat extends Animal {
  protected String species;  // Moved down to Cat
}

class Dog extends Animal {
  // Dog-specific code
}
```

## 为什么重构
尽管最初计划在所有类中通用地使用字段，但实际上该字段仅在一些子类中使用。例如，当计划中的功能未能实现时，可能会出现这种情况。

这也可能是由于部分提取（或移除）类层次结构功能而导致的。

## 优势
提高了类内部的一致性。字段位于其实际使用的位置。

当同时移到多个子类时，可以独立地开发这些字段。是的，这确实会创建代码重复，因此只有在真正打算以不同的方式使用字段时才进行字段下推。

## 如何重构
1. 在所有必要的子类中声明字段。
2. 从超类中删除该字段。