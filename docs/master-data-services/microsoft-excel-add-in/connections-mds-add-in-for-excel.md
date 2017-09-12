---
title: "连接 （MDS 外接程序 excel） |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
caps.latest.revision: 12
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3223a2a26e9476549afd5bd5dbdef84337414ac8
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="connections-mds-add-in-for-excel"></a>连接（用于 Excel 的 MDS 外接程序）
  若要将数据下载到 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，必须首先创建连接。 通过建立连接， [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 服务才知道要连接到哪个 MDS 数据库。  
  
 连接字符串通常是 URL [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web 应用程序，例如`http://contoso/mds`。  
  
 每次启动 Excel 时，您必须连接到一个 MDS 存储库。 只有在活动电子表格已包含 MDS 管理的数据的情况下才例外。 在这种情况下，每次刷新或发布工作表中的数据时会自动建立连接。  
  
 您可以创建多个连接。 最近访问过的连接被视为默认连接。  
  
 可以同时连接多个用户。 但是，当多个用户试图发布相同的数据时，可能会发生冲突。 有关详细信息，请参阅[概述：从 Excel 导入数据（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)。  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>自动连接和加载常用数据  
 如果总要连接同一服务器并加载相同的一组数据，您可以创建快捷查询文件，其中包含连接和筛选器信息。 有关查询文件的详细信息，请参阅 [快捷查询文件（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)。  
  
## <a name="data-quality-services"></a>Data Quality Services  
 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 提供数据质量服务功能，可帮助您在将数据发布到 MDS 存储库之前先匹配数据。 建立连接时，如果 DQS 数据库与 MDS 数据库安装在同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上，您将能够在功能区上看到 DQS 按钮。 如果 DQS_Main 数据库没有位于该实例上，则这些按钮不显示，且数据质量功能不可用。  
  
## <a name="related-tasks"></a>相关任务  
  
|任务说明|主题|  
|----------------------|-----------|  
|创建与 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 数据库的连接。|[连接到 MDS 存储库（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|将 MDS 数据加载到 Excel 中。|[Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
|将 MDS 数据加载到 Excel 中之前先对其进行筛选。|[导出前筛选数据（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>相关内容  
  
-   [概述：将数据导出到 Excel（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [快捷查询文件（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [用于 Microsoft Excel 的 Master Data Services 外接程序](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  