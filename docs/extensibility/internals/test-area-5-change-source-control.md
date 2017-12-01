---
title: "测试区域 5： 更改源控制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9e1bbce7fd1727bc629f015894c16b1d56a2150
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-5-change-source-control"></a>测试区域 5： 更改源代码管理
此源代码管理插件测试区域涉及更改通过的源控件**更改源代码管理**命令。  
  
 **更改源代码管理**命令为用户提供四项基本功能：  
  
-   **绑定：**  
  
     允许用户建立或重新建立解决方案/项目和版本存储区之间的源控件链接。  
  
-   **取消绑定：**  
  
     从基于每个连接的源控件中移除项目/解决方案。  
  
-   **连接/断开连接：**  
  
 受控的解决方案，这会在区域 3 介绍切换连接或脱机状态。 有关详细信息，请参阅[测试区域 3： 签出 / 撤消签出](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)。  
  
## <a name="command-menu-access"></a>命令菜单访问  
 以下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的测试用例使用集成的开发环境菜单路径。  
  
 更改源代码管理：**文件**，**源代码管理**，**更改源代码管理**。  
  
## <a name="test-cases"></a>测试用例  
 以下是针对特定测试用例**更改源代码管理**命令测试区域。  
  
### <a name="case-5a-bind"></a>案例 5a： 绑定  
 绑定允许用户将源代码控制信息添加到所选的项目和解决方案。 通常，将提示用户来标识这些是要添加源代码管理中的项目。 用户不可能在作为此操作 （添加到源代码管理与不同） 的一部分的源代码管理中创建新项目。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|将绑定到空的位置|1.创建项目。<br />2.将解决方案添加到源代码管理。<br />3.打开**更改源代码管理**对话框 (**文件**，**源代码管理**，**更改源代码管理**)。<br />4.单击**取消绑定**。<br />5.接受警告对话框中，如果它显示。<br />6.选择所有项。<br />7.单击**绑定**。<br />8.浏览到源代码管理存储区中的空位置。<br />9.单击**确定**关闭**更改源代码管理**对话框。<br />10.单击**继续使用这些绑定**在确认对话框中。<br />11.单击**确定**警告对话框中，如果它显示中。<br />12.签入的所有内容。 如果此步骤成功，则继续下一步。<br />13.到新位置，请从源代码管理中打开解决方案。|`Result from Step 12:`<br /><br /> 解决方案和项目是绑定到的写入到新的目标版本存储区中。<br /><br /> 解决方案和项目文件已签入。<br /><br /> 版本存储项目层次结构匹配磁盘上的项目的文件夹层次的结构。<br /><br /> `Result from Step 13:`<br /><br /> 将下载所有项目项。|  
