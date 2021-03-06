---
title: “服务器触发器递归”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1c2e8192c83fe0a654d90b47edaa5d77eb4c483f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111981"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>server trigger recursion 服务器配置选项
  使用 **server trigger recursion** 选项可指定是否允许服务器级触发器递归激发。 当此选项设置为 1 (ON) 时，将允许服务器级触发器递归激发。 当设置为 0 (OFF) 时，服务器级触发器不能递归激发。 当 server trigger recursion 选项设置为 0 (OFF) 时，仅阻止直接递归。 （若要禁用间接递归，请将 **nested triggers** 选项设置为 0。）该选项的默认值为 1 (ON)。 该设置更改后立即生效，而不需要重新启动服务器。  
  
 有关详细信息，请参阅 [创建嵌套触发器](../../relational-databases/triggers/create-nested-triggers.md)。  
  
## <a name="see-also"></a>请参阅  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
