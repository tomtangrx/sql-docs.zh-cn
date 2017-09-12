---
title: "转换 Sybase ASE 数据库对象 (SybaseToSQL) |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Converting Database Objects
ms.assetid: 509cb65d-2f54-427a-83d7-37919cc4e3e3
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dd8fba1682d270251a865675f047e69a66e12479
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="converting-sybase-ase-database-objects-sybasetosql"></a>转换 Sybase ASE 数据库对象 (SybaseToSQL)
你已连接到 Sybase 自适应 Server Enterprise (ASE) 后，连接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 和设置项目和数据映射选项，您可以将转换到的 Sybase 自适应 Server Enterprise (ASE) 数据库对象[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 数据库对象。  
  
## <a name="the-conversion-process"></a>转换过程  
转换数据库对象从 ASE 所需的对象定义，将它们转换为类似[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 对象，然后将此信息加载到 SSMA 元数据。 不，它不会将信息加载到的实例[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure。 您然后可以通过查看对象及其属性[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 元数据资源管理器。  
  
在转换期间，SSMA 打印消息输出到输出窗格中，并为错误列表窗格中的错误消息。 使用的输出和错误的信息来确定你是否必须修改你的 ASE 数据库或您的转换过程，以获取所需的转换结果。  
  
## <a name="setting-conversion-options"></a>设置转换选项  
在将对象转换之前, 查看中的项目转换选项**项目设置**对话框。 通过使用此对话框中，你可以设置 SSMA 将函数和全局变量的转换。 有关详细信息，请参阅[项目设置 &#40;转换 &#41;&#40;SybaseToSQL &#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
## <a name="converting-ase-database-objects"></a>转换 ASE 数据库对象  
若要转换 ASE 数据库对象，你首先选择你想要转换的对象，然后执行转换的 SSMA。 若要查看输出消息在转换期间上,**视图**菜单上，选择**输出**。  
  
**若要将 ASE 对象转换为 SQL Server 或 SQL Azure 语法**  
  
1.  在 Sybase 元数据资源管理器中，展开 ASE 服务器，然后展开**数据库**。  
  
2.  选择要转换的对象：  
  
    -   若要转换的所有数据库，请旁边选中的复选框**数据库**。  
  
    -   若要将转换或省略数据库，选择或清除数据库名称旁边的复选框。  
  
    -   若要将转换或省略单个架构，展开数据库，展开**架构**，然后选中或清除架构旁边的复选框。  
  
    -   若要将转换或忽略的对象的类别，展开架构，然后选择或清除的类别旁边的复选框。  
  
    -   若要将转换或省略单个对象，展开类别文件夹中，然后选择或清除该对象旁边的复选框。  
  
3.  要将所有所选的对象的转换，请右键单击**数据库**和选择**转换架构**。  
  
    您还可以通过右键单击该对象或其包含的文件夹，然后选择转换单个对象的类别**转换架构**。  
  
> [!NOTE]  
> 某些 Sybase 系统函数不完全匹配的等效的 SQL Server 系统函数的行为。 为了模拟 Sybase ASE 行为，SSMA 将生成下调用 s2ss 的架构转换后的 SQL Server 数据库中用户定义函数。 具体取决于项目设置中，某些 SQL Server 系统函数会替换这些仿真函数。 SSMA 创建以下用户定义函数：  
  
||||  
|-|-|-|  
|**char_length_nvarchar**|**index_colorder**|**ssma_datepart**|  
|**char_length_varchar**|**inttohex**|**substring_nvarchar**|  
|**charindex_nvarchar**|**ssma_datediff**|**substring_varbinary**|  
|**charindex_varchar**|**hextoint**|**substring_varchar**|  
|**ulowsurr**|**to_unichar**|**ssma_current_time**|  
|**uhighsurr**|||  
  
## <a name="objects-not-supported-in-sql-azure"></a>不支持在 SQL Azure 中的对象  
以下 T-SQL 关键字用于通过 SSMA Sybase 转换为正则 SQL Server 过程，但这些关键字不受 SQL Azure T-SQL 语法：  
  
||||  
|-|-|-|  
|CHECKPOINT|CREATE/ALTER/DROP DEFAULT|CREATE/DROP RULE|  
|DBCC TRACEOFF|DBCC TRACEON|授权/撤销/拒绝所有|  
|KILL|READTEXT|SELECT INTO|  
|SET OFFSETS|SETUSER|SHUTDOWN|  
|WRITETEXT|||  
  
## <a name="viewing-conversion-problems"></a>查看转换问题  
某些 ASE 对象可能不进行转换。 你可以通过查看摘要转换报表来确定转换成功率。  
  
**若要查看摘要报表**  
  
1.  在 Sybase 元数据资源管理器中，选择**数据库**。  
  
2.  在右窗格中，选择**报表**选项卡。  
  
    此报表显示所有数据库对象的已评估或转换摘要评估的报表。 你还可以查看摘要报表为单个对象：  
  
    -   若要查看单个数据库的报表，请在 Sybase 元数据资源管理器中选择的数据库。  
  
    -   若要查看单个数据库对象的报表，请在 Sybase 元数据资源管理器中选择的对象。 转换问题的对象具有红色错误图标。  
  
对于失败转换的对象，你可以查看导致转换失败的语法。  
  
**若要查看单个转换问题**  
  
1.  在 Sybase 元数据资源管理器中，展开**数据库**。  
  
2.  展开显示红色错误图标的数据库。  
  
3.  展开**架构**文件夹，然后展开显示红色错误图标的架构。  
  
4.  在架构中，展开具有红色错误图标的文件夹。  
  
5.  选择具有红色错误图标的对象。  
  
6.  在右窗格中，单击**报表**选项卡。  
  
7.  在顶部**报表**选项卡是下拉列表。 如果此列表显示**统计信息**，更改选定范围向**源**。  
  
    SSMA 显示的源代码和紧邻代码之上的多个按钮。  
  
8.  单击**下一步问题**按钮。 这是一个带有箭头右侧的红色错误图标。  
  
    ASE 的 SSMA 将突出显示当前对象中找到的第一个有问题的源代码。  
  
对于无法转换每个项，您必须确定你想要使用该对象执行操作：  
  
-   您可以在编辑过程和触发器的源代码**SQL**选项卡。  
  
-   你可以更改要删除或修改有问题的代码的 ASE 对象。 若要更新的代码载入 SSMA，你将需要更新的元数据。 有关详细信息，请参阅[连接到 Sybase ASE &#40;SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
-   你可以从迁移中排除对象。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 元数据资源管理器和 Sybase 元数据资源管理器中，在加载到对象之前清除项旁边的复选框[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 和从 ASE 的迁移数据。  
  
## <a name="next-step"></a>下一步  
迁移过程的下一步是[加载转换数据库对象到 SQL Server / SQL Azure (SybaseToSQL)](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06)。  
  
## <a name="see-also"></a>另请参阅  
[Sybase ASE 将数据库迁移到 SQL Server 的 Azure SQL DB &#40;SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