|将绑定到与客户端同步的位置|1.创建项目。<br />2.将解决方案添加到源代码管理。<br />3.在版本存储区中创建的解决方案和项目的副本 (共享和分支如果使用[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />4.打开**更改源代码管理**对话框 (**文件**，**源代码管理**，**更改源代码管理**)。<br />5.取消绑定所有。<br />6.单击**确定**关闭**更改源代码管理**对话框。<br />7.重新打开**更改源代码管理**对话框。<br />8.全选。<br />9.单击**绑定**。<br />10.浏览到的解决方案和项目的分支位置 （从步骤 3）<br />11.单击**确定**关闭**更改源代码管理**对话框。<br />12.获取所有项的最新的以递归方式。|Get 后前 get 一样，则文件内容。|  
|将绑定到与客户端不同步的位置|1.创建项目。<br />2.将解决方案添加到源代码管理。<br />3.在版本存储区中创建的解决方案和项目的副本 (共享和分支如果使用[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />4.修改版本存储区中分支的项目中的文件。<br />5.打开**更改源代码管理**对话框 (**文件**，**源代码管理**，**更改源代码管理**)。<br />6.取消绑定所有。<br />7.单击**确定**关闭**更改源代码管理**对话框。<br />8.重新打开**更改源代码管理**对话框。<br />9.全选。<br />10.单击**绑定**。<br />11.浏览到分支为解决方案和项目的位置。<br />12.单击**确定**关闭**更改源代码管理**对话框。<br />13.接受警告对话框中，如果它显示。<br />14.获取所有项的最新的递归。|此外会本地修改已在步骤 4 中修改的文件。|  
|将绑定永远不会受源代码管理的解决方案|1.在源代码管理中创建空的文件夹。<br />2.创建客户端项目。<br />3.打开**更改源代码管理**对话框 (**文件**，**源代码管理**，**更改源代码管理**)。<br />4.将解决方案绑定到在源代码管理中的空位置。<br />5.单击**确定**关闭**更改源代码管理**对话框。<br />6.单击**继续使用这些绑定**在确认对话框中。<br />7.单击**确定**警告对话框中，如果它显示中。|解决方案添加到源代码管理。<br /><br /> 解决方案和项目已签出。|  
|取消绑定|1.创建项目。<br />2.将解决方案添加到源代码管理。<br />3.打开更改源代码管理对话框。<br />4.取消绑定所有。<br />5.单击**确定**按钮以关闭对话框。 如果此步骤成功，则继续下一步。<br />6.重新打开**更改源代码管理**对话框。<br />7.将绑定到不相关的位置。<br />8.单击**取消**。|`Result from Step 5:`<br /><br /> 解决方案不再受源代码管理<br /><br /> `Result from Step 8:`<br /><br /> 解决方案是仍不处于源代码管理。|  
  
### <a name="case-5b-unbind"></a>案例 5b： 取消绑定  
 取消绑定中删除源代码控件从项目和其解决方案的信息。 受影响的项目和解决方案基于用户选择和如何项目已添加到源代码管理的组合。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|取消绑定包含一个文件系统或本地 IIS Web 项目和一个客户端项目的解决方案|1.创建一个文件系统或本地 IIS Web 项目。<br />2.将解决方案添加到源代码管理。<br />3.向解决方案添加新的客户端项目。<br />4.如果系统提示，则接受检查出的解决方案。<br />5.打开**更改源代码管理**对话框。<br />6.单击**取消绑定**。<br />7.单击“确定”关闭对话框。<br />8.尝试签出解决方案、 项目、 解决方案项、 项目项。|解决方案和项目不在源代码管理下。<br /><br /> 源代码管理菜单命令不会出现。|  
|取消取消绑定|1.创建项目。<br />2.将解决方案添加到源代码管理。<br />3.打开**更改源代码管理**对话框。<br />4.单击**取消绑定所有**。<br />5.单击**取消**。|解决方案是在源代码管理下。|  
  
### <a name="case-5c-rebind"></a>案例 5c： 重新绑定  
 重新绑定是只需取消绑定和绑定的组合 — 重新绑定，以前在源代码管理下，未绑定项目/解决方案的过程。  
  
|操作|测试步骤|若要验证的预期的结果|  
|------------|----------------|--------------------------------|  
|重新绑定解决方案和项目无需关闭**更改源代码管理**对话框|1.创建项目。<br />2.将解决方案添加到源代码管理。<br />3.打开**更改源代码管理**对话框。<br />4.单击**取消绑定**。<br />5.选择所有行。<br />6.单击**绑定**。<br />7.单击**确定**关闭**更改源代码管理**对话框。<br />8.如果系统提示，请接受签出。|解决方案和项目是在源代码管理下。|  
|重新绑定仅无需关闭项目**更改源代码管理**对话框|1.创建项目。<br />2.将只将项目添加到源控件使用 (文件-> 源控件-> 将所选项目添加到源代码管理。<br />3.打开更改源代码管理对话框。<br />4.取消绑定只将项目。<br />5.将仅项目的绑定。|解决方案将保持不受控制。<br /><br /> 项目保留受控。|  
|重新绑定仅无需关闭解决方案**更改源代码管理**对话框|1.创建项目。<br />2.仅将解决方案添加到源控件使用 (**文件**，**源代码管理**，**添加选定的项目添加到源代码管理**。<br />3.打开**更改源代码管理**对话框。<br />4.取消绑定仅该解决方案 (不要关闭**更改源代码管理**对话框。)<br />5.将绑定仅解决方案。<br />6.单击“确定”关闭对话框。<br />7.签出解决方案和解决方案项 （如果有。）|解决方案将保持受控。<br /><br /> 项目还是保持不受控制。|  
|重新绑定解决方案/仅时相同的目录中的项目|1.创建项目。<br />2.将只将项目添加到源控件使用 (**文件**，**源代码管理**，**添加选定的项目添加到源代码管理**。<br />3.关闭解决方案。<br />4.使用至少两个项目创建一个新的解决方案。<br />5.将解决方案添加到源代码管理。<br />6.添加在步骤 1 中创建从源代码管理的项目。<br />7.如果系统提示，请接受解决方案签的出。<br />8.检查整个解决方案中。<br />9.打开**更改源代码管理**对话框。<br />10.选择 （从步骤 6) 添加的项目，然后单击**拆散**。<br />11.单击“确定”关闭对话框。<br />12.如果系统提示，请接受签出。<br />13.重新打开**更改源代码管理**对话框。<br />14.选择 （从步骤 6) 添加的项目，然后单击**绑定**。<br />15.选择原始位置。|解决方案和项目保持受控。|  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件的测试指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)