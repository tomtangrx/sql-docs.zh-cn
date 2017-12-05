---
title: "sp_help_spatial_geometry_index (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_index
- sp_help_spatial_geometry_index_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_spatial_geometry_index procedure
ms.assetid: f1bcefb1-09c8-4b49-8c51-5d471065849f
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b91735734ed05f6132dbebb7ca7eaf5a26f703fa
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpspatialgeometryindex-transact-sql"></a>sp_help_spatial_geometry_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  名称和一组指定的属性的值将返回有关**几何图形**空间索引。 以表格式返回结果。 可以选择是返回索引的一组核心属性还是返回索引的所有属性。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_help_spatial_geometry_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput'   
     [ , [ @query_sample = ] 'query_sample']   
```  
  
## <a name="arguments"></a>参数  
 请参阅[自变量和空间索引的属性存储过程](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)。  
  
## <a name="property-valuereturn-value"></a>属性值/返回值  
 请参阅[自变量和空间索引的属性存储过程](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)。  
  
## <a name="permissions"></a>Permissions  
 必须为用户分配一个 PUBLIC 角色以便能够访问该过程。 需要服务器和对象的 READ ACCESS 权限。  
  
## <a name="remarks"></a>注释  
 包含 NULL 值的属性未包含在返回集中。  
  
## <a name="example"></a>示例  
 下面的示例使用`sp_help_spatial_geometry_index`调查空间索引**SIndx_SpatialTable_geometry_col2**在表上定义**geometry_col**中给定的查询示例 **@qs**. 此示例只返回指定索引的核心属性。  
  
```  
declare @qs geometry  
        ='POLYGON((-90.0 -180.0, -90.0 180.0, 90.0 180.0, 90.0 -180.0, -90.0 -180.0))';  
exec sp_help_spatial_geometry_index 'geometry_col', 'SIndx_SpatialTable_geometry_col2', 0, @qs;  
```  
  
## <a name="see-also"></a>另请参阅  
 [空间索引存储过程](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index_xml](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)   
 [空间索引概述](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [空间数据 (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  