---
title: 发布属性 - 发布访问列表 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8dfe6ea6cace81776deefe3b0824d7289e9ed6b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784495"
---
# <a name="publication-properties-publication-access-list"></a>发布属性，发布访问列表
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  可以使用 **“发布属性”** 对话框的 **“发布访问列表”** 页，在发布访问列表 (PAL) 中添加和删除登录名、帐户和组。 PAL 是用于保护发布服务器的主要机制。 创建发布时，复制将为该发布创建 PAL。 PAL 的功能类似于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 访问控制列表，PAL 包含被授予该发布的访问权的登录名、帐户和组的列表。  
  
 当订阅服务器连接到发布服务器或分发服务器并请求访问发布时，订阅服务器的登录名将与 PAL 中的身份验证信息进行比较。 这样，通过防止客户端工具使用发布服务器和分发服务器登录名在发布服务器上直接进行修改，从而为发布服务器提供额外的安全性。 有关详细信息，请参阅[保护发布服务器](../../relational-databases/replication/security/secure-the-publisher.md)。  
  
## <a name="options"></a>选项  
 **“添加”**  
 将新项添加到列表。 只能添加那些在发布服务器和分发服务器上均已定义的登录名、帐户或组名称。 如果使用域帐户或在两个服务器上都已创建本地帐户，则这些信息在两个服务器上均已定义。  
  
 **删除**  
 从列表中删除所选项。  
  
 **全部删除**  
 从列表中删除所有项。  
  
## <a name="see-also"></a>另请参阅  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [查看和修改发布属性](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [发布数据和数据库对象](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
