﻿---
title: 分配挂钩函数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 406647ae086285df8dfdfc00daf4b62be66e74a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402703"
---
# <a name="allocation-hook-functions"></a>分配挂钩函数
分配挂钩函数，使用安装[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)，每次分配、 重新分配或释放内存时调用。 这种类型的挂钩可用于多种用途。 使用它来测试应用程序如何处理内存不足的情况下，例如检查分配模式，或记录分配信息以供日后分析。

> [!NOTE]
> 注意有关在分配挂钩函数中使用 C 运行库函数的限制，详见[分配挂钩和 C 运行时内存分配](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)中的说明。

 分配挂钩函数应具有的原型如下例所示：

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 传递给 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) 的指针为 _CRT_ALLOC_HOOK 类型，如 CRTDBG.H 中所定义：

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 当运行时库调用您的挂钩时，*nAllocType*参数表明即将执行哪项分配操作(**_HOOK_ALLOC**、**_HOOK_REALLOC** 或 **_HOOK_FREE**)。 在释放或重新分配时，`pvData`有一个指针指向即将释放的内存块的用户文章。 但是在分配时，此指针为 null，因为分配尚未发生。 其余的参数包含相关分配的大小、内存块类型、 与之关联的顺序请求号和指向文件名的指针。 如果可用，参数还包括在其中进行分配的行号。 挂钩函数在执行完所有分析及需要做的其他任务后，它必须返回 **TRUE**，表明分配操作可以继续，或返回**FALSE**，表明分配操作会失败。 一个此类型的简单挂钩函数可能会检查到目前为止分配的内存量，如果该内存量超出最小限制，则返回**FALSE**。 然后应用程序将遇到内存分配错误，这种错误通常只会在可用内存极为不足时发生。 较复杂的挂钩函数可以跟踪分配模式，分析内存使用，或在特定情况发生时进行报告。

## <a name="see-also"></a>请参阅

- [分配挂钩和 C 运行时内存分配](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [编写调试挂钩函数](../debugger/debug-hook-function-writing.md)