---
title: "GETUTCDATE （SSIS 表达式） |Microsoft 文档"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fd7919482026f85d9261c2a36d16defdf6b59cd9
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE（SSIS 表达式）
  使用 DT_DBTIMESTAMP 格式返回以 UTC 时间（协调世界时或格林尼治标准时间）表示的系统当前日期。 GETUTCDATE 函数不带参数。  
  
## <a name="syntax"></a>语法  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>参数  
 InclusionThresholdSetting  
  
## <a name="result-types"></a>结果类型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>表达式示例  
 此示例返回以 UTC 时间表示的当前日期的年份。  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 此示例返回 **ModifiedDate** 列中的日期和当前 UTC 日期之间的天数。  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 此示例将三个月加到当前 UTC 日期。  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>另请参阅  
 [GETDATE &#40;SSIS 表达式 &#41;](../../integration-services/expressions/getdate-ssis-expression.md)   
 [函数 &#40;SSIS 表达式 &#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  