---
title: 'Idiadatasource:: Get_lasterror |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ad0570436dda6ac9ae52325c891b32a563cf6f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547359"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
检索最后一个加载错误的文件名称。

## <a name="syntax"></a>语法

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>参数
 pRetVal

[out]返回一个字符串，包含与最后一个加载错误关联的.pdb 文件名称。

## <a name="return-value"></a>返回值
 返回引起的加载操作的最后一个错误代码。 返回`E_INVALIDARG`如果`pRetVal`参数是`NULL`。

## <a name="example"></a>示例

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>请参阅
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)