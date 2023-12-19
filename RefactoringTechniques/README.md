# 重构技术

## 组合方法（Composing Methods）

大部分的重构致力于正确地组合方法。在大多数情况下，过于冗长的方法是所有问题的根源。这些方法内部的代码复杂性掩盖了执行逻辑，使方法极难理解——甚至更难修改。

这个组中的重构技术简化方法，消除代码重复，并为将来的改进铺平道路。

- [提取方法（Extract Method）](#extract-method)
- [内联方法（Inline Method）](#inline-method)
- [提取变量（Extract Variable）](#extract-variable)
- [内联临时变量（Inline Temp）](#inline-temp)
- [用查询替换临时变量（Replace Temp with Query）](#replace-temp-with-query)
- [分割临时变量（Split Temporary Variable）](#split-temporary-variable)
- [移除对参数的赋值（Remove Assignments to Parameters）](#remove-assignments-to-parameters)
- [用方法对象替换方法（Replace Method with Method Object）](#replace-method-with-method-object)
- [替代算法（Substitute Algorithm）](#substitute-algorithm)

## 在对象之间移动特性（Moving Features between Objects）

即使您以不太理想的方式在不同类之间分配功能，仍有希望。

这些重构技术展示了如何安全地在类之间移动功能、创建新类，并隐藏对公共访问的实现细节。

- [移动方法（Move Method）](#move-method)
- [移动字段（Move Field）](#move-field)
- [提取类（Extract Class）](#extract-class)
- [内联类（Inline Class）](#inline-class)
- [隐藏代理（Hide Delegate）](#hide-delegate)
- [移除中间人（Remove Middle Man）](#remove-middle-man)
- [引入外加方法（Introduce Foreign Method）](#introduce-foreign-method)
- [引入本地扩展（Introduce Local Extension）](#introduce-local-extension)

## 组织数据（Organizing Data）

这些重构技术有助于处理数据，用富类功能替换原始数据类型。另一个重要的结果是解开类之间的关联，使类更具可移植性和可重用性。

- [将值对象转换为引用对象（Change Value to Reference）](#change-value-to-reference)
- [将引用对象转换为值对象（Change Reference to Value）](#change-reference-to-value)
- [复制被观察的数据（Duplicate Observed Data）](#duplicate-observed-data)
- [自封装字段（Self Encapsulate Field）](#self-encapsulate-field)
- [用对象替换数据值（Replace Data Value with Object）](#replace-data-value-with-object)
- [用对象替换数组（Replace Array with Object）](#replace-array-with-object)
- [将单向关联改为双向关联（Change Unidirectional Association to Bidirectional）](#change-unidirectional-association-to-bidirectional)
- [将双向关联改为单向关联（Change Bidirectional Association to Unidirectional）](#change-bidirectional-association-to-unidirectional)
- [封装字段（Encapsulate Field）](#encapsulate-field)
- [封装集合（Encapsulate Collection）](#encapsulate-collection)
- [用符号常量替换魔法数（Replace Magic Number with Symbolic Constant）](#replace-magic-number-with-symbolic-constant)
- [用类替换类型码（Replace Type Code with Class）](#replace-type-code-with-class)
- [用子类替换类型码（Replace Type Code with Subclasses）](#replace-type-code-with-subclasses)
- [用状态/策略替换类型码（Replace Type Code with State/Strategy）](#replace-type-code-with-statestrategy)
- [用字段替换子类（Replace Subclass with Fields）](#replace-subclass-with-fields)

## 简化条件表达式（Simplifying Conditional Expressions）

随着时间的推移，条件语句的逻辑往往变得越来越复杂，有更多的技术可以应对这种情况。

- [合并条件表达式（Consolidate Conditional Expression）](#consolidate-conditional-expression)
- [合并重复的条件片段（Consolidate Duplicate Conditional Fragments）](#consolidate-duplicate-conditional-fragments)
- [分解条件表达式（Decompose Conditional）](#decompose-conditional)
- [用多态替换条件表达式（Replace Conditional with Polymorphism）](#replace-conditional-with-polymorphism)
- [移除控制标志（Remove Control Flag）](#remove-control-flag)
- [用守卫子句替换嵌套条件表达式（Replace Nested Conditional with Guard Clauses）](#replace-nested-conditional-with-guard-clauses)
- [引入空对象（Introduce Null Object）](#introduce-null-object)
- [引入断言（Introduce Assertion）](#introduce-assertion)

## 简化方法调用（Simplifying Method Calls）

这些技术使方法调用变得更简单，更容易理解。这反过来简化了类之间的交互接口。

- [添加参数（Add Parameter）](#add-parameter)
- [移除参数（Remove Parameter）](#remove-parameter)
- [重命名方法（Rename Method）](#rename-method)
- [将查询函数与修改函数分离（Separate Query from Modifier）](#separate-query-from-modifier)
- [参数化方法（Parameterize Method）](#parameterize-method)
- [引入参数对象（Introduce Parameter Object）](#introduce-parameter-object)
- [保留整个对象（Preserve Whole Object）](#preserve-whole-object)
- [移除设值方法（Remove Setting Method）](#remove-setting-method)
- [用方法调用替换参数（Replace Parameter with Method Call）](#replace-parameter-with-method-call)
- [隐藏方法（Hide Method）](#hide-method)
- [用工厂方法替换构造函数（Replace Constructor with Factory Method）](#replace-constructor-with-factory-method)
- [用异常替换错误码（Replace Error Code with Exception）](#replace-error-code-with-exception)
- [用测试替换异常（Replace Exception with Test）](#replace-exception-with-test)

## 处理泛化（Dealing with Generalization）

抽象有自己的一组重构技术，主要涉及沿着类继承层次结构移动功能、创建新类和接口，以及替换继承与委托等。

- [向上移动字段（Pull Up Field）](#pull-up-field)
- [向上移动方法（Pull Up Method）](#pull-up-method)
- [向上移动构造函数体（Pull Up Constructor Body）](#pull-up-constructor-body)
- [向下移动字段（Push Down Field）](#push-down-field)
- [向下移动方法（Push Down Method）](#push-down-method)
