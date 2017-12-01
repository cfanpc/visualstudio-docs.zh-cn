---
title: "如何： 以编程方式在工作表中的数据排序 |Microsoft 文档"
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
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 211a357095290f8f8d608d01c093cd373c7525ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>如何：以编程方式对工作表中的数据进行排序
  在运行时，可以对工作表区域和列表中所包含数据进行排序。 以下代码先按第一列中的数据对名为 `Fruits` 的多列区域进行排序，然后按第二列中的数据进行相同操作。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sorting-data-in-a-document-level-customization"></a>对文档级自定义项中的数据进行排序  
  
#### <a name="to-sort-data-in-a-namedrange-control"></a>若要对 NamedRange 控件中的数据进行排序  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> 方法。 以下示例需要工作表上一个名为 `Fruits` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件。 必须将此代码置于表类中，而不是在 `ThisWorkbook` 类中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
 将以下代码置于 Sheet1.vb 或 Sheet1.cs 中，以对 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件中的数据进行排序。 该代码假定你在名为 `Sheet1` 的工作表中，具有名为 `fruitList` 的 <xref:Microsoft.Office.Tools.Excel.ListObject>控件。  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>对 ListObject 控件中的数据进行排序  
  
1.  调用 <xref:Microsoft.Office.Tools.Excel.ListObject> 主机控件的 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 属性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sorting-data-in-a-vsto-add-in"></a>对 VSTO 外接程序中的数据进行排序  
  
#### <a name="to-sort-data-in-a-native-range"></a>若要对本机范围内的数据进行排序  
  
1.  调用本机 Excel <xref:Microsoft.Office.Interop.Excel.Range> 控件的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。 以下示例需要工作表上一个名为 `Fruits` 的本机 Excel 控件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>对 ListObject 控件中的数据进行排序  
  
1.  调用本机 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控件的 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>属性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。 以下示例假定你在活动工作表中有名为 `fruitList` 的本机 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>另请参阅  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以编程方式自动用递增变化的数据填充范围](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何： 以编程方式引用代码中的工作表范围](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何： 以编程方式将样式应用于工作簿中的](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange 控件](../vsto/namedrange-control.md)   
 [ListObject 控件](../vsto/listobject-control.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  