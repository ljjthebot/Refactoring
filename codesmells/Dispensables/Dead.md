#死代码
##征兆和症状

变量、参数、字段、方法或类不再被使用（通常是因为它已过时）。

##问题的原因

当软件的需求发生变化或进行了修正时，没有人有时间清理旧代码。

这样的代码也可能存在于复杂的条件语句中，当其中一个分支变得无法到达时（由于错误或其他情况）。

##处理方法

找到死代码的最快方法是使用好的集成开发环境（IDE）。

删除未使用的代码和不必要的文件。

对于不必要的类，如果使用了子类或超类，可以应用“内联类”（Inline Class）或“折叠层次结构”（Collapse Hierarchy）。

要删除不必要的参数，请使用“删除参数”（Remove Parameter）。

##收益

减小代码体积。

更简单的维护。