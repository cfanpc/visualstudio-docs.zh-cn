---
title: "调试已部署的 ASP.NET 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 06/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 421c1f5f8736b9bd2cd95ac61570cc831c468c78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-deployed-aspnet-applications"></a>调试已部署的 ASP.NET 应用程序
若要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试已部署的应用程序，必须附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程，并确保调试器能够访问该应用程序的符号。 此外，还必须找到并打开该应用程序的源文件。 有关详细信息，请参阅[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)，[如何： 查找 ASP.NET 进程的名称](../debugger/how-to-find-the-name-of-the-aspnet-process.md)，和[系统要求](../debugger/aspnet-debugging-system-requirements.md)。  

> [!WARNING]
> 如果附加到[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]工作进程用于调试和命中断点，所有托管代码中辅助进程暂停。 暂停辅助进程中的所有托管代码会导致服务器上的所有用户的工作中断。 在成品服务器上进行调试之前，请考虑对生产工作的潜在影响。 
  
附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程与附加到任何其他远程进程的过程相同。 附加到辅助进程后，如果你没有打开合适的项目，则应用程序中断时，将显示一个对话框。 此对话框将提示您提供该应用程序源文件的位置。 在该对话框中指定的文件名必须与用调试符号（位于 Web 服务器上）指定的文件名匹配。 有关详细信息，请参阅[附加到运行进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。 若要设置在 IIS 上的远程调试，请参阅[远程 IIS 计算机上的远程调试 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。
 
> [!NOTE]
>  许多 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序都引用包含业务逻辑或其他有用代码的 DLL。 这种引用将复制该 DLL 从本地计算机到 Web 应用程序的虚拟目录的 \bin 文件夹部署您的应用程序时。 进行调试时，请记住 Web 应用程序引用的是 DLL 的这个副本，而不是本地计算机上的副本。 
  
## <a name="see-also"></a>另请参阅  
 [调试 ASP.NET 应用程序](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何： 为 ASP.NET 应用程序启用调试](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何： 查找 ASP.NET 进程的名称](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)