---
title: "参数的集合引用 （报表生成器和 SSRS） |Microsoft 文档"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4b47e15-0484-4c13-9182-898db825f01f
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 17698a3c268e824d2f638042b71b3ec21f994e86
ms.contentlocale: zh-cn
ms.lasthandoff: 08/09/2017

---
# <a name="built-in-collections---parameters-collection-references-report-builder"></a>内置集合的参数的集合引用 （报表生成器）
  报表参数是可以在表达式中引用的内置集合之一。 通过在表达式中包含参数，您可以基于用户的选择来自定义报表的数据和外观。 表达式可以用于任何报表项属性或提供的文本框属性 (*Fx*) 或\<**表达式**> 选项。 表达式还可用于以其他方式控制报表的内容和外观。 有关详细信息，请参阅[表达式示例（报表生成器和 SSRS）](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)。  
  
 在运行时比较参数值和数据集字段值时，所比较的两个项的数据类型必须相同。 报表参数可以是下列类型之一：Boolean、DateTime、Integer、Float 或 Text，它们表示基础数据类型 String。 如有必要，您可能必须转换参数值的数据类型以与数据集值相匹配。 有关详细信息，请参阅 [表达式中的数据类型（报表生成器和 SSRS）](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)。  
  
 为了在表达式中包含参数引用，必须了解如何指定正确的参数引用语法，该语法会因参数是单值参数还是多值参数而有所不同。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="Single"></a> 在表达式中使用单值参数  
 下表显示了在表达式中包含对任何数据类型单值参数的引用时所用的语法示例。  
  
|示例|Description|  
|-------------|-----------------|  
|`=Parameters!` *\<ParameterName >*`.IsMultiValue`|返回 **False**。<br /><br /> 检查参数是否是多值。 如果是 **True**，则该参数是多值并且是一个对象集合。 如果是 **False**，则该参数是单值并且是单个对象。|  
|`=Parameters!` *\<ParameterName >*`.Count`|返回整数值 1。 对于单值参数，该计数始终为 1。|  
|`=Parameters!` *\<ParameterName >*`.Label`|返回参数标签，该参数标签通常用作可用值下拉列表中的显示名称。|  
|`=Parameters!` *\<ParameterName >*`.Value`|返回参数值。 如果尚未设置 Label 属性，则此值会显示在可用值的下拉列表中。|  
|`=CStr(Parameters!`  *\<参数名称 >*`.Value)`|返回该参数值作为字符串。|  
|`=Fields(Parameters!` *\<ParameterName >*`.Value).Value`|返回与参数同名的字段的值。|  
  
 有关在筛选器中使用参数的详细信息，请参阅[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)。  
  
##  <a name="Multi"></a> 在表达式中使用多值参数  
 下表显示了在表达式中包含对任何数据类型多值参数的引用时所用的语法示例。  
  
|示例|Description|  
|-------------|-----------------|  
|`=Parameters!` *\<MultivalueParameterName >*`.IsMultiValue`|返回 **True** 或 **False**。<br /><br /> 检查参数是否是多值。 如果是 **True**，则该参数是多值并且是一个对象集合。 如果是 **False**，则该参数是单值并且是单个对象。|  
|`=Parameters!` *\<MultivalueParameterName >*`.Count`|返回整数值。<br /><br /> 表示值的数量。 对于单值参数，该计数始终为 1。 对于多值参数，该计数为 0 或更多。|  
|`=Parameters!` *\<MultivalueParameterName >*`.Value(0)`|返回多值参数中的第一个值。|  
|`=Parameters!` *\<MultivalueParameterName >* `.Value(Parameters!`  *\<MultivalueParameterName >*`.Count-1)`|返回多值参数中的最后一个值。|  
|`=Split("Value1,Value2,Value3",",")`|返回一组值。<br /><br /> 为多值 **String** 参数创建值数组。 可以在第二个参数中使用分隔符拆分。 可以使用该表达式为多值参数设置默认值，或创建多值参数以发送至子报表或钻取报表。|  
|`=Join(Parameters!` *\<MultivalueParameterName >*`.Value,", ")`|返回一个 **String** ，它包含以逗号分隔的多值参数中的值列表。 可以在第二个参数中使用任何分隔符进行联接。|  
  
 有关筛选器中使用参数的详细信息，请参阅[报表参数 &#40;报表生成器和报表设计器 &#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>另请参阅  
 [表达式（报表生成器和 SSRS）](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [常用筛选器 &#40;报表生成器和 SSRS &#41;](../../reporting-services/report-design/commonly-used-filters-report-builder-and-ssrs.md)   
 [添加、 更改或删除报表参数 &#40;报表生成器和 SSRS &#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)   
 [教程： 将参数添加到您的报表 &#40;报表生成器 &#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [报表生成器教程](../../reporting-services/report-builder-tutorials.md)   
 [表达式 &#40; 中的内置集合报表生成器和 SSRS &#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md)  
  
  