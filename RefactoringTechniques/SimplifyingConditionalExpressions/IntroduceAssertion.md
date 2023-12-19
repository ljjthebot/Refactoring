# 引入断言

## 问题
为了使代码的某一部分正确工作，必须满足特定条件或值。

## 解决方案
使用具体的断言检查替换这些假设。

```java
// Java示例
double getExpenseLimit() {
  // Should have either expense limit or
  // a primary project.
  return (expenseLimit != NULL_EXPENSE) ?
    expenseLimit :
    primaryProject.getMemberExpenseLimit();
}
```

```
double getExpenseLimit() {
  Assert.isTrue(expenseLimit != NULL_EXPENSE || primaryProject != null);

  return (expenseLimit != NULL_EXPENSE) ?
    expenseLimit:
    primaryProject.getMemberExpenseLimit();
}
```

## 为什么要重构
假设代码的一部分对对象的当前条件或参数或局部变量的值做出了一些假设。通常情况下，这些假设总是成立，除非发生错误。

通过添加相应的断言，使这些假设显而易见。与方法参数的类型提示一样，这些断言可以作为代码的实时文档。

作为一个指导方针，查看代码需要断言的地方，检查描述特定方法将在其中工作的条件的注释。

## 好处
如果假设不成立，代码因此产生错误结果，最好在这导致严重后果和数据损坏之前停止执行。这也意味着在制定程序测试方法时，您忽略了编写必要的测试。

## 缺点
有时候，异常比简单的断言更合适。您可以选择异常的必要类，并让其余代码正确处理它。

什么情况下异常比简单的断言更好？如果异常可能由用户或系统的操作引起，并且您可以处理该异常。另一方面，普通的未命名和未处理的异常基本上等同于简单的断言，您不处理它们，它们仅作为程序错误的结果而发生，而这是绝不应该发生的。

## 如何重构
当您发现某个条件是假设时，请添加相应的断言以确保它。

添加断言不应更改程序的行为。

不要在代码中对所有事情都使用断言。只检查对代码的正确运行必不可少的条件。如果您的代码在特定断言为false时仍然正常工作，那么可以安全地删除该断言。
```