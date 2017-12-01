---
title: "测试区域 7： 共享 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f61a9917d484499e3cfd641f581859de01663bd0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-7-share"></a>测试区域 7： 共享
此测试区域涉及通过位置之间的共享项**共享**命令。  
  
 Hhare 操作是明显重复的文件和源控件文件层次结构中的两个或多个位置之间的文件夹项。 重复实际上未出现在服务器上，但用户未看到两个或多个指定位置中的相同文件。 无论对任何共享的项进行更改，这些更改将显示在所有其他共享位置。  
  
 如果在与至少一个文件受源代码管理中选择某个文件夹共享到文件夹中起作用。 在以下情况下已禁用共享命令：  
  
-   如果所选的文件夹是空的文件夹。  
  
-   如果没有实际的文件夹，但它未包含任何源控件文件。  
  
-   如果没有虚拟文件夹，或不在源代码管理下的文件是在它。  
  
-   如果没有远程站点 Web 项目。  
  
## <a name="command-menu-access"></a>命令菜单访问  
 以下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境菜单路径使用的测试用例。  
  
 共享：**文件**->**源代码管理**->**共享**。  
  
## <a name="expected-behavior"></a>预期的行为  
  
-   共享的文件将出现在共享位置。  
  
-   查看源控件版本存储历史记录显示共享文件。  
  
-   编辑共享的文件编辑文件的这两个位置。  
  
## <a name="test-cases"></a>测试用例  
 以下是针对共享测试区域的特定测试用例。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|共享到另一个加载项目受源代码管理的一个加载项目的文件|1.创建新项目。<br />2.将第二个项目添加到解决方案。<br />3.第二个项目中有不在第一个项目的名称创建一个文件。<br />4.将解决方案添加到源代码管理。<br />5.选择第一个项目。<br />6.打开**共享**对话框 (**文件** -> **源代码管理** -> **共享**)。<br />7.共享到第一个项目从第二个项目文件。<br />8.接受**签出**如果系统提示。|常见的预期的行为。|  
|共享到另一个项目的文件|1.创建新项目。<br />2.将其添加到源代码管理。<br />3.关闭解决方案。<br />4.创建第二个项目 （新的解决方案。）<br />5.将解决方案添加到源代码管理。<br />6.选择的项目。<br />7.打开**共享**对话框 (**文件** -> **源代码管理** -> **共享**)。<br />8.共享的文件从以前添加的项目，以便打开的项目。<br />9.接受**签出**如果系统提示。|常见的预期的行为。|  
|当前加载的项目到共享的文件不是从源代码管理项目的一部分|1.创建新项目。<br />2.将解决方案添加到源代码管理。<br />3.将文件添加到不是项目或解决方案的一部分的源控件。<br />4.选择该项目，打开**共享**对话框 (**文件** -> **源代码管理** -> **共享**)。<br />5.选择的文件内**共享**对话框中，不在当前项目或解决方案中存在并共享它。<br />6.接受**签出**如果系统提示。|源代码管理存储区具有执行 Get，因此该文件现在位于项目的本地位置。|  
|到其他文件夹的同一项目中的共享文件|1.选择**自动签出**中**工具** -> **选项** -> **源代码管理**。<br />2.创建新项目并将其添加到源代码管理。<br />3.将文件夹添加到项目。<br />4.将文件添加到的文件夹并签入文件夹。<br />5.选择的文件夹。<br />6.打开**共享**对话框 (**文件** -> **源代码管理** -> **共享**)。<br />7.到所选文件夹的共享文件。|常见的预期的行为。<br /><br /> 之前用于共享，文件夹必须检查使用中它的文件。|  
|加载的项目到共享的文件夹，递归|1.创建新项目。<br />2.将解决方案添加到源代码管理。<br />3.选择的项目。<br />4.打开**共享**对话框 (**文件** -> **源代码管理** -> **共享**)。<br />5.选择的文件夹。<br />6.项目到共享文件夹以递归方式。|常见的预期的行为。|  
|共享到另一个项目中的多个文件|1.使用在其中的多个文件创建新项目。<br />2.将解决方案添加到源代码管理。<br />3.关闭解决方案。<br />4.在新的解决方案中创建新项目。<br />5.将解决方案添加到源代码管理。<br />6.选择的项目。<br />7.打开**共享**对话框 (**文件** -> **源代码管理** -> **共享**)。<br />8.共享多个文件从以前创建的项目到当前打开的项目。|常见的预期的行为。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件的测试指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)