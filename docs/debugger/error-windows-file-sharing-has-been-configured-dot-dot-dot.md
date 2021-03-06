---
title: 错误：Windows 文件共享已配置...|Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 89224dc5394f248ea82d428731ef387cb705ff27
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850044"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>错误：已配置 Windows 文件共享...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

已配置 Windows 文件共享，因此您将使用另一不同的用户名连接到远程计算机。 这与远程调试不兼容  
  
 当前文件共享配置设置为使用另一用户名连接到远程计算机。 在这种情况下不能进行远程调试。  
  
 若要更正此错误，请使用其他帐户名登录到计算机上，或是更改文件共享以使用要用来进行调试的帐户名。  
  
 如果要使用此用户名连接到远程计算机，则必须首先从远程计算机断开连接。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1. 使用其他帐户名登录到本地计算机（要从其进行调试的计算机）上。  
  
     - 或 -  
  
     . 中断与远程计算机的连接，然后重新配置文件共享，以便使用您的帐户名称连接至其他计算机：  
  
    1. 在**开始**菜单中，指向**附件**，然后单击**命令提示符**。  
  
    2. 在 Windows 命令提示符中，键入：  
  
         `net use /delete computer_name`  
  
    3. 使用 Windows 帮助中介绍的任一方法更改文件共享设置。
