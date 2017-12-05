---
title: "sys.fn_validate_plan_guide (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fn_validate_plan_guide
- sys.fn_validate_plan_guide_TSQL
- fn_validate_plan_guide
- fn_validate_plan_guide_TSQL
dev_langs: TSQL
helpviewer_keywords:
- fn_validate_plan_guide function
- sys.fn_validate_plan_guide function
ms.assetid: 3af8b47a-936d-4411-91d1-d2d16dda5623
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fbca0ca02e994a3c286cea445965edd9cd53bfcf
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="sysfnvalidateplanguide-transact-sql"></a>sys.fn_validate_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  验证指定计划指南的有效性。 sys.fn_validate_plan_guide 函数返回计划指南应用于其查询时遇到的第一条错误消息。 如果计划指南有效，则将返回一个空的行集。 在更改了数据库的物理设计后，计划指南可能会变为无效。 例如，如果计划指南指定了特定索引并且随后将该索引删除，则查询将不能再使用该计划指南。  
  
 通过验证计划指南，可确定优化器是否能够在不进行修改的情况下直接使用该指南。 例如，基于函数的结果，可决定删除该计划指南并重新调整查询或修改数据库设计（例如，重新创建计划指南中指定的索引）。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
sys.fn_validate_plan_guide ( plan_guide_id )  
```  
  
## <a name="arguments"></a>参数  
 *plan_guide_id*  
 为计划指南的 ID 中报告[sys.plan_guides](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)目录视图。 *plan_guide_id*是**int**无默认值。  
  
## <a name="table-returned"></a>返回的表  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|msgnum|**int**|错误消息的 ID。|  
|severity|**tinyint**|消息的严重级别，在 1 到 25 之间。|  
|state|**int**|错误的状态号，用于指示发生错误的代码位置。|  
|message|**nvarchar(2048)**|错误的消息正文。|  
  
## <a name="permissions"></a>Permissions  
 OBJECT 作用域的计划指南要求对被引用的对象具有 VIEW DEFINITION 或 ALTER 权限，并要求具有编译计划指南中提供的查询或批处理的权限。 例如，如果批处理包含 SELECT 语句，则需要具有对被引用对象的 SELECT 权限。  
  
 SQL 或 TEMPLATE 作用域的计划指南要求对数据库具有 ALTER 权限，并要求具有编译计划指南中提供的查询或批处理的权限。 例如，如果批处理包含 SELECT 语句，则需要具有对被引用对象的 SELECT 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-validating-all-plan-guides-in-a-database"></a>A. 验证数据库中的所有计划指南  
 下面的示例检查当前数据库中所有计划指南的有效性。 如果返回一个空结果集，则所有计划指南都是有效的。  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT plan_guide_id, msgnum, severity, state, message  
FROM sys.plan_guides  
CROSS APPLY fn_validate_plan_guide(plan_guide_id);  
GO  
```  
  
### <a name="b-testing-plan-guide-validation-before-implementing-a-change-to-the-database"></a>B. 在对数据库实施更改前测试计划指南的有效性  
 下面的示例使用显式事务删除索引。 `sys.fn_validate_plan_guide`函数执行，以确定数据库中的任何计划指南将使此操作无效。 基于此函数的结果，将提交 `DROP INDEX` 语句或回滚事务，并且不删除索引。  
  
```tsql  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DROP INDEX IX_SalesOrderHeader_CustomerID ON Sales.SalesOrderHeader;  
-- Check for invalid plan guides.  
IF EXISTS (SELECT plan_guide_id, msgnum, severity, state, message  
           FROM sys.plan_guides  
           CROSS APPLY sys.fn_validate_plan_guide(plan_guide_id))  
    ROLLBACK TRANSACTION;  
ELSE  
    COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [计划指南](../../relational-databases/performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  