---
title: SQL Server XTP 游标 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 000b1a6815547487635bac28973cb06bf0cb8204
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158525"
---
# <a name="sql-server-xtp-cursors"></a>SQL Server XTP 游标
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP 游标性能对象包含与内部内存中 OLTP 引擎游标相关的计数器。 游标是内存中 OLTP 引擎用于处理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询的低级构建基块。 因此，您通常不能直接控制游标。  
  
 下表介绍了 **SQL Server XTP 游标** 计数器。  
  
|计数器|描述|  
|-------------|-----------------|  
|**游标删除数/秒**|每秒游标删除数（平均值）。|  
|**游标插入数/秒**|每秒游标插入数（平均值）。|  
|**启动的游标扫描数/秒**|每秒启动的游标扫描数（平均值）。|  
|**游标唯一冲突数/秒**|每秒唯一约束冲突数（平均值）。|  
|**游标更新数/秒**|每秒游标更新数（平均值）。|  
|**游标写冲突数/秒**|同一行版本每秒发生的写/写冲突数（平均值）。|  
|**灰尘角扫描重试次数/秒（用户发出）**|在用户全表扫描发出的灰尘角扫描期间，由于写冲突而进行的每秒扫描重试次数（平均值）。 此为非常低级的计数器，不适合客户使用。|  
|**删除的过期行数/秒**|游标每秒删除的过期行数（平均值）。|  
|**接触的过期行数/秒**|游标每秒接触的过期行数（平均值）。|  
|**返回的行数/秒**|游标每秒返回的行数（平均值）。|  
|**接触的行数/秒**|游标每秒接触的行数（平均值）。|  
|**接触的临时删除行数/秒**|游标每秒接触的即将到期的行数（平均值）。 如果删除行的事务仍处于活动状态（即尚未提交或中止），则此行即将到期。|  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server XTP（内存中 OLTP）性能计数器](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
