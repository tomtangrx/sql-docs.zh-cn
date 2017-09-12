---
title: "时态表注意事项和限制 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a21481-0f0e-41e3-a1ad-49a84091b422
caps.latest.revision: 18
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 30791ad9733446f664db1592b95d1ffec5fc9a1b
ms.openlocfilehash: 5ee3aa9223ae8ab832eff23a1da1755278e86d0b
ms.contentlocale: zh-cn
ms.lasthandoff: 07/31/2017

---
# <a name="temporal-table-considerations-and-limitations"></a>时态表注意事项和限制
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  由于系统版本控制的特性，在使用时态表时，有一些应考虑的注意事项和限制。  
  
 使用时态表时，请考虑以下事项。  
  
-   时态表必须定义主键，以便将当前表的记录和历史记录表的记录关联起来，并且历史记录表不能定义主键。  
  
-   用于记录 **SysStartTime** 和 **SysEndTime** 值的 SYSTEM_TIME 时间段列必须使用数据类型 datetime2 进行定义。  
  
-   如果历史记录表的名称在历史记录表创建期间指定，则必须指定架构和表的名称。  
  
-   默认情况下，历史记录表是经过 **PAGE** 压缩的。  
  
-   如果当前表已分区，则历史记录表在默认文件组上创建，因为不会自动将分区配置从当前表复制到历史记录表。  
  
-   由于 **FILETABLE** 和 **FILESTREAM** 允许在 **外部进行数据操作，所以时态表和历史记录表不能为** FILETABLE **，且可以包含** FILESTREAM [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外的任何受支持的数据类型的列，因此系统版本控制不能得到保证。  
  
-   尽管时态表支持 Blob 数据类型，如 **(n)varchar(max)**、**varbinary(max)**、**(n)text** 和 **image**，但由于其大小，会导致产生巨大的存储成本，并可能对性能产生影响。 因此在设计系统的过程中，应慎重使用这些数据类型。  
  
-   必须在与当前表相同的数据库中创建历史记录表。 不支持对 **Linked Server** 的时态查询。  
  
-   历史记录表不能有约束（主键、外键、表或列约束）。  
  
-   时态查询（使用 **FOR SYSTEM_TIME** 子句的查询）的顶部不支持索引视图  
  
-   对于系统版本控制的时态表，Online 选项 (**WITH (ONLINE = ON**) 对 **ALTER TABLE ALTER COLUMN** 不起任何作用。 无论为 ONLINE 选项指定的值是什么，都不会 联机执行 ALTER 列。  
  
-   **INSERT** 和 **UPDATE** 语句无法引用 SYSTEM_TIME 时间段列。 将阻止将值直接插入这些列的尝试。  
  
-   **SYSTEM_VERSIONING** 为 **ON** 时，不支持 **TRUNCATE TABLE**  
  
-   不允许直接修改历史记录表中的数据。  
  
-   当前表上不允许**ON DELETE CASCADE** 和 **ON UPDATE CASCADE** 。 换言之，当时态表引用外键关系中的表时（对应于 sys.foreign_keys 中的 *parent_object_id* ），将不允许 CASCADE 选项。 若要解除此限制，请使用应用程序逻辑或 after 触发器，以在主键表中进行删除时保持一致性（对应于 sys.foreign_keys 中的  *referenced_object_id* ）。 如果主键表是时态表而引用表为非时态表，则不存在此类限制。 

    **注意：**此限制仅适用于 SQL Server 2016。 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] 和 SQL Server 2017（从 CTP 2.0 开始）中支持 CASCADE 选项。  
  
-   在当前表或历史记录表上均不允许使用**INSTEAD OF** 触发器，以避免导致 DML 逻辑失效。 仅在当前表上允许**AFTER** 触发器。 这些触发器在历史记录表上会被阻止，以避免导致 DML 逻辑失效。  
  
-   复制技术的使用受到限制。  
  
    -   **始终启用：** 完全支持  
  
    -   **更改数据捕获和更改数据跟踪：** 仅当前表支持  
  
    -   **快照和事务复制**：仅支持未启用时态的单个发布服务器和启用了时态的一个订阅服务器。 在这种情况下，发布服务器用于 OLTP 工作负载，而订阅服务器用于卸载报表（包括“AS OF”查询）。    
        不支持使用多个订阅服务器，因为这种方案可能导致时态数据不一致，原因是每个服务器都依赖于本地系统时钟。  
  
    -   **合并复制：** 不支持时态表  
  
-   定期查询仅影响当前表中的数据。 若要查询历史记录表中的数据，必须使用时态查询。 稍后将在本文档中“查询时态数据”部分讨论相关内容。  
  
-   最佳索引策略将包括当前表上的聚集列存储索引和/或 B 树行存储索引，以及历史记录表上的聚集列存储索引，旨在优化存储大小和性能。 如果你创建/使用自己的历史记录表，我们强烈建议你创建此类型的索引，它包含以时间段列的结尾为开头的时间段列，以加快时态查询，同时加快作为数据一致性检查的一部分的查询。 默认历史记录表具有基于时间段列（结束、开始）创建的聚集行存储索引。 建议至少应使用非聚集行存储索引。  
  
-   创建历史记录表后，不会将下列对象/属性从当前表复制到历史记录表  
  
    -   时间段定义  
  
    -   标识定义  
  
    -   索引  
  
    -   统计信息  
  
    -   检查约束  
  
    -   触发器  
  
    -   分区配置  
  
    -   权限  
  
    -   行级别安全性谓词  
  
-   在历史记录表链中，无法将历史记录表配置为当前表。  
  
## <a name="did-this-article-help-you-were-listening"></a>本文是否对你有帮助？ 我们洗耳恭听  
 你正在查找哪些信息，是否已经找到？ 我们不断听取你的反馈来改进内容。 请将你的评论提交到 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20Considerations%20and%20Limitations%20page)  
  
## <a name="see-also"></a>另请参阅  
 [时态表](../../relational-databases/tables/temporal-tables.md)   
 [系统版本控制时态表入门](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [时态表系统一致性检查](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [时态表分区](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [时态表安全性](../../relational-databases/tables/temporal-table-security.md)   
 [管理版本由系统控制的时态表中历史数据的保留期](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [系统版本控制时态表与内存优化表](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [时态表元数据视图和函数](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
