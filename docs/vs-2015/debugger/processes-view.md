---
title: 进程视图 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c83b57ade3a78a4dcc926e34547ee566326e129
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47477750"
---
# <a name="processes-view"></a>进程视图
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[进程视图](https://docs.microsoft.com/visualstudio/debugger/processes-view)。  
  
进程视图显示在系统上的所有活动进程树。 显示进程 ID 和模块名称。 如果你想要检查特定系统进程，它通常对应于正在执行的程序，请使用进程视图。 进程标识由模块名称，或者它们被指定"系统进程"。  
  
 Microsoft Windows 支持多个进程。 每个进程都可以有一个或多个线程和每个线程可以具有一个或多个关联的顶级窗口。 每个顶层窗口都可以拥有一系列的 windows。 一个 + 符号指示一个级别处于折叠状态。 折叠的视图包含每个进程的一行。 单击加号以展开级别。  
  
 如果你想要检查特定系统进程，它通常对应于正在执行的程序，请使用进程视图。 进程标识由模块名称，或者它们被指定"系统进程"。 若要查找一个过程，折叠决策树和搜索列表。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-open-the-processes-view"></a>若要打开进程视图  
  
1.  从**Spy**菜单中，选择**进程**。  
  
 ![Spy&#43; &#43;进程视图](../debugger/media/spy-processes.png "Spy + + _Processes")  
Spy++ 进程视图  
  
 上图中显示与进程和线程节点已展开进程视图。  
  
### <a name="in-this-section"></a>本节内容  
 [在进程视图中的进程搜索](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 介绍如何在进程视图中查找特定的进程。  
  
 [显示进程属性](../debugger/how-to-display-process-properties.md)  
 说明如何显示一条消息的详细信息。  
  
### <a name="related-sections"></a>相关章节  
 [Spy++ 视图](../debugger/spy-increment-views.md)  
 介绍 windows、 消息、 进程和线程的 Spy + + 树的视图。  
  
 [使用 Spy++](../debugger/using-spy-increment.md)  
 引入了 Spy + + 工具，并说明如何使用它。  
  
 [“进程搜索”对话框](../debugger/process-search-dialog-box.md)  
 用于查找特定的进程在进程视图中的节点。  
  
 [“进程属性”对话框](../debugger/process-properties-dialog-box.md)  
 显示在进程视图中选择的进程的属性。  
  
 [Spy++ 参考](../debugger/spy-increment-reference.md)  
 包含描述每个 Spy + + 菜单和对话框中的各个部分。


