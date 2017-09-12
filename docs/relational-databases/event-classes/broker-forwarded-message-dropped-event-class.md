---
title: "Broker:Forwarded Message Dropped 事件类 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker:Forwarded Message Dropped event class
ms.assetid: ec242d0b-77b0-45f5-8b12-186a14b173a8
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8d63f05d5f476dcb03398872759b92e21d04c99c
ms.contentlocale: zh-cn
ms.lasthandoff: 06/22/2017

---
# <a name="brokerforwarded-message-dropped-event-class"></a>Broker:Forwarded Message Dropped 事件类
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 当 Service Broker 删除要用于转发的消息时，将生成 Broker:Forwarded Message Dropped 事件。  
  
## <a name="brokerforwarded-message-dropped-event-class-data-columns"></a>Broker:Forwarded Message Dropped 事件类的数据列  
  
|数据列|类型|说明|列号|可筛选|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|**nvarchar**|客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|10|是|  
|BigintData1|**bigint**|消息序列号。|52|是|  
|ClientProcessID|**int**|由主机分配给正在运行客户端应用程序的进程的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|是|  
|DatabaseID|**int**|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database*语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 将显示数据库名。 可使用 DB_ID 函数来确定数据库的值。|3|是|  
|DatabaseName|**nvarchar**|正在运行用户语句的数据库的名称。|35|是|  
|DBUserName|**nvarchar**|此消息来自的 Broker 实例标识符。|40|是|  
|错误|**int**|事件中文本的 sys.messages 的消息 ID 号。|31|是|  
|EventClass|**int**|捕获的事件类的类型。 对于 Broker:Forwarded Message Dropped，始终为 191。|27|是|  
|EventSequence|**int**|此事件的序列号。|51|是|  
|FileName|**nvarchar**|作为消息发送目标的服务的名称。|36|是|  
|GUID|**uniqueidentifier**|对话的会话 ID。 此标识符将作为消息的一部分进行传输，并在会话双方之间共享。|54|是|  
|HostName|**nvarchar**|正在运行客户端程序的计算机的名称。 如果客户端提供了主机名，则填充此数据列。 若要确定主机名，请使用 HOST_NAME 函数。|8|是|  
|IndexID|**int**|所转发消息的剩余跃点数。|24|是|  
|IntegerData|**int**|所转发消息的片段数。|25|是|  
|LoginSid|**图像**|已登录用户的安全标识号 (SID)。 服务器中的每个登录名都具有唯一的 SID。|41|是|  
|NTDomainName|**nvarchar**|用户所属的 Windows 域。|7|是|  
|NTUserName|**nvarchar**|拥有生成此事件的连接的用户的名称。|6|是|  
|ObjectId|**int**|转发的消息的生存时间值。|22|是|  
|ObjectName|**nvarchar**|所转发消息的消息 ID。|34|是|  
|OwnerName|**nvarchar**|消息目标的 Broker 实例标识符。|37|是|  
|RoleName|**nvarchar**|会话句柄的角色。 可为下列值之一：<br /><br /> -Initiator。 此 Broker 发起了该会话。<br /><br /> -Target。 此 Broker 是会话的目标。|38|是|  
|ServerName|**nvarchar**|所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。|26|是|  
|Severity|**int**|事件中文本的严重级别号。|29|是|  
|SPID|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为客户端所关联的进程分配的服务器进程 ID。|12|是|  
|StartTime|**datetime**|事件（如果有）的开始时间。|14|是|  
|State|**int**|指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源代码中生成该事件的位置。 可能生成此事件的每个位置都有不同的状态代码。 Microsoft 支持工程师可使用此状态代码查找生成该事件的位置。|30|是|  
|成功|**int**|消息处于活动状态的时间长度。 如果此值大于或等于生存时间，则删除该消息。|23|是|  
|TargetLoginName|**nvarchar**|消息本应已转发到的网络地址。|42|是|  
|TargetUserName|**nvarchar**|启动消息的服务的名称。|39|是|  
|TextData|**ntext**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 删除消息的原因说明。|1|是|  
|Transaction ID|**bigint**|系统为事务分配的 ID。|4|是|  
  
 此事件的 TextData 列包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 删除消息的原因说明。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  