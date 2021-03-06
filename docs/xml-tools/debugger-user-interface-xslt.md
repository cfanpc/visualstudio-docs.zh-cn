---
title: XSLT 调试器窗口
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25c47e6db79fe4b860b6e7c209f0fc8403d0fcd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838488"
---
# <a name="debugger-user-interface-xslt"></a>调试程序用户界面 (XSLT)

本文介绍的调试器窗口和对话框。 只讨论具有 XSLT 特定的调试行为的用户界面部分。

有关详细信息，请参阅[调试用户界面参考](../debugger/debugging-user-interface-reference.md)。

## <a name="locals-window"></a>局部变量窗口

“局部变量”窗口显示在样式表中定义的任何变量的有关信息。 “局部变量”窗口包含三列信息：

**名称**

此列包含当前范围中的所有局部变量的名称。 节点集具有一个树控件，您可以向下钻取以查看子文件夹。

**值**

该列显示每个变量所包含的值。 属性、处理指令、注释、文本和 CData 节点显示节点的文本值。 命名空间节点显示命名空间 URI。

**Type**

此列标识每个变量中列出的数据类型**名称**列。

“局部变量”窗口还显示用于跟踪 XSLT 转换上下文的预定义上下文变量。 下表介绍 XSLT 调试程序所使用的预定义上下文变量。

|名称|描述|
|-|-----------------|
|`last()`|上下文大小。|
|`position()`|上下文节点相对于上下文大小的位置（或索引号）。|
|`self::node()`|上下文节点的值。|

## <a name="output-window"></a>“输出”窗口

“输出”窗口显示在调试期间出现的任何错误消息或发生的任何安全异常。 它还显示调试程序输出。

## <a name="task-list"></a>任务列表

**任务列表**列出了在样式表中的所有编译错误。 双击错误可以将光标置于包含错误的行。

**任务列表**XSLT 文件中的脚本块包括出现的任何错误。

> [!NOTE]
> XSLT 调试程序没有任何警告，因此它们永远不会出现在**任务列表**。

## <a name="breakpoints-window"></a>“断点”窗口

“断点”窗口显示当前项目中设置的所有断点。 如果在该窗口位于视图中时添加断点，该窗口将自动更新，以显示新的断点。

“断点”窗口的操作方式应与其他 Visual Studio 调试程序相同。

## <a name="watch-window"></a>监视窗口

“监视”窗口用于计算变量。 还可以更改变量的值。

“监视”窗口中显示的变量针对当前上下文（调用堆栈上最顶部的项）。 如果更改上下文，“监视”窗口将更新，显示为该上下文设置的变量。

## <a name="call-stack-window"></a>“调用堆栈”窗口

**调用堆栈**窗口用于查看调用堆栈、 参数类型和参数值的函数的名称。 仅当正在调试的程序处于中断状态时，才显示调用堆栈信息。

调用堆栈表示 XSLT 执行所经过的各种上下文。 例如，如果没有从模板调用"a"到模板"b"、 模板"a"和模板"b"中将出现**调用堆栈**与当前上下文处于列表顶部的窗口。 用户可以查看当前正在执行的查询。

如果模板在 XSLT 文件中没有名称，将使用 XSLT 处理器生成的名称。

如果单击的不是列表顶部的项，则使用标准的绿色突出显示和绿色箭头向查看者指示 XSLT 执行分支出现的位置。

## <a name="quickwatch-dialog-box"></a>“快速监视”对话框

**快速监视**对话框用于计算 XPath 1.0 表达式。 上下文节点（“局部变量”窗口中的 `self::node()` 节点）为 XPath 表达式的执行提供上下文。 执行 XPath 表达式的结果显示在“监视”窗口中。

以下列表描述对 XPath 表达式计算的限制：

- 只允许使用内置 XPath 函数。

- 之类的内置 XSLT 函数`document()`和`key()`不允许。

- 不允许使用用户定义函数。

有关详细信息，请参阅[如何：计算 XPath 表达式](../xml-tools/how-to-evaluate-an-xpath-expression.md)。

## <a name="disassembly-window"></a>“反汇编”窗口

“反汇编”窗口显示 XSLT 编译器生成的程序集代码。 此窗口的用法与所有其他 Visual Studio 反汇编窗口相同。

有关详细信息，[如何：使用反汇编窗口](../debugger/how-to-use-the-disassembly-window.md)。

## <a name="see-also"></a>请参阅

- [调试 XSLT](../xml-tools/debugging-xslt.md)
- [初探调试器](../debugger/debugger-feature-tour.md)
- [检查 Visual Studio 中的自动和局部变量窗口中的变量](../debugger/autos-and-locals-windows.md)