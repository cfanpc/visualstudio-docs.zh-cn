---
title: "生成 Office 解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
ms.assetid: c4b79ea8-df70-4a72-b76e-26e337d65727
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3df5fca6d41070b09ceb8b8be9b05212b7caa69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="building-office-solutions"></a>生成 Office 解决方案
  通常情况下，生成和调试 Office 项目与在 Visual Studio 中生成和调试其他类型的项目（例如 Windows 窗体）相同。 本部分的主题介绍存在的差异。 有关如何生成应用程序的常规信息，请参阅[编译和 Visual Studio 中生成](/visualstudio/ide/compiling-and-building-in-visual-studio)。  
  
> [!NOTE]  
>  开发扩展的 Office 体验跨解决方案是否有兴趣[多个平台](https://dev.office.com/add-in-availability)？ 查看全新[Office 外接程序模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 外接程序具有内存占用较小与 VSTO 外接程序和解决方案，相比，并且你可以通过使用几乎任何 web 编程技术，例如 HTML5、 JavaScript、 CSS3 和 XML 生成它们。  
  
## <a name="project-output-for-office-projects"></a>Office 项目的项目输出  
 Office 项目的输出位置为 *projectname*\bin\release or *projectname*\bin\debug。 不能生成到部署目录中。  
  
### <a name="document-level-projects"></a>文档级项目  
 生成文档级项目时，项目输出中包含以下项：  
  
-   项目文档的副本。  
  
-   项目程序集以及“复制本地”  属性设置为 **true**的所有引用的程序集。  
  
-   文件扩展名为 .manifest 的应用程序清单。 有关更多信息，请参见 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)。  
  
-   文件扩展名为 .vsto 的部署清单。 有关更多信息，请参见 [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md)。  
  
-   程序数据库 (PDB) 文件。  
  
> [!NOTE]  
>  如果将文档级解决方案生成到远程位置（而不生成到本地计算机），请将完全限定路径添加到应用程序信任中心中的“受信任位置”列表。 有关详细信息，请参阅 [Securing Office Solutions](../vsto/securing-office-solutions.md)。  
  
### <a name="application-level-projects"></a>应用程序级项目  
 生成 VSTO 外接程序项目时，项目输出中包含以下项：  
  
-   项目程序集以及“复制本地”  属性设置为 **true**的所有引用的程序集。  
  
-   文件扩展名为 .manifest 的应用程序清单。 有关更多信息，请参见 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)。  
  
-   文件扩展名为 .vsto 的部署清单。 有关更多信息，请参见 [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md)。  
  
-   项目程序集的程序数据库 (PDB) 文件。  
  
 VSTO 外接程序项目的生成过程还会在开发计算机上创建加载 VSTO 外接程序所需的一组注册表项。 有关详细信息，请参阅 [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md)。  
  
 如果生成包含窗体区域的 Outlook VSTO 外接程序项目，生成过程会向注册表中添加以下附加信息：  
  
-   与一个或多个窗体区域关联的每个邮件类的键。  
  
-   每个窗体区域的项以及表示 Outlook VSTO 外接程序的名称的关联值。  
  
 Outlook 需要此信息来加载窗体区域。  
  
## <a name="referenced-assemblies"></a>引用的程序集  
 可以从“生成 Office 解决方案”项目引用程序集（包括类库项目）。 每个引用的程序集都具有一个名为“复制本地” 的属性。 “复制本地” 指示是否将程序集复制到输出目录中。 默认情况下，此属性设置为 **true**。 “复制本地”  设置为 **true** 的每个引用的程序集都被复制到输出目录中。  
  
## <a name="security-during-the-build-process"></a>生成过程中的安全性  
 Visual Studio 会自动配置开发计算机上的安全设置，以便在生成过程中向解决方案授予信任。 这样一来，解决方案将能在你对其进行调试时运行。  
  
 Office 项目使用证书来验证发布者。 Visual Studio 会自动创建一个临时证书来标识 Office 解决方案，并配置开发计算机以信任该临时证书。  
  
 有关详细信息，请参阅 [Securing Office Solutions](../vsto/securing-office-solutions.md)。  
  
### <a name="network-projects"></a>网络项目  
 如果程序集或文档位于网络共享位置，则本地（“用户”级别）安全策略更新不足以允许解决方案运行。 要使解决方案运行，管理员必须先在“计算机”级别向网络共享位置上的程序集和文档授予完全信任。 有关如何设置安全策略的详细信息，请参阅 [Securing Office Solutions](../vsto/securing-office-solutions.md)。  
  
 对于文档级项目，还必须将文档的完全限定位置添加到 Office 受信任文件夹列表。 有关更多信息，请参见 [Granting Trust to Documents](../vsto/granting-trust-to-documents.md)。  
  
## <a name="changing-the-platform-target"></a>更改目标平台  
 默认情况下，Office 项目的目标平台是“任何 CPU” 。 通常情况下，不应更改此设置。 使用“任何 CPU”  目标平台设置生成的 Office 解决方案在 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 或 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]的 32 位和 64 位版本上运行。  
  
 只有在创建仅在 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 或 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]的 64 位版本中运行的解决方案，并且该解决方案调用本机 64 位 API 时，才应将目标平台设置为 x64。 有关更改目标平台设置的详细信息，请参阅[如何： 向目标平台的配置项目](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
 如果将目标平台设置为 x64，则解决方案将不会在 Windows 或 Office 的 32 位版本中运行。 x64 目标平台要求解决方案在 64 位进程中运行。  
  
## <a name="using-the-clean-command"></a>使用“清除”命令  
 若要从开发计算机删除生成的项目文件，可以使用 **中的“生成”****菜单上的“清除”**[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]命令。 “清除”  命令可删除生成输出位置上的所有文件。 对于应用程序级项目，“清除”  命令还可删除生成过程创建的注册表项。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[调试 Office 项目](../vsto/debugging-office-projects.md)|存在涉及调试 Office 项目的问题。|  
|[演练：创建你的第一个 Excel 文档级自定义项](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|演示如何创建 Excel 的基本文档级自定义项。|  
|[如何：重新启用已禁用的 VSTO 外接程序](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|描述如何重新启用已被硬禁用或软禁用的 VSTO 外接程序。|  
|[设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)|提供一些链接，指向与创建 Office 解决方案以及程序集在解决方案中的角色有关的信息。|  
  
  