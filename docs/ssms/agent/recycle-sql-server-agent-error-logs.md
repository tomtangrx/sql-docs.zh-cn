---
title: 回收 SQL Server 代理错误日志 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 905763fcb4f44b3cf9fa27c450b187ec448fedb8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760345"
---
# <a name="recycle-sql-server-agent-error-logs"></a>回收 SQL Server 代理错误日志
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此页可以回收 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志。 回收该日志将关闭当前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理错误日志并启动新的错误日志，而且不会重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。 注意， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理保留九个最新的错误日志。 如果已经有九个错误日志，则回收错误日志会导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理删除最早的错误日志。  
  
## <a name="see-also"></a>另请参阅  
[SQL Server 代理错误日志](../../ssms/agent/sql-server-agent-error-log.md)  
  
