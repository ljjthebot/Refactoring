# 代码重构-学习笔记
原文地址：[https://refactoring.guru/refactoring/techniques](https://refactoring.guru/refactoring/techniques)

# 清晰的代码

重构的主要目的是应对技术债务。它将混乱的代码转变为清晰的代码和简单的设计。

不错！但是清晰的代码到底是什么呢？以下是一些其特点：

1. **清晰的代码对其他程序员来说是明显的。**
   我不是在谈论超级复杂的算法。糟糕的变量命名，臃肿的类和方法，魔法数字——所有这些都使代码变得混乱且难以理解。

2. **清晰的代码不包含重复。**
   每当必须更改重复的代码时，您必须记住对每个实例进行相同的更改。这增加了认知负担并减缓进度。

3. **清晰的代码包含最少数量的类和其他移动部分。**
   较少的代码意味着较少的东西需要记住。较少的代码意味着较少的维护。较少的代码意味着较少的错误。代码是一种负担，保持其简短而简单。

4. **清晰的代码通过所有测试。**
   当你的代码只有 95% 的测试通过时，你知道你的代码很脏。当你的测试覆盖率为 0% 时，你知道情况很糟糕。

清晰的代码更容易且更便宜维护！

# 技术债务

每个人都尽力从头开始编写优秀的代码。可能没有程序员故意编写不干净的代码，以损害项目。但是清洁的代码在何时变得不洁？

关于不洁代码的“技术债务”隐喻最初是由Ward Cunningham提出的。

如果你从银行贷款，这使你能够更快地购物。你支付额外费用以加速流程 - 你不仅支付本金，还支付贷款的额外利息。不用说，你甚至可能累积了如此多的利息，以至于利息超过了你的总收入，使全额偿还成为不可能。

同样的事情也可能发生在代码中。你可以暂时加速新功能的编写，而不为其编写测试，但这将逐渐减慢你的进度，直到最终通过编写测试来偿还债务。

## 技术债务的原因

1. **商业压力**
   有时业务情况可能迫使您在完全完成之前推出功能。在这种情况下，代码中将出现补丁和临时解决方案，以隐藏项目未完成的部分。

2. **对技术债务后果的缺乏理解**
   有时您的雇主可能不理解技术债务的“利息”，因为它随着债务累积而减缓开发速度。这可能使得难以将团队的时间用于重构，因为管理层看不到其价值。

3. **未能对组件的严格一致性进行斗争**
   当项目看起来更像一个整体而不是单个模块的产品时，任何对项目的一部分的更改都将影响其他部分。团队开发变得更加困难，因为难以隔离各个成员的工作。

4. **缺乏测试**
   缺乏即时反馈会鼓励快速但有风险的解决方法或临时解决方案。在最糟糕的情况下，这些更改将在没有任何先前测试的情况下实施和部署到生产环境中。后果可能是灾难性的。例如，一个看似无害的热修复可能向数千名客户发送奇怪的测试电子邮件，甚至更糟，冲洗或损坏整个数据库。

5. **缺乏文档**
   这会减慢新成员加入项目的速度，并且如果关键人员离开项目，开发可能会停滞不前。

6. **团队成员之间的互动不足**
   如果知识库未在整个公司分布，人们最终会使用对流程和项目信息的过时理解。当初级开发人员受到其导师错误培训时，情况可能会恶化。

7. **长期同时在多个分支上开发**
   这可能导致技术债务的累积，当合并更改时会增加这些债务。在孤立环境中进行的更改越多，总技术债务就越大。

8. **延迟的重构**
   项目的需求不断变化，到某个时候可能会明显感觉到代码的某些部分已经过时，变得臃肿，并且必须进行重新设计以满足新的需求。

另一方面，项目的程序员每天都在编写与过时部分配合使用的新代码。因此，重构被推迟的时间越长，将来就越需要重新制定依赖性代码。

9. **缺乏合规性监控**
   当参与项目的每个人都按照他们认为合适的方式编写代码时（即，他们上次编写项目时的方式）。

10. **无能**
    这是指开发人员根本不知道如何编写体面的代码。
    
# 何时进行重构

## 三次原则
- **第一次：** 当你第一次做某事时，只需完成任务。
  
- **第二次：** 当你第二次做类似的事情时，对重复感到不满，但仍然以相同的方式做。

- **第三次：** 当你第三次做某事时，开始进行重构。

## 添加功能时
- 重构帮助你理解其他人的代码。如果你必须处理别人的混乱代码，尝试先进行重构。清晰的代码更容易理解。你将不仅为自己改进它，还为在你之后使用它的人改进它。

- 重构使添加新功能变得更容易。在清晰的代码中进行更改要容易得多。

## 修复错误时
- 代码中的错误就像现实生活中的错误一样：它们存在于代码中最黑暗、最肮脏的地方。清理你的代码，错误几乎会自己被发现。

- 管理员欣赏积极的重构，因为它消除了以后需要进行特殊重构任务的需要。满意的老板会让程序员更加愉快！

## 进行代码审查时
- 代码审查可能是在代码对外公开之前整理代码的最后机会。

- 最好是与作者一起执行这样的审查。这样你可以迅速解决简单的问题，并评估解决更难问题所需的时间。


# 如何进行重构

重构应该是一系列小的变化，每个变化都稍微改善了现有代码，同时仍然保持程序的可用状态。

## 正确进行重构的检查清单

1. **代码应该变得更清晰。**
   如果重构后代码仍然一样不清晰... 嗯，很抱歉，你刚刚浪费了一小时的生活。尝试弄清楚为什么会发生这种情况。

   这经常发生在你从小改变的重构中移开，并将一大堆重构混合到一个大的更改中。因此，很容易迷失在其中，尤其是如果你有时间限制的话。

   但在处理极其混乱的代码时，这也可能发生。无论你改进什么，代码整体仍然是一场灾难。

   在这种情况下，值得考虑彻底重写代码的某些部分。但在此之前，你应该编写测试并留出足够的时间。否则，你将会得到我们在第一段中谈到的结果。

2. **在重构期间不应创建新功能。**
   不要混合重构和直接开发新功能。尽量将这两个过程分开，至少在单个提交的范围内分开。

3. **所有现有测试在重构后都必须通过。**
   在重构后，测试可能会出现两种情况：

   - 你在重构过程中犯了一个错误。这是很明显的：立即修复错误。

   - 你的测试层次太低。例如，你正在测试类的私有方法。

   在这种情况下，测试有问题。你可以重构测试本身，或者编写一个全新的更高层次的测试集。避免这种情况的一个好方法是编写BDD风格的测试。
    

# 重构目录

## [代码异味](codesmells/README.md)
- 什么？代码怎么可能有“异味”？
- 嗯，它没有鼻子... 但它确实可能臭！

### [臃肿者](codesmells/bloaters/README.md)
臃肿者是指那些已经变得庞大到难以处理的代码、方法和类。通常这些异味不会立即出现，而是随着程序的演变而积累（尤其是当没有人努力清除它们时）。

- [长方法（Long Method）](codesmells/bloaters/LongMethod.md)
- [大类（Large Class）](codesmells/bloaters/LargeClass.md)
- [原始偏执（Primitive Obsession）](codesmells/bloaters/primitiveObsession.md)
- [长参数列表（Long Parameter List）](codesmells/bloaters/LongParaList.md)
- [数据团（Data Clumps）](codesmells/bloaters/DataClumps.md)

### [面向对象滥用](codesmells/Object-OrientationAbusers/README.md)
这些异味是指对面向对象编程原则的不完整或不正确应用。

- [具有不同接口的替代类（Alternative Classes with Different Interfaces）](codesmells/Object-OrientationAbusers/Alternative.md)
- [拒绝继承（Refused Bequest）](codesmells/Object-OrientationAbusers/Refused.md)
- [开关语句（Switch Statements）](codesmells/Object-OrientationAbusers/SwitchStatements.md)
- [临时字段（Temporary Field）](codesmells/Object-OrientationAbusers/Temporary.md)

### [阻止变更](codesmells/Change/README.md)
这些异味意味着如果你需要在代码的一个地方进行更改，你必须在其他地方进行许多更改。由此导致程序开发变得更加复杂和昂贵。

- [发散变更（Divergent Change）](codesmells/Change/Divergent.md)
- [平行继承体系（Parallel Inheritance Hierarchies）](codesmells/Change/Parallel.md)
- [散弹手术（Shotgun Surgery）](codesmells/Change/Shotgun.md)

### [可丢弃的](codesmells/Dispensables/README.md)
可丢弃的是指一些毫无意义和不必要的东西，如果删除，将使代码更清晰、更高效，并更易于理解。

- [注释（Comments）](codesmells/Dispensables/Comments.md)
- [重复代码（Duplicate Code）](codesmells/Dispensables/Duplicate.md)
- [数据类（Data Class）](codesmells/Dispensables/Data.md)
- [死代码（Dead Code）](codesmells/DispensablesDead.md/)
- [懒惰类（Lazy Class）](codesmells/Dispensables/Lazy.md)
- [猜测性泛化（Speculative Generality）](codesmells/Dispensables/Speculative.md)

### [耦合者](codesmells/Couplers/README.md)
这一组中的所有异味都导致类之间的耦合过度，或显示了如果通过过度委托来替代耦合会发生什么。

- [特性嫉妒（Feature Envy）](codesmells/Couplers/Feature.md)
- [不适当的亲密关系（Inappropriate Intimacy）](codesmells/Couplers/Inappropriate.md)
- [不完整的库类（Incomplete Library Class）](codesmells/Couplers/)
- [消息链（Message Chains）](codesmells/Couplers/Message.md)
- [中间人（Middle Man）](codesmells/Couplers/Middle.md)

## [重构技术](RefactoringTechniques/README.md)

### [方法组合](RefactoringTechniques/ComposingMethods/README.md)
大部分的重构都致力于正确组合方法。在大多数情况下，过长的方法是所有问题的根源。这些方法内部的代码曲折地隐藏了执行逻辑，使方法难以理解——甚至更难更改。

- [提取方法（Extract Method）](RefactoringTechniques/ComposingMethods/Extract.md)
- [内联方法（Inline Method）](RefactoringTechniques/ComposingMethods/Inline.md)
- [提取变量（Extract Variable）](RefactoringTechniques/ComposingMethods/Variable.md)
- [内联临时变量（Inline Temp）](RefactoringTechniques/ComposingMethods/InlineTemp.md)
- [用查询替代临时变量（Replace Temp with Query）](RefactoringTechniques/ComposingMethods/ReplaceTempwithQuery.md)
- [拆分临时变量（Split Temporary Variable）](RefactoringTechniques/ComposingMethods/SplitTemporaryVariable.md)
- [移除对参数的赋值（Remove Assignments to Parameters）](RefactoringTechniques/ComposingMethods/RemoveAssignmentstoParameters.md)
- [用方法对象替代方法（Replace Method with Method Object）](RefactoringTechniques/ComposingMethods/ReplaceMethodwithMethodObject.md)
- [替代算法（Substitute Algorithm）](RefactoringTechniques/ComposingMethods/SubstituteAlgorithm.md)

### [在对象之间移动特性](RefactoringTechniques/MovingFeaturesbetweenObjects/README.md)
即使你以不太理想的方式在不同类之间分发功能，仍有希望。

这些重构技术展示了如何在类之间安全地移动功能，创建新类，并将实现细节隐藏在公共访问之外。

- [移动方法（Move Method）](RefactoringTechniques/MovingFeaturesbetweenObjects/MoveMethod.md)
- [移动字段（Move Field）](RefactoringTechniques/MovingFeaturesbetweenObjects/MoveField.md)
- [提取类（Extract Class）](RefactoringTechniques/MovingFeaturesbetweenObjects/ExtractClass.md)
- [内联类（Inline Class）](RefactoringTechniques/MovingFeaturesbetweenObjects/InlineClass.md)
- [隐藏代理（Hide Delegate）](RefactoringTechniques/MovingFeaturesbetweenObjects/HideDelegate.md)
- [移除中间人（Remove Middle Man）](RefactoringTechniques/MovingFeaturesbetweenObjects/RemoveMiddleMan.md)
- [引入外来方法（Introduce Foreign Method）](RefactoringTechniques/MovingFeaturesbetweenObjects/IntroduceForeignMethod.md)
- [引入本地扩展（Introduce Local Extension）](RefactoringTechniques/MovingFeaturesbetweenObjects/IntroduceLocalExtension.md)

### [数据组织](RefactoringTechniques/OrganizingData/README.md)
这些重构技术有助于处理数据，将基本类型替换为丰富的类功能。另一个重要的结果是解开类之间的关联，使类更易于移植和重用。

- [将值对象变为引用对象（Change Value to Reference）](RefactoringTechniques/OrganizingData/ChangeValuetoReference.md)
- [将引用对象变为值对象（Change Reference to Value）](RefactoringTechniques/OrganizingData/ChangeReferencetoValue.md)
- [重复观察数据（Duplicate Observed Data）](RefactoringTechniques/OrganizingData/DuplicateObservedData.md)
- [自封装字段（Self Encapsulate Field）](RefactoringTechniques/OrganizingData/SelfEncapsulateField.md)
- [用对象替代数据值（Replace Data Value with Object）](RefactoringTechniques/OrganizingData/ReplaceDataValuewithObject.md)
- [用对象替代数组（Replace Array with Object）](RefactoringTechniques/OrganizingData/ReplaceArraywithObject.md)
- [将单向关联改为双向关联（Change Unidirectional Association to Bidirectional）](RefactoringTechniques/OrganizingData/ChangeUnidirectionalAssociationtoBidirectional.md)
- [将双向关联改为单向关联（Change Bidirectional Association to Unidirectional）](RefactoringTechniques/OrganizingData/ChangeBidirectionalAssociationtoUnidirectional.md)
- [封装字段（Encapsulate Field）](RefactoringTechniques/OrganizingData/EncapsulateField.md)
- [封装集合（Encapsulate Collection）](RefactoringTechniques/OrganizingData/EncapsulateCollection.md)
- [用符号常量替代魔法数字（Replace Magic Number with Symbolic Constant）](RefactoringTechniques/OrganizingData/ReplaceMagicNumberwithSymbolicConstant.md)
- [用类替代类型码（Replace Type Code with Class）](RefactoringTechniques/OrganizingData/ReplaceTypeCodewithClass.md)
- [用子类替代类型码（Replace Type Code with Subclasses）](RefactoringTechniques/OrganizingData/ReplaceTypeCodewithSubclasses.md)
- [用状态/策略替代类型码（Replace Type Code with State/Strategy）](RefactoringTechniques/OrganizingData/ReplaceTypeCodewithStateStrategy.md)
- [用字段替代子类（Replace Subclass with Fields）](RefactoringTechniques/OrganizingData/ReplaceSubclasswithFields.md)

### [简化条件表达式](RefactoringTechniques/SimplifyingConditionalExpressions/README.md)
随着时间推移，条件表达式往往变得越来越复杂，有更多的技术来对抗这种情况。

- [合并条件表达式（Consolidate Conditional Expression）](RefactoringTechniques/SimplifyingConditionalExpressions/ConsolidateConditionalExpression.md)
- [合并重复的条件片段（Consolidate Duplicate Conditional Fragments）](RefactoringTechniques/SimplifyingConditionalExpressions/ConsolidateDuplicateConditionalFragments.md)
- [分解条件表达式（Decompose Conditional）](RefactoringTechniques/SimplifyingConditionalExpressions/DecomposeConditional.md)
- [用多态替代条件表达式（Replace Conditional with Polymorphism）](RefactoringTechniques/SimplifyingConditionalExpressions/ReplaceConditionalwithPolymorphism.md)
- [移除控制标志（Remove Control Flag）](RefactoringTechniques/SimplifyingConditionalExpressions/RemoveControlFlag.md)
- [用守卫句替代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）](RefactoringTechniques/SimplifyingConditionalExpressions/ReplaceNestedConditionalwithGuardClauses.md)
- [引入空对象（Introduce Null Object）](RefactoringTechniques/SimplifyingConditionalExpressions/IntroduceNullObject.md)
- [引入断言（Introduce Assertion）](RefactoringTechniques/SimplifyingConditionalExpressions/IntroduceAssertion.md)

### [简化方法调用](RefactoringTechniques/SimplifyingMethodCalls/README.md)
这些技术使方法调用更简单、更易理解。从而简化了类之间的交互接口。

- **[添加参数（Add Parameter）](RefactoringTechniques/SimplifyingMethodCalls/AddParameter.md)**
- **[移除参数（Remove Parameter）](RefactoringTechniques/SimplifyingMethodCalls/RemoveParameter.md)**
- **[重命名方法（Rename Method）](RefactoringTechniques/SimplifyingMethodCalls/RenameMethod.md)**
- **[将查询和修改分离（Separate Query from Modifier）](RefactoringTechniques/SimplifyingMethodCalls/SeparateQueryfromModifier.md)**
- **[参数化方法（Parameterize Method）](RefactoringTechniques/SimplifyingMethodCalls/ParameterizeMethod.md)**
- **[引入参数对象（Introduce Parameter Object）](RefactoringTechniques/SimplifyingMethodCalls/IntroduceParameterObject.md)**
- **[保留整个对象（Preserve Whole Object）](RefactoringTechniques/SimplifyingMethodCalls/PreserveWholeObject.md)**
- **[移除设置方法（Remove Setting Method）](RefactoringTechniques/SimplifyingMethodCalls/RemoveSettingMethod.md)**
- **[用显式方法替换参数（Replace Parameter with Explicit Methods）](RefactoringTechniques/SimplifyingMethodCalls/ReplaceParameterwithExplicitMethods.md)**
- **[用方法调用替换参数（Replace Parameter with Method Call）](RefactoringTechniques/SimplifyingMethodCalls/ReplaceParameterwithMethodCall.md)**
- **[隐藏方法（Hide Method）](RefactoringTechniques/SimplifyingMethodCalls/HideMethod.md)**
- **[用工厂方法替换构造函数（Replace Constructor with Factory Method）](RefactoringTechniques/SimplifyingMethodCalls/ReplaceConstructorwithFactoryMethod.md)**
- **[用异常替换错误码（Replace Error Code with Exception）](RefactoringTechniques/SimplifyingMethodCalls/ReplaceErrorCodewithException.md)**
- **[用测试替换异常（Replace Exception with Test）](RefactoringTechniques/SimplifyingMethodCalls/ReplaceExceptionwithTest.md)**

### [处理泛化](RefactoringTechniques/DealingwithGeneralization/README.md)
抽象有其自己的一组重构技术，主要涉及沿着类继承层次结构移动功能，创建新的类和接口，以及替换继承与委托之间的关系。

- **[上移字段（Pull Up Field）](RefactoringTechniques/DealingwithGeneralization/PullUpField.md)**
- **[上移方法（Pull Up Method）](RefactoringTechniques/DealingwithGeneralization/PullUpMethod.md)**
- **[上移构造函数主体（Pull Up Constructor Body）](RefactoringTechniques/DealingwithGeneralization/PullUpConstructorBody.md)**
- **[下移字段（Push Down Field）](RefactoringTechniques/DealingwithGeneralization/PushDownField.md)**
- **[下移方法（Push Down Method）](RefactoringTechniques/DealingwithGeneralization/PushDownMethod.md)**
- **[提取子类（Extract Subclass）](RefactoringTechniques/DealingwithGeneralization/ExtractSubclass.md)**
- **[提取超类（Extract Superclass）](RefactoringTechniques/DealingwithGeneralization/ExtractSuperclass.md)**
- **[提取接口（Extract Interface）](RefactoringTechniques/DealingwithGeneralization/ExtractInterface.md)**
- **[折叠层次结构（Collapse Hierarchy）](RefactoringTechniques/DealingwithGeneralization/CollapseHierarchy.md)**