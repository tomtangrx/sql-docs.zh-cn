---
title: Deprecation Final Support 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Deprecation Final Support event class
- deprecation [SQL Server], events final support
ms.assetid: 2b4d88d0-62be-45c0-bea8-c5900d553d31
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b4165f92457abc8764095de73f53e6d0ed3d2348
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720605"
---
# <a name="deprecation-final-support-event-class"></a>Deprecation Final Support 事件类
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  当使用将从 **的下一个主版本中删除的功能时，将发生** Deprecation Final Support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]事件类。 为了使您的应用程序能够尽可能地长久使用，请不要使用会导致 **Deprecation Final Support** 事件类或 **Deprecation Announcement** 事件类的功能。 请尽快修改使用最终不推荐使用的功能的应用程序。  
  
## <a name="deprecation-final-support-event-class-data-columns"></a>Deprecation Final Support 事件类的数据列  
  
|数据列名称|数据类型|描述|列 ID|可筛选|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|10|用户帐户控制|  
|ClientProcessID|**int**|主机为运行该客户端应用程序的进程分配的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|用户帐户控制|  
|DatabaseID|**int**|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 数据列而且服务器可用，则 **ServerName** 将显示数据库名。 可使用 DB_ID 函数来确定数据库的值。|3|用户帐户控制|  
|DatabaseName|**nvarchar**|正在其中运行用户语句的数据库的名称。|35|用户帐户控制|  
|EventClass|**int**|事件类型 = 126。|27|否|  
|EventSequence|**int**|给定事件在请求中的顺序。|51|否|  
|HostName|**nvarchar**|正在运行客户端的计算机的名称。 如果客户端提供了主机名，则填充此数据列。 若要确定主机名，请使用 HOST_NAME 函数。|8|用户帐户控制|  
|IntegerData2|**int**|正在执行的语句的终止偏移量（字节）。|55|用户帐户控制|  
|IsSystem|**int**|指示事件是发生在系统进程中还是发生在用户进程中。 1 = 系统，0 = 用户。|60|用户帐户控制|  
|LoginName|**nvarchar**|用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“DOMAIN\username”）。|11|用户帐户控制|  
|LoginSid|**图像**|登录用户的安全标识号 (SID)。 你可以在 **sys.server_principals** 目录视图中找到此信息。 服务器中的每个登录名都具有唯一的 SID。|41|用户帐户控制|  
|NTDomainName|**nvarchar**|用户所属的 Windows 域。|7|用户帐户控制|  
|NTUserName|**nvarchar**|Windows 用户名。|6|用户帐户控制|  
|Offset|**int**|存储过程或批查询中的语句的起始偏移量。|61|用户帐户控制|  
|ObjectID|**int**|不推荐使用的功能的 ID 号。|22|用户帐户控制|  
|ObjectName|**nvarchar**|不推荐使用的功能的名称。|34|用户帐户控制|  
|RequestID|**int**|包含该语句的请求的 ID。|49|用户帐户控制|  
|ServerName|**nvarchar**|所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。|26|否|  
|SessionLoginName|**nvarchar**|发起会话的用户的登录名。 例如，如果你使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，再以 Login2 的身份执行语句，则 **SessionLoginName** 将显示 Login1，而 **LoginName** 将显示 Login2。 此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。|64|用户帐户控制|  
|SPID|**int**|发生该事件的会话的 ID。|12|用户帐户控制|  
|SqlHandle|**图像**|可用于标识 SQL 批处理或存储过程的二进制句柄。|63|用户帐户控制|  
|StartTime|**datetime**|该事件（如果存在）的启动时间。|14|用户帐户控制|  
|TextData|**ntext**|依赖于跟踪中捕获的事件类的文本值。|1|用户帐户控制|  
|TransactionID|**bigint**|系统分配的事务 ID。|4|用户帐户控制|  
|XactSequence|**bigint**|用于说明当前事务的标记。|50|用户帐户控制|  
  
## <a name="see-also"></a>另请参阅  
 [sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Deprecation Announcement 事件类](../../relational-databases/event-classes/deprecation-announcement-event-class.md)   
 [SQL Server 2016 中不推荐使用的数据库引擎功能](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
