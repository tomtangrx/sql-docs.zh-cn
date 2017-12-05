---
title: "执行语句 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e617e4550766b7952961c3dae6830eaebdd2686a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="executing-statements-odbc"></a>执行语句 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序提供的各种方式来执行 SQL 语句中的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]数据库：  
  
-   直接执行  
  
-   准备好的执行  
  
 直接执行涉及到生成的字符字符串包含[!INCLUDE[tsql](../../../includes/tsql-md.md)]语句并将其提交执行使用**SQLExecDirect**函数。 准备好的执行即生成一个包含 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句的字符串，然后分两个阶段执行。 第一个阶段将使用[SQLPrepare 函数](http://go.microsoft.com/fwlink/?LinkId=59360)函数来分析和编译中的语句的执行计划[!INCLUDE[ssDE](../../../includes/ssde-md.md)]。 第二个阶段将使用**SQLExecute**函数来执行之前准备好的执行计划。 这节省了每次执行的分析和编译开销。 应用程序通常使用准备好的执行来重复执行相同的参数化 SQL 语句。  
  
 直接执行和准备好的执行都可以执行单个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句或批处理 SQL 语句，也可以调用存储过程。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [直接执行](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [准备好的执行](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [过程](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [语句的批处理](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [ISO 选项的作用](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>另请参阅  
 [正在执行查询 &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  