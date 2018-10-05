---
title: CustomParameter 元素 （Visual Studio 模板） |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d968f255607bd0d98dc83945bfcb555400a1573a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47479473"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[CustomParameter 元素 （Visual Studio 模板）](https://docs.microsoft.com/visualstudio/extensibility/customparameter-element-visual-studio-templates)。  
  
包含自定义参数名称和从模板创建项目或项时要使用的值。  
  
## <a name="syntax"></a>语法  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`Name`|必须的。 参数的名称。 参数的格式是 $*名称*$。|  
|`Value`|必须的。 参数的替换值。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|组是在该向导可以将参数替换项时要传递到模板向导的自定义参数。|  
  
## <a name="remarks"></a>备注  
 如果模板包含`CustomParameter`元素，每个实例`Name`属性将替换`Value`中创建的项目或项目文件的属性。  
  
## <a name="example"></a>示例  
 下面的示例演示如何在模板中使用多个自定义参数。 当从具有以下自定义参数的所有实例的模板创建项目或项`$color1$`并`$color2$`在模板中的文件将替换`Red`和`Blue`分别。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>请参阅  
 [CustomParameters 元素 （Visual Studio 模板）](../extensibility/customparameters-element-visual-studio-templates.md)   
 [模板参数](../ide/template-parameters.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)
