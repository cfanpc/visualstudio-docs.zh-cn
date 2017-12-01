---
title: "测试区域 1： 从源代码管理添加到打开 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 959387176e079d76263a2a5c499b5a0723fd7ad7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-1-add-toopen-from-source-control"></a>测试区域 1： 从源代码管理添加到 / 打开
此源代码管理插件测试区域介绍将放置在源代码管理下的项目或解决方案，并检索它们从源代码管理。  
  
## <a name="command-menu-access"></a>命令菜单访问  
 以下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境菜单路径使用的测试用例：  
  
-   有关[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]、 从源代码管理打开：**文件**，**打开**，**项目**/**解决方案**; 查找中[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]位置。  
  
-   为其他源控件插件，从源代码管理打开：**文件**，**源代码管理**，**从源代码管理打开**。  
  
-   添加到源代码管理：**文件**，**源代码管理**，**将解决方案添加到源代码管理文件**，**源代码管理**，**添加所选项目添加到源管理**。  
  
-   快捷菜单 （项目/解决方案），**将解决方案添加到源代码管理**。  
  
-   从源代码管理中的添加：**文件**，**源代码管理**，**从源代码管理中添加项目**。  
  
-   有关[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]，添加从源控件也会从可用**文件**，**添加**，**现有项目**; 查找中[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]位置。  
  
    > [!NOTE]
    >  可以在此测试中使用的本地文件或本地 IIS （web 服务器） 的路径。  
  
## <a name="expected-behavior"></a>预期的行为  
  
-   对于每个支持的项目类型，用户应该能够"将添加到"和"打开从"源代码管理。  
  
-   当项目添加到源代码管理，相应\< *ProjectName*> 创建.vspscc 文件 （项目提示文件）。 它包含排除文件列表和连接信息。 不要删除此文件，因为它包含特定于项目的信息。  
  
-   当将解决方案添加到源代码管理，相应\< *SolutionName*> 创建.vssscc （三重 S） 文件。 文本文件包含连接信息和排除文件列表，类似于项目提示文件。 此文件是临时的且仅在从源代码管理数据库中存在。  
  
-   从源代码管理中，打开解决方案时\< *SolutionName*>.vsscc (double S) 只能在源代码管理数据库中存在的文件在临时文件在本地创建。 此文件包含从解决方案的连接文件夹到解决方案文件的路径。 此文件是临时的且本地副本中的内容将被删除，"从源代码管理打开"操作完成时。  
  
-   项目添加到源代码管理后，可以对其 （签出，Get，以及等等） 来执行任何源代码控制操作。  
  
## <a name="test-cases"></a>测试用例  
 以下是特定测试用例添加到 / 打开从源代码管理测试区域。  
  
### <a name="case-1a-add-solution-to-source-control"></a>案例 1a： 将解决方案添加到源代码管理  
 此测试用例侧重于将解决方案添加到源代码管理。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|将包含到源代码管理的客户端项目的解决方案添加|1.创建客户端项目。<br />2.将解决方案添加到源代码管理 (**文件**，**源代码管理**，**将解决方案添加到源代码管理**)。|解决方案/项目已添加到源代码管理。|  
|添加解决方案，其中包含一个文件系统或到源代码管理的本地 IIS Web 项目|1.创建一个文件系统或本地 IIS Web 项目 (使用浏览按钮来指向项目的位置; 路径确定创建什么类型的 Web 项目)。<br />2.将解决方案添加到源代码管理 (**文件**，**源代码管理**，**将解决方案添加到源代码管理**)。|解决方案/项目已添加到源代码管理。|  
|将包含到源代码管理的远程站点 Web 项目的解决方案添加|1.创建远程站点 Web 项目。<br />2.将解决方案添加到源代码管理 (**文件**，**源代码管理**，**将解决方案添加到源代码管理**)。<br />3.单击**确定**FrontPage 访问警告对话框中。|解决方案已添加到源代码管理。<br /><br /> 远程网站项目不在源控件下。 （远程站点项目必须控制从其自己的 IIS 服务器。）|  
|将单个项目解决方案添加到源控件使用**添加选定的项目添加到源代码管理**。|1.创建单个项目解决方案。<br />2.将仅解决方案添加到为选择的源代码管理 (**文件**，**源代码管理**，**添加选定的项目添加到源代码管理**)。 如果此步骤成功，则继续下一步。<br />3.添加到源代码管理为选择的项目 (**文件**，**源代码管理**，**添加选定的项目添加到源代码管理**)。<br />4.单击**是**将该项目添加到相同的位置。<br />5.单击**签出**中**签出以进行编辑**对话框。|`Result from Step 2:`<br /><br /> 项目和项目中的所有文件都具有签出源控件指示器和工具提示将显示"不受源代码管理"。<br /><br /> `Result from Step 5:`<br /><br /> 项目和解决方案文件是在源代码管理的同一文件夹中。|  
|取消将解决方案添加到源代码管理|1.创建单个项目解决方案。<br />2.尝试添加到源代码管理项目和解决方案。 如果此步骤成功，则继续下一步。<br />3.放入源代码管理系统后，取消。|`Result from Step 2:`<br /><br /> 设置项目位置源控件对话框仅出现一次。<br /><br /> `Result from Step 3:`<br /><br /> 项目添加已取消、 项目/解决方案不在源控件下，所有添加到源控件菜单仍可用。|  
  
### <a name="case-1b-open-solution-from-source-control"></a>事例 1b。 从源代码管理打开的解决方案  
 此测试用例重点介绍从源代码管理打开解决方案。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|打开包含从源代码管理的客户端项目的解决方案|1.创建客户端项目。<br />2.将解决方案添加到源代码管理。<br />3.关闭解决方案。<br />4.到新位置，请从源代码管理中打开的解决方案。|从源代码管理打开的解决方案/项目。|  
|打开包含本地或从源代码管理的 IIS Web 项目的解决方案|1.创建一个本地或 IIS Web 项目。<br />2.将解决方案添加到源代码管理。<br />3.关闭解决方案。<br />4.到新位置，请从源代码管理中打开的解决方案。|从源代码管理打开的解决方案/项目。|  
|打开包含从源代码管理的远程站点 Web 项目的解决方案|1.创建远程站点 Web 项目。<br />2.将解决方案添加到源代码管理。 如果此步骤成功，则继续下一步。<br />3.关闭解决方案。<br />4.到新位置，请从源代码管理中打开的解决方案。|`Result from Step 2:`<br /><br /> 远程站点 Web 不在源控件下。<br /><br /> `Result from Step 4:`<br /><br /> 从源代码管理打开的解决方案。<br /><br /> 已加载远程网站项目，但不在源控件下。|  
  
### <a name="case-1c-add-solution-from-source-control"></a>案例 1 c： 从源代码管理中添加解决方案  
 此测试用例重点介绍从源代码管理中添加解决方案。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|将添加到空解决方案-单个项目解决方案|1.创建单个项目解决方案。<br />2.将解决方案添加到源代码管理。<br />3.关闭解决方案。<br />4.创建第二个空解决方案。<br />5.从源代码管理中添加以前受控的解决方案 (**文件**，**源代码管理**，**从源代码管理中添加项目**)。|添加的项目将出现在**解决方案资源管理器**并签入。|  
|将添加到与单个项目的解决方案-单个项目|1.与单个项目创建一个解决方案。<br />2.将解决方案添加到源代码管理。<br />3.关闭解决方案。<br />4.创建第二个空解决方案。<br />5.从源代码管理中添加以前受控的解决方案 (**文件**，**源代码管理**，**从源代码管理中添加项目**)。|添加的项目将出现在**解决方案资源管理器**并签入。|  
|将添加到解决方案，按选定内容添加到源代码管理的解决方案|1.使用项目创建一个解决方案。<br />2.为选择仅解决方案添加到源代码管理。 如果此步骤成功，则继续下一步。<br />3.关闭解决方案。<br />4.创建一个新的解决方案。<br />5.从源代码管理中添加以前受控的解决方案 (**文件**，**源代码管理**，**从源代码管理中添加项目**)。|`Result from Step 2:`<br /><br /> 项目不在源控件下。<br /><br /> `Result from Step 5:`<br /><br /> 如果第一种解决方案有解决方案项，它们不能添加从源代码管理，因此它们不会显示。<br /><br /> 从第一个解决方案的项目将显示为不可用。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件的测试指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)