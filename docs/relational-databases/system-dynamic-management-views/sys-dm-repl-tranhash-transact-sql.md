---
title: sys.dm_repl_tranhash (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d10d4451071ac476b25fdfef00ab4a48d1c3f63
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736577"
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回有关事务发布中正在复制的事务的信息。  
  
|column_name|data_type|description|  
|------------------|----------------|-----------------|  
|**存储桶**|**bigint**|哈希表中的存储桶数。|  
|**hashed_trans**|**bigint**|当前批次中复制的已提交事务数。|  
|**completed_trans**|**bigint**|到目前为止的争用事务数。|  
|**compensated_trans**|**bigint**|包含部分回滚的事务数。|  
|**first_begin_lsn**|**nvarchar(64)**|当前批次中最早的起始日志序列号 (LSN)。|  
|**last_commit_lsn**|**nvarchar(64)**|当前批次中最后提交的 LSN。|  
  
## <a name="permissions"></a>Permissions  
 要求具有对发布数据库的 VIEW DATABASE STATE 权限，调用**dm_repl_tranhash**。  
  
## <a name="remarks"></a>备注  
 只为复制项目缓存中当前加载的复制的数据库对象返回信息。  
  
## <a name="see-also"></a>请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与复制相关的动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
