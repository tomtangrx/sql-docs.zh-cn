---
title: "安装 Reporting Services SharePoint 模式 |Microsoft 文档"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 17effa28932798a3cd35427a0a7104d4aa355b56
ms.contentlocale: zh-cn
ms.lasthandoff: 08/09/2017

---
# <a name="install-reporting-services-sharepoint-mode"></a>安装 Reporting Services SharePoint 模式

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services SharePoint 中，启用报表创建和查看文档库中的[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]订阅发送报表通过电子邮件， [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]，数据警报以及报表管理功能，所有的部署中的基于[!INCLUDE[msCoName](../../includes/msconame-md.md)]SharePoint。 有关在 SharePoint 模式下的功能的详细信息，请参阅"功能支持和行为的差异按服务器模式"一节中[Reporting Services 报表服务器](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)。

> [!NOTE]
> 与 SharePoint 的 reporting Services 集成 SQL Server 2016 之后将不再可用。

安装 SharePoint 模式下的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 两个核心 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件：  

|安装|说明|  
|------------------|-----------------|  
|**报表服务器：** 在 SharePoint 模式下安装的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器|该报表服务器处理数据和报表处理和呈现以及订阅和数据警报处理。 SharePoint 模式报表服务器设计并安装为 SharePoint 共享服务。<br /><br /> **如何：** 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装介质安装报表服务器。|  
|**外接程序：** SharePoint 产品 (**rssharepoint.msi**) 的[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序。|该外接程序在 SharePoint Web 前端服务器上安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用户界面 (UI) 页和功能。 UI 功能包括 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint 管理中心中的管理页、在 SharePoint 文档库内使用的功能页以及 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据警报页。<br /><br /> **方法：**  外接程序可以通过 Web 下载或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装介质安装。 有关详细信息，请参阅 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。|  
  
## <a name="in-this-section"></a>本节内容  
 [支持的 SharePoint 和 Reporting Services 服务器及外接程序的组合 (SQL Server 2016)](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [在 SharePoint 模式下安装第一个报表服务器](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [安装或卸载用于 SharePoint 的 Reporting Services 外接程序](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [向场中添加另一个报表服务器（SSRS 扩展）](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [向场中添加另一个 Reporting Services Web 前端](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [为 Reporting Services 服务应用程序配置电子邮件（SharePoint 2013 和 SharePoint 2016）](http://msdn.microsoft.com/en-us/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [用于 SSRS 服务应用程序的设置订阅和警报](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Claims to Windows Token Service (c2WTS) 和 Reporting Services](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  

## <a name="next-steps"></a>后续步骤

 [数据警报体系结构和工作流](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [管理员提出警报的数据警报管理器](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  

更多问题？ [尝试的 Reporting Services 论坛](http://go.microsoft.com/fwlink/?LinkId=620231)