---
title: '&lt;assemblyIdentity&gt;元素 （ClickOnce 部署） |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "58934797"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt;元素 （ClickOnce 部署）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

标识的主要程序集的[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `assemblyIdentity`元素是必需的。 它不包含任何子元素，并具有以下属性。  
  
|特性|描述|  
|---------------|-----------------|  
|`name`|必需。 标识部署的用户可读名称供您参考。<br /><br /> 如果`name`包含特殊字符，如单引号或双引号引起来，应用程序可能无法激活。|  
|`version`|必需。 采用以下格式指定该程序集的版本号： `major.minor.build.revision`。<br /><br /> 此值必须在应用更新的清单，以触发应用程序更新中会递增。|  
|`publicKeyToken`|必需。 指定的 16 字符十六进制字符串表示在其下部署清单进行签名的公钥的 sha-1 哈希值的最后 8 个字节。 用于签名的公钥必须为 2048 位或更高版本。<br /><br /> 尽管为程序集签名是可选但建议，但此属性是必需的。 如果程序集未签名，你应从自签名的程序集复制值或使用"虚拟"值均为零。|  
|`processorArchitecture`|必需。 指定的处理器。 有效的值是`msil`适用于所有处理器`x86`的 32 位 Windows`IA64`为 64 位 Windows 和`Itanium`Intel 64 位 Itanium 处理器。|  
|`type`|必需。 有关使用 Windows 的并行安装技术的兼容性。 唯一允许的值是`win32`。|  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的代码示例演示`assemblyIdentity`中的元素[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署清单。 此代码示例是为提供一个更大示例的一部分[ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题。  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity> 元素](../deployment/assemblyidentity-element-clickonce-application.md)
