---
title: IDebugClassField::EnumNestedEnums |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdfa97ccdbf139ce28ec58c07864551c4e6a7d5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922629"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
创建此类的嵌套枚举器的枚举器。

## <a name="syntax"></a>语法

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>参数
`ppEnum`

 [out]返回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)对象，表示嵌套枚举的列表。 如果不有任何嵌套的枚举，则返回 null 值。

## <a name="return-value"></a>返回值
如果成功，则返回 S_OK 或如果没有嵌套的枚举器，则返回 S_FALSE。 否则，返回错误代码。

## <a name="remarks"></a>备注
枚举每个元素均[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)描述嵌套的枚举对象。

在类中声明的枚举被视为嵌套的枚举。 例如，给定：

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums`方法将返回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)对象，其中包含一个[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)对象，表示`NestedEnum`枚举。

## <a name="see-also"></a>请参阅
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
