---
title: "ValueColumn 元素 (ASSL) |Microsoft 文档"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ValueColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ValueColumn element
ms.assetid: 6c2d6822-8ecc-46df-9fa9-bb92ac716c36
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c17b9dea933e1beee1f4957a9bb6f82c669963be
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="valuecolumn-element-assl"></a>ValueColumn 元素 (ASSL)
  标识提供父元素值的列。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|默认值|不定（请参阅“备注”）|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子元素|无|  
  
## <a name="remarks"></a>注释  
 如果[NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)元素**DimensionAttribute**指定，则相同**DataItem**值用作默认值**ValueColumn**元素。 如果**NameColumn**元素**DimensionAttribute**未指定与[KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)集合**DimensionAttribute**包含单个[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)元素表示与字符串数据类型相同的键列**DataItem**值用作默认值**ValueColumn**元素。  
  
 有关详细信息**DataItem**类型，包括 Analysis Services 脚本语言 (ASSL) 对象和属性表**DataItem**类型，请参阅[DataItem 数据类型 &#40;ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 对应的父级的元素**NameColumn**分析管理对象 (AMO) 对象模型中是<xref:Microsoft.AnalysisServices.DimensionAttribute>和<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>。  
  
## <a name="see-also"></a>另请参阅  
 [对象 &#40;ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  