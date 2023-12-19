# Pull Up Constructor Body

## 问题
您的子类具有构造函数，其中的代码大部分相同。

## 解决方案
创建一个超类构造函数，并将子类中相同的代码移到其中。在子类构造函数中调用超类构造函数。

### Java
```java
class Manager extends Employee {
  public Manager(String name, String id, int grade) {
    this.name = name;
    this.id = id;
    this.grade = grade;
  }
  // ...
}

class Manager extends Employee {
  public Manager(String name, String id, int grade) {
    super(name, id);
    this.grade = grade;
  }
  // ...
}
```

## 为什么重构
这个重构技术与 Pull Up Method 有什么不同？

在Java中，子类无法继承构造函数，因此您不能简单地将 Pull Up Method 应用于子类构造函数，然后在将所有构造函数代码移至超类后将其删除。除了在超类中创建构造函数之外，还需要在子类中具有构造函数，简单地委托给超类构造函数。

在C++和Java中（如果您没有显式调用超类构造函数），在子类构造函数之前会自动调用超类构造函数，这使得只能从子类构造函数的开头移动公共代码（因为您无法从子类构造函数的任意位置调用超类构造函数）。

在大多数编程语言中，子类构造函数可以具有与超类参数不同的参数列表。因此，应该仅使用超类构造函数真正需要的参数创建超类构造函数。

## 如何重构
1. 在超类中创建一个构造函数。
2. 从每个子类的构造函数的开头提取公共代码到超类构造函数中。在这样做之前，尽量将尽可能多的公共代码移动到构造函数的开头。
3. 在子类构造函数的第一行放置对超类构造函数的调用。