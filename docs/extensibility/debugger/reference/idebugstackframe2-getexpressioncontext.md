---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee4f7ec068b3daa77692d4ab64d327ebb8f61766
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457401"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
获取在当前上下文中的堆栈帧和线程的表达式计算评估上下文。

## <a name="syntax"></a>语法

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>参数
 `ppExprCxt`\

 [out]返回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)对象，表示为表达式计算上下文。

## <a name="return-value"></a>返回值
 如果成功，则返回`S_OK`; 否则为返回错误代码。

## <a name="remarks"></a>备注
 通常情况下，可以将表达式计算上下文视为执行表达式计算的作用域。 调用[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法来分析表达式，然后调用生成[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法已分析的表达式进行求值。

## <a name="see-also"></a>请参阅
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)