---
title: "如何： 以编程方式添加图片和到文档的艺术字 |Microsoft 文档"
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
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a30c865a1bee9f3e8a75d5362688f1a83baba02a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>如何：以编程方式向文档中添加图片和艺术字
  可以在设计时或运行时向文档中添加图片和图形对象。 可使用“艺术字”向 Microsoft Office Word 文档添加装饰性文本。 这些特殊文本效果是一些图形对象，你可以自定义这些图形对象并插入到文档中。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="adding-a-picture-at-design-time"></a>在设计时添加图片  
 如果正在开发文档级自定义项，则可以在设计时向文档中添加图片。  
  
#### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>在设计时向 Word 文档添加图片  
  
1.  将光标置于文档中要插入图片的位置。  
  
2.  单击**插入**功能区选项卡。  
  
3.  在**图例**组中，单击**图片**。  
  
4.  在**插入图片**对话框中，导航到你想要插入，图片，然后单击**插入**。  
  
     图片将被添加到文档中光标当前所在的位置。  
  
## <a name="adding-a-picture-at-run-time"></a>在运行时添加图片  
 可以将图片插入文档中光标当前所在的位置。  
  
#### <a name="to-add-a-picture-at-the-cursor-location"></a>在光标位置添加图片  
  
1.  调用 <xref:Microsoft.Office.Interop.Word.InlineShapes> 集合的 <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> 方法，并传入文件名。  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="adding-wordart-at-design-time"></a>在设计时添加艺术字  
 如果正在开发文档级自定义项，则可以在设计时向文档中添加艺术字。  
  
#### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>在设计时向 Word 文档添加艺术字  
  
1.  将光标置于文档中要插入艺术字的位置。  
  
2.  单击**插入**功能区选项卡。  
  
3.  在**文本**组中，单击**艺术字**，然后选择艺术字样式。  
  
4.  添加你想要到文档中显示的文本**编辑艺术字文本**对话框中，单击**确定**。  
  
     这样文本就会添加到文档中，并应用选定的艺术字样式。  
  
## <a name="adding-wordart-at-run-time"></a>在运行时添加艺术字  
 可以将艺术字插入文档中光标当前所在的位置。 对于文档级自定义项和 VSTO 外接程序，此过程有所不同。  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>在文档级自定义项中的光标位置处添加艺术字  
  
1.  获取当前光标位置的左上角位置。  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  在文档中调用 <xref:Microsoft.Office.Interop.Word.Shapes> 对象的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>在 VSTO 外接程序中的光标位置处添加艺术字  
  
1.  获取当前光标位置的左上角位置。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  调用活动文档（或指定的其他文档）的 <xref:Microsoft.Office.Interop.Word.Shapes> 对象的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compiling-the-code"></a>编译代码  
  
-   名为图片**SamplePicture.jpg**必须位于驱动器 c。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 以编程方式打开现有文档](../vsto/how-to-programmatically-open-existing-documents.md)   
 [如何： 以编程方式在 Word 文档中插入文本](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何： 以编程方式在搜索后还原选定内容](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [如何： 以编程方式保存文档](../vsto/how-to-programmatically-save-documents.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  