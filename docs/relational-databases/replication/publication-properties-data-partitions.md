---
title: "发布属性 - 数据分区 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.datapartitions.f1
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 50ef9df48b07e6be66798ac2bd5f33dc57fe6a84
ms.contentlocale: zh-cn
ms.lasthandoff: 06/22/2017

---
# <a name="publication-properties-data-partitions"></a>发布属性，数据分区
  可以使用 **“发布属性”** 对话框的 **“数据分区”** 页，定义使用参数化筛选的合并发布的数据分区。 在定义分区后，您随后还可以生成这些分区的快照，为基于订阅服务器的连接属性（登录名和/或计算机名称）的不同订阅服务器提供不同的初始数据集。 如果订阅服务器在第一次同步时对其分区没有可用的快照，您还可以选择允许订阅服务器请求快照的传递和生成。 有关详细信息，请参阅 [为包含参数化筛选器的合并发布创建快照](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。  
  
## <a name="options"></a>选项  
 **添加**  
 单击 **“添加”** 可以定义分区。 在 **“添加数据分区”** 对话框中，为 **HOST_NAME()** 和/或 **SUSER_SNAME()**指定值，再定义计划以刷新快照即可。  
  
 **编辑**  
 选择网格中的现有分区，再单击 **“编辑”** 可以编辑相应的分区。  
  
 **删除**  
 选择网格中的现有分区，再单击 **“删除”** 可以删除相应的分区。  
  
 **立即生成所选快照**  
 选择网格中的一个或多个分区，再单击 **“立即生成所选快照”** 可以生成这些分区的快照。  
  
 **清除现有快照**  
 选择网格中的一个或多个分区，再单击 **“清除现有快照”** 可以清除这些分区的快照。  
  
 **在新订阅服务器尝试同步时，根据需要自动定义分区并生成快照**  
 如果希望允许订阅服务器请求快照的生成和应用程序，请选择此选项。 如果订阅服务器在第一次同步时对其分区没有可用的快照，则订阅服务器可能要求设置此选项。  
  
## <a name="see-also"></a>另请参阅  
 [创建发布](../../relational-databases/replication/publish/create-a-publication.md)   
 [查看和修改发布属性](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [参数化行筛选器](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [发布数据和数据库对象](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [带有参数化筛选器的合并发布的快照](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  