# Pull Up Method

## 问题
您的子类具有执行相似工作的方法。

## 解决方案
使这些方法相同，然后将它们移到相关的超类中。

### Pull Up Method - Before
```java
class Parent {
  // ...
  void commonMethod() {
    // Common implementation in the parent class
  }
}

class Child1 extends Parent {
  // ...
  void specificMethod() {
    // Specific implementation in Child1
  }
}

class Child2 extends Parent {
  // ...
  void specificMethod() {
    // Specific implementation in Child2
  }
```

### Pull Up Method - After
```java
class Parent {
  // ...
  void commonMethod() {
    // Common implementation in the parent class
  }

  // Common method pulled up from subclasses
  // This method is now available in the Parent class
  void specificMethod() {
    // Common implementation previously in Child1 and Child2
  }
}

class Child1 extends Parent {
  // ...
}

class Child2 extends Parent {
  // ...
}
```

## 为什么重构
子类独立增长和发展，导致相同（或几乎相同）的字段和方法。

## 优势
消除了重复的代码。如果需要更改方法，最好在一个地方进行更改，而不是在子类中搜索方法的所有副本。

如果由于某种原因子类重新定义了超类方法但执行的工作基本相同，也可以使用此重构技术。

## 如何重构
1. 调查超类中的相似方法。如果它们不是相同的，请将它们格式化为相互匹配。
2. 如果方法使用不同的参数集，请将参数放入您想在超类中看到的形式。
3. 将方法复制到超类。在这里，您可能会发现方法代码使用只存在于子类中的字段和方法，因此在超类中不可用。为解决此问题，您可以：
   - 对于字段：使用 Pull Up Field 或 Self-Encapsulate Field 在子类中创建 getter 和 setter；然后在超类中将这些 getter 声明为抽象的。
   - 对于方法：使用 Pull Up Method 或在超类中为它们声明抽象方法（请注意，如果以前的类不是抽象的，则您的类将变为抽象的）。
4. 从子类中删除这些方法。
5. 检查调用方法的位置。在某些地方，您可能能够用超类替换子类的使用。