### 简化条件表达式

条件表达式随着时间的推移往往变得越来越复杂，有许多技术可以应对这种情况。

#### [分解条件表达式（Decompose Conditional）](DecomposeConditional.md)
**问题：** 你有一个复杂的条件语句（if-then/else 或 switch）。

**解决方案：** 将条件语句中复杂的部分分解成单独的方法：条件部分、then 部分和 else 部分。

#### [合并条件表达式（Consolidate Conditional Expression）](ConsolidateConditionalExpression.md)
**问题：** 有多个条件表达式导致相同的结果或操作。

**解决方案：** 将所有这些条件表达式合并成一个单一的表达式。

#### [合并重复的条件片段（Consolidate Duplicate Conditional Fragments）](ConsolidateDuplicateConditionalFragments.md)
**问题：** 相同的代码存在于条件语句的所有分支中。

**解决方案：** 将代码移到条件语句外部。

#### [移除控制标志（Remove Control Flag）](RemoveControlFlag.md)
**问题：** 有一个布尔变量充当多个布尔表达式的控制标志。

**解决方案：** 不使用变量，而是使用 break、continue 和 return。

#### [用卫语句替换嵌套条件表达式（Replace Nested Conditional with Guard Clauses）](ReplaceNestedConditionalwithGuardClauses.md)
**问题：** 有一组嵌套的条件语句，很难确定代码执行的正常流程。

**解决方案：** 将所有特殊检查和边缘情况隔离到单独的卫语句中，并将它们放置在主要检查之前。理想情况下，应该有一个“平坦”的条件列表，一个接一个。

#### [用多态替换条件表达式（Replace Conditional with Polymorphism）](ReplaceConditionalwithPolymorphism.md)
**问题：** 有一个条件表达式根据对象类型或属性执行各种操作。

**解决方案：** 创建与条件表达式分支相匹配的子类。在这些子类中，创建一个共享方法，并将条件表达式分支中的代码移到该方法中。然后用相关方法调用替换条件表达式。通过多态性，根据对象类别实现适当的操作。

#### [引入空对象（Introduce Null Object）](IntroduceNullObject.md)
**问题：** 由于某些方法返回 null 而不是真实对象，你的代码中有许多检查 null 的情况。

**解决方案：** 不使用 null，而是返回一个表现默认行为的空对象。

#### [引入断言（Introduce Assertion）](IntroduceAssertion.md)
**问题：** 为了让代码的某部分正确工作，必须满足某些条件或值必须为真。

**解决方案：** 用具体的断言检查替换这些假设。