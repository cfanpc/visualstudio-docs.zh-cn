---
title: IDebugCoreServer3::CreateInstanceInServer |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8536fe85e58d3c43784d52b85d50015225068141
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47483169"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[IDebugCoreServer3::CreateInstanceInServer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver)。  
  
在服务器上创建调试引擎的实例。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>参数  
 `szDll`  
 [in]实现中指定的 CLSID 的 dll 路径`clsidObject`参数。 如果这是`NULL`，然后 COM 的`CoCreateInstance`调用函数。  
  
 `wLangId`  
 [in]调试引擎的区域设置。 这可以是 0，如果[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)不应调用方法。  
  
 `clsidObject`  
 [in]若要创建的调试引擎的 CLSID。  
  
 `riid`  
 [in]接口 ID 的特定接口来检索此类对象中。  
  
 `ppvObject`  
 [out]`IUnknown`中实例化的对象的接口。 强制转换或封送到所需的接口的此对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>请参阅  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
