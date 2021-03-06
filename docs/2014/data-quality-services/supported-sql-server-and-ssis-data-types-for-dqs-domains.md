---
title: DQS 域支持的 SQL Server 和 SSIS 数据类型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d5ab84f7892b3ef4e146096c2bc35201585d782b
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2018
ms.locfileid: "51029708"
---
# <a name="supported-sql-server-and-ssis-data-types-for-dqs-domains"></a>DQS 域支持的 SQL Server 和 SSIS 数据类型
  SQL Server 和 SQL Server Integration Services (SSIS) 中有很多数据类型，但是只有四种数据类型用于 DQS 域：Date、Decimal、Integer 和 String。 并非所有 SQL Server 和 SSIS 数据类型在 DQS 中都受支持。 仅当源数据类型在 DQS 中受支持且与 DQS 域数据类型匹配时，才能将源数据映射到 DQS 域来执行数据质量活动。 本主题提供有关支持的可映射到 DQS 中四种域数据类型之一的 SQL Server 和 SSIS 数据类型信息。  
  
> [!NOTE]  
>  在 .xlsx 和 .xls 文件中，源列的数据类型由前八行中最主要的数据类型确定。 如果某一单元不符合该数据类型，将向它提供 null 值。 同样，在 .csv 文件中，源列的数据类型由前八行中最主要的数据类型确定。  
  
##  <a name="SQLServer"></a> 支持的 SQL Server 数据类型  
 下表提供有关对于每种 DQS 域数据类型支持的 SQL Server 数据类型的信息：  
  
|DQS 域数据类型|支持的 SQL Server 数据类型|  
|--------------------------|------------------------------------|  
|date|日期|  
|Decimal|Decimal<br /><br /> FLOAT<br /><br /> money<br /><br /> NUMERIC<br /><br /> REAL<br /><br /> SMALLMONEY|  
|Integer|BIGINT<br /><br /> ssNoversion<br /><br /> smallint<br /><br /> TINYINT|  
|String|char<br /><br /> NCHAR<br /><br /> NVARCHAR<br /><br /> varchar|  
  
 其余 SQL Server 数据类型在 DQS 中不受支持。 有关所有 SQL Server 数据类型的信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。  
  
##  <a name="SSIS"></a> 支持的 SSIS 数据类型  
 下表提供有关对于每种 DQS 域数据类型支持的 SSIS 数据类型的信息：  
  
|DQS 域数据类型|支持的 SSIS 数据类型|  
|--------------------------|------------------------------|  
|date|DT_DATE|  
|Decimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|Integer|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|String|DT_STR<br /><br /> DT_WSTR|  
  
 其余 SSIS 数据类型在 DQS 中不受支持。 有关所有 SSIS 数据类型的信息，请参阅 [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md)。  
  
## <a name="see-also"></a>请参阅  
 [管理域](../../2014/data-quality-services/managing-a-domain.md)  
  
  
