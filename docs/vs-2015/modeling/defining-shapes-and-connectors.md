---
title: 定义形状和连接线 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 761e0e77a0fe9f6f32f08045d81f6eab815801dd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112320"
---
# <a name="defining-shapes-and-connectors"></a>定义形状和连接线
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在域特定语言 (DSL) 中，有多种基本类型的形状，可用于在关系图上显示信息。  
  
## <a name="shapeTypes"></a> 基本类型的形状和连接线  
 DSL 关系图显示了一系列*形状*连接符的行或*连接器*。  通常情况下（但并非总是如此）：  
  
- 形状是模型元素的可视表示形式。  
  
- 连接符表示引用关系。  
  
- 关系图表示模型根实例。  
  
- 模型元素之间的嵌入关系通过包容来显示。 例如，表示组件端口的元素将嵌入在组件中。  
  
  不会强制使用这些模式，但强烈支持使用它们。 在设计 DSL 时，请记住，嵌入关系的设计应受你希望在屏幕上呈现模型的方式所影响。 相比之下，引用关系应反映业务域的概念。  
  
  提供以下类型的形状：  
  
|形状类型|描述|  
|----------------|-----------------|  
|几何图形|通用矩形或椭圆形形状。 可在相对于形状边界的特定位置中显示文本和图标修饰器。<br /><br /> 若要将嵌套在几何形状内的形状，请参阅[嵌套形状](../modeling/nesting-shapes.md)。|  
|隔离舱形状|包含标头和隔离舱的矩形（如 UML 类）。 每个隔离舱都可包含文本行列表。<br /><br /> 这些行通常表示嵌入在由形状表示的元素下方的元素。 有关示例，请从类关系图解决方案模板中创建 DSL。|  
|图像形状|显示图像的形状。|  
|端口形状|设计为附加到另一个形状的轮廓的小矩形。 通常用于组件模型中。<br /><br /> 由端口表示的模型元素通常嵌入在由父形状表示的元素下。 有关示例，请通过使用组件解决方案模板创建 DSL。<br /><br /> 默认情况下，端口形状可沿其父形状的侧边滑动。 可定义边界规则以将其约束到特定位置。<br /><br /> 通过使端口形状变得极小并使其透明，可将其用于在其父形状的图面上提供一个固定连接点。|  
|泳道|泳道将关系图分为水平或垂直段。 在该关系图上，泳道始终位于其他形状的下方。<br /><br /> 通常泳道的模型元素是模型根上的父级，而其他元素是它们的父级。 有关示例，请从任务流解决方案模板中创建 DSL。|  
|连接符|在形状之间绘制的线条通常表示引用关系。 可设置选项以使连接符绘制为直线或折线，并带有不同类型的箭头。|  
  
## <a name="shapeInheritance"></a> 形状继承  
 一个形状可继承自另一个形状。 但是，这些形状的类型必须相同。 例如，几何形状只能继承自几何形状。 继承形状具有其基形状的隔离舱和修饰器。 连接符可继承自连接符。
