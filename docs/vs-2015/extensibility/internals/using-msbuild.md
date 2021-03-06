---
title: 使用 MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 887afab85738e33bccd56543772b576e3843fe92
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675226"
---
# <a name="using-msbuild"></a>使用 MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MSBuild 提供了用于创建全面地描述要生成、 生成任务，并生成配置的项目项的项目文件以定义完善且可扩展 XML 格式。  
  
 基于 MSBuild 的语言项目系统的端到端示例，请参阅 IronPython 示例中的深入探讨[VSSDK 示例](../../misc/vssdk-samples.md)。  
  
## <a name="general-msbuild-considerations"></a>常规 MSBuild 注意事项  
 MSBuild 项目文件，例如， [!INCLUDE[csprcs](../../includes/csprcs-md.md)] .csproj 和[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].vbproj 文件包含在生成时使用，但也可以包含在设计时使用的数据的数据。 使用 MSBuild 基元，包括存储生成时数据[Item 元素 (MSBuild)](../../msbuild/item-element-msbuild.md)并[Property 元素 (MSBuild)](../../msbuild/property-element-msbuild.md)。 设计时数据，这是特定于项目类型和任何相关的项目子类型的数据，存储在为其保留的自由的 XML。  
  
 MSBuild 不具有对配置对象的本机支持，但提供了用于指定特定于配置数据条件属性。 例如：  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 条件属性的详细信息，请参阅[条件构造](../../msbuild/msbuild-conditional-constructs.md)。  
  
### <a name="extending-msbuild-for-your-project-type"></a>将 MSBuild 扩展的项目类型  
 MSBuild 接口和 Api 可能会有所更改的未来版本中[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 因此，它是比较明智的做法是，若要使用托管的包框架 (MPF) 类，因为它们提供从更改屏蔽。  
  
 托管包框架中的项目 (MPFProj) 提供了用于创建和管理新的项目系统的帮助程序类。 可找到的源的代码和编译说明[项目的 Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 特定于项目的 MPF 类如下所示：  
  
|类|实现|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` 类是 MSBuild 项的包装器。  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>单个文件生成器 vs。MSBuild 任务  
 单个文件生成器是在仅设计时可访问，但在设计时和生成时使用 MSBuild 任务。 最大的灵活性，因此，使用 MSBuild 任务来转换和生成代码。 有关详细信息，请参阅[自定义工具](../../extensibility/internals/custom-tools.md)。  
  
## <a name="see-also"></a>请参阅  
 [MSBuild 参考](../../msbuild/msbuild-reference.md)   
 [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [自定义工具](../../extensibility/internals/custom-tools.md)
