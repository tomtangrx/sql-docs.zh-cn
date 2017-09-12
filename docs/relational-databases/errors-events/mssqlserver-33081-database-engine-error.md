---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c5c47dd2a9d349da10e876f8da486790355be125
ms.contentlocale: zh-cn
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver33081"></a>MSSQLSERVER_33081
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|33081|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|消息正文|由于 Authenticode 签名或文件路径无效，未能加载加密提供程序“%.*ls”。  请检查以前的消息，了解其他失败信息。|  
  
## <a name="explanation"></a>解释  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法加载错误消息中列出的加密提供程序。 几个 Windows API 失败可能导致此错误。 环形缓冲区包含失败的 API 的名称和 API 返回的 Windows 错误代码。 若要获取更多信息，请使用以下查询来查询 sys.dm_os_ring_buffers 视图。  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>用户操作  
若要调查问题，请在 MSDN (http://msdn.microsoft.com/) 中搜索该 Windows 错误代码。 解决该问题，或联系 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客户支持服务部门以获得详细信息。 如果需要与客户支持服务部门联系，请为我们的支持人员收集以下信息。  
  
-   错误日志显示无法加载加密提供程序错误。  
  
-   执行以下语句所得到的输出：  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
> 尝试立即收集环形缓冲区信息，因为重新启动期间该信息会丢失。  
  
