---
title: ABS（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c787a67c1c3a65b695e3fc7af79f2eda7c86f3be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852145"
---
# <a name="abs-ssis-expression"></a>ABS（SSIS 表达式）
  返回数值表达式的绝对值。  
  
## <a name="syntax"></a>语法  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>参数  
 *numeric_expression*  
 是有符号或无符号的数值表达式。  
  
## <a name="result-types"></a>结果类型  
 提交给函数的数值表达式的数据类型。  
  
## <a name="remarks"></a>Remarks  
 如果该参数为空，则 ABS 返回的结果为空。  
  
## <a name="expression-examples"></a>表达式示例  
 这些示例对一个正数和一个负数应用 ABS 函数。 两者都返回 1.23。  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 此示例对将变量 **HighTemperature** 和 **LowTempature**的值相减的表达式应用 ABS 函数。  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>另请参阅  
 [函数（SSIS 表达式）](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
