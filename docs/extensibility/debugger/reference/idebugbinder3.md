---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a08ee3f637b954d2df7e48fb8f6aebbdd0948c19
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414075"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> 在 Visual Studio 2015 中，这种方式实现表达式计算器已弃用。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)并[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此接口提供对类型、 别名和自定义可视化工具服务的访问。

## <a name="syntax"></a>语法

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>实施者的说明
 调试引擎实现此接口以支持别名、 自定义可视化工具服务和对象类型信息的访问。

## <a name="notes-for-callers"></a>调用方的说明
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)接口获取此接口通过[QueryInterface](/cpp/atl/queryinterface)。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 除了提供的方法[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)接口，此接口实现了以下：

|方法|描述|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|检索表示此对象绑定到的内存的内存对象。|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|检索此对象 （如果有），与关联的异常|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|检索在给定其名称的别名|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|检索此对象的所有别名的数组|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|获取与此对象关联的自变量类型的数目|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|检索与此对象关联的自变量类型的列表|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|获取可视化工具服务的接口|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|将转换为内存上下文的对象位置或 64 位内存地址。|

## <a name="requirements"></a>要求
 标头： ee.h

 命名空间:Microsoft.VisualStudio.Debugger.Interop

 程序集：Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)