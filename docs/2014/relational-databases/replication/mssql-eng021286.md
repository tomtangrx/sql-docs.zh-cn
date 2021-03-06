---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: af9407c14b970ee1b2c1108121c24f1368fbc29e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057577"
---
# <a name="mssqleng021286"></a>MSSQL_ENG021286
    
## <a name="message-details"></a>消息详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|21286|  
|事件源|MSSQLSERVER|  
|组件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符号名称||  
|消息正文|冲突表 '%s' 不存在。|  
  
## <a name="explanation"></a>解释  
 如果 [sysmergearticles (Transact-SQL)](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) 中所列项目的冲突表实际不存在，则会引发此错误。 尝试向为合并复制发布的表中添加列或从中删除列，也会发生此错误。  
  
## <a name="user-action"></a>用户操作  
 对缺少冲突表的数据库执行 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)，以验证是否不存在数据一致性问题。  
  
 如果订阅服务器上缺少冲突表，请删除订阅并重新创建它。 如果发布服务器上缺少冲突表，请删除所有订阅，删除发布，然后重新创建发布和所有订阅。 有关详细信息，请参阅[发布数据和数据库对象](publish/publish-data-and-database-objects.md)和[订阅发布](subscribe-to-publications.md)。  
  
## <a name="see-also"></a>请参阅  
 [错误和事件参考（复制）](errors-and-events-reference-replication.md)  
  
  
