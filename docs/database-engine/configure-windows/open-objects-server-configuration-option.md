---
title: "open objects 服务器配置选项 | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e620443786ae337e78062abc8cf99f0a077fbd99
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="open-objects-server-configuration-option"></a>open objects 服务器配置选项
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  虽然该选项的功能在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中已禁用，但在 **sp_configure** 中该选项仍然存在。 （其设置不起作用。）在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，打开的数据库对象的数量是动态管理的，该数量只受可用内存的限制。 **sp_configure** 中可用的 **open objects** 选项用于现有脚本的后向兼容性。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
