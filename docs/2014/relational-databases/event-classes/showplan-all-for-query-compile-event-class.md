---
title: Showplan All for Query Compile 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan All for Query Compile event class
ms.assetid: bb1dc446-5e6c-43d6-9db8-78c76cc2e01f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: facea3ca200d2b4ecb6a7230e8b49f85772a27fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125157"
---
# <a name="showplan-all-for-query-compile-event-class"></a>Showplan All for Query Compile 事件类
  在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 编译 SQL 语句时，会发生 Showplan All for Query Compile 事件类。 包括此事件类以标识 Showplan 运算符。 此事件类所包括的信息是 Showplan XML For Query Compile 事件类所包括信息的一部分。  
  
 由于 Showplan All for Query Compile 事件类显示完整的编译时数据，因此包含 Showplan All for Query Compile 的跟踪会产生性能系统开销。 若要最大限度地降低此开销，请仅将此事件类用于在短时间段内监视特定问题的跟踪。  
  
 跟踪中包括 Showplan All for Query Compile 事件类时，必须选中 BinaryData 数据列。 否则，跟踪中将不显示此事件类的信息。  
  
## <a name="showplan-all-for-query-compile-event-class-data-columns"></a>Showplan All for Query Compile 事件类数据列  
  
|数据列名称|数据类型|Description|列 ID|可筛选|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|10|用户帐户控制|  
|BinaryData|`image`|查询的预计成本。|2|否|  
|ClientProcessID|`int`|主机为运行该客户端应用程序的进程分配的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|用户帐户控制|  
|DatabaseID|`int`|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 如果在跟踪中捕获 ServerName 数据列而且服务器可用，则将显示数据库名。 可使用 DB_ID 函数来确定数据库的值。|3|用户帐户控制|  
|DatabaseName|`nvarchar`|正在其中运行用户语句的数据库的名称。|35|用户帐户控制|  
|EventClass|`int`|事件类型 = 169。|27|否|  
|EventSequence|`int`|特定事件在请求中的顺序。|51|否|  
|GroupID|`int`|在其中激发 SQL 跟踪事件的工作负荷组的 ID。|66|用户帐户控制|  
|HostName|`nvarchar`|正在运行客户端的计算机的名称。 如果客户端提供了主机名，则填充此数据列。 若要确定主机名，请使用 HOST_NAME 函数。|8|用户帐户控制|  
|IntegerData|`int`|预计返回的行数。|25|用户帐户控制|  
|IsSystem|`int`|指示事件是发生在系统进程中还是发生在用户进程中。 1 = 系统，0 = 用户。|60|用户帐户控制|  
|LineNumber|`int`|显示包含错误的行的编号。|5|用户帐户控制|  
|LoginName|`nvarchar`|用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“DOMAIN\username”）。|11|用户帐户控制|  
|LoginSID|`image`|登录用户的安全标识号 (SID)。 您可以在 sys.server_principals 目录视图中找到此信息。 服务器中的每个登录名都具有唯一的 SID。|41|否|  
|NestLevel|`int`|表示 @@NESTLEVEL 所返回的数据的整数。|29|用户帐户控制|  
|NTDomainName|`nvarchar`|用户所属的 Windows 域。|7|用户帐户控制|  
|NTUserName|`nvarchar`|Windows 用户名。|6|用户帐户控制|  
|ObjectID|`int`|系统分配的对象 ID。|22|用户帐户控制|  
|ObjectName|`nvarchar`|引用的对象名。|34|用户帐户控制|  
|ObjectType|`int`|表示事件中涉及的对象类型的值。 该值对应于 sys.objects 中的类型列。 有关值的信息，请参阅 [ObjectType 跟踪事件列](objecttype-trace-event-column.md)。|28|用户帐户控制|  
|RequestID|`int`|包含该语句的请求的 ID。|49|用户帐户控制|  
|ssSqlProfiler|`nvarchar`|所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。|26|否|  
|SessionLoginName|`nvarchar`|发起会话的用户的登录名。 例如，如果您使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，再以 Login2 的身份执行语句，则 SessionLoginName 将显示 Login1，而 LoginName 将显示 Login2。 此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。|64|用户帐户控制|  
|SPID|`int`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为客户端的相关进程分配的服务器进程 ID。|12|用户帐户控制|  
|StartTime|`datetime`|事件开始的时间（如果可用）。|14|用户帐户控制|  
|TransactionID|`bigint`|系统分配的事务 ID。|4|用户帐户控制|  
|XactSequence|`bigint`|用于说明当前事务的标记。|50|用户帐户控制|  
  
## <a name="see-also"></a>请参阅  
 [扩展事件](../extended-events/extended-events.md)   
 [sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Showplan 逻辑运算符和物理运算符参考](../showplan-logical-and-physical-operators-reference.md)  
  
  
