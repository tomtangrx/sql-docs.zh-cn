---
title: "Reporting Services (SSRS) |Microsoft 文档"
description: "了解针对移动和分页 Reporting Services 报表和在本地的 Power BI 报表工具和服务。"
ms.custom: 
ms.date: 07/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
caps.latest.revision: 70
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 49f990d30564a2c4fc38a527e7da1e97f9a21ca1
ms.contentlocale: zh-cn
ms.lasthandoff: 07/03/2017

---

# 什么是 SQL Server Reporting Services (SSRS)？
<a id="what-is-sql-server-reporting-services-ssrs" class="xliff"></a>

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

创建、 部署和管理移动和分页 Reporting Services 报表和在准备就绪，可以使用的工具和 SQL Server Reporting Services (SSRS) 和 Power BI 提供的服务的范围内的本地上的 Power BI 报表。

![SQL Server Reporting Services 一起](../reporting-services/media/ss-reporting-services-all-together.png "SQL Server Reporting Services 所有组合在一起")

## 创建、 部署和管理移动和分页报表
<a id="create-deploy-and-manage-mobile-and-paginated-reports" class="xliff"></a>

SQL Server Reporting Services 是客户在其本地部署的一种解决方案，用于创建、发布和管理报表，然后以不同方式将其传送到正确的用户，用户可在 Web 浏览器或移动设备中查看报表，也可在收件箱中查看电子邮件形式的报表。

对于 SQL Server 2016，Reporting Services 提供产品的更新套件：

* 提供最新的**传统分页报表** ，使用户可通过更新工具和用于创建报表的新功能创建新式报表。
* 具有响应式布局的**新移动报表** ，可适应不同设备和保存方式。
* **新式 Web 门户** ，可在任何新式浏览器中查看。 在新门户中，你可以组织，并显示移动和分页 Reporting Services 报表和 Kpi 以及 Power BI Desktop 报表。 此外可以在门户上存储的 Excel 工作簿。

请继续阅读有关每项的详细信息。

> [!NOTE]
> 查找 Power BI 报表服务器？ 请参阅[开始使用 Power BI 报表服务器](https://powerbi.microsoft.com/documentation/reportserver-get-started/)。

### Reporting Services 中的新增功能
<a id="whats-new-in-reporting-services" class="xliff"></a>

这些源让你可以随时了解最新的 SQL Server 2016 Reporting Services 新增功能。

* [Reporting Services 中的新增功能](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)
* [SQL Server Reporting Services 团队博客](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Guy in a Cube YouTube 通道](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)

## 分页报表
<a id="paginated-reports" class="xliff"></a>

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

Reporting Services 与“传统”分页文档样式报表相关联，这种报表中数据越多，表格中的行就越多，报表的页数也越多。 这非常适合生成针对打印优化的固定布局、像素完美的文档，如 PDF 和 Word 文件。

现在仍存在核心 BI 工作负荷，因此我们对其进行了改进。 现在，你可以使用更新的新功能创建现代查看报表，使用[报表生成器](../reporting-services/report-builder/report-builder-in-sql-server-2016.md)或报表设计器中[SQL Server Data Tools (SSDT)](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)。

* 已更新所有默认样式和调色板，因此默认情况下，使用新的极简主义新式样式创建报表。
* 已更新“参数”窗格，因此可随意排列参数。
* 可以导出到 PowerPoint 等新格式。 PowerPoint 中的 Reporting Services 可视化效果是实时且可编辑的，不仅仅是屏幕截图。
* 可创建混合的 Power BI/Reporting Services 体验：可将报表中的视觉对象固定到 Power BI 仪表板，而不是在 Power BI 中重新创建本地 Reporting Services 报表。 然后可以在 Power BI 仪表板上同一个位置监视所有内容。

## 移动报表
<a id="mobile-reports" class="xliff"></a>

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

移动计算已经改变了工作所用的设备，这意味着现在的用户具有不同的报告需求。 引入平板电脑和手机时，固定布局报表体验不佳。 针对宽屏电脑设计的内容无法在小屏幕手机上获得最佳体验，小屏幕手机不仅尺寸更小而且采用纵向或横向布局。

这些差异很大的屏幕外形规格所需的不是固定布局，而是可适应不同设备和不同保留方式的响应式布局。 为此，我们添加了新的报表类型：移动报表，此报表基于我们在约一年前获得并集成到产品中的 Datazen 技术。 使用 [SQL Server Migration Assistant for Datazen](https://www.microsoft.com/download/details.aspx?id=53128)可以将现有 Datazen 报表迁移到 Reporting Services。 

在新的 [移动报表发布服务器](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) 应用中创建这些移动报表。 然后在本机适用于 Windows 10、iOS、Android 和 HTML5 的 [用于移动设备的 Power BI 应用](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/) 中，可访问 Power BI 云中的数据以及本地 SQL Server 2016 Reporting Services 数据。 创建可视化效果时，移动报表发布服务器自动生成每种可视化效果的示例数据，因此可查看数据的可视化效果以及每种可视化效果中可正常运行的数据类型。

## Web 门户
<a id="web-portal" class="xliff"></a>

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

对于本机模式 Reporting Services 的最终用户，前门是可在任何新式浏览器中查看的新式 Web 门户。 你可以访问新门户中，加上 Power BI Desktop 报表中的所有 Reporting Services 移动和分页报表和 Kpi。 阅读更多有关[Reporting Services 中的 Power BI 报表](../reporting-services/power-bi-reports-in-reporting-services.md)。  

可将自己的自定义品牌应用到 Web 门户。 可在 Web 门户中创建 KPI。 KPI 可结合浏览器查看关键业务指标，而无需打开报表。 

新的 Web 门户是完全重写的报表管理器。 现在，它是单页、基于标准的 HTML5 应用，新式浏览器针已针对此应用进行了优化，这些浏览器包括：Microsoft Edge、Internet Explorer 10 和 11、Chrome、Firefox、Safari 以及所有主流浏览器。

按类型组织 web 门户上的内容： Reporting Services 移动和分页报表和 Kpi，加上 Power BI Desktop 报表、 Excel 工作簿、 共享数据集和共享的数据源以用作您的报表的构建基块。 你可以存储和管理它们安全地在这里，传统的文件夹层次结构中。 可以标记收藏夹并管理内容（如果拥有该角色）。

在新的 Web 门户中，仍可计划报表处理、按需访问报表并订阅已发布的报表。

有关[Web 门户 （SSRS 本机模式）](../reporting-services/web-portal-ssrs-native-mode.md)。

## SharePoint 集成模式下的 Reporting Services
<a id="reporting-services-in-sharepoint-integrated-mode" class="xliff"></a>

在 SharePoint 集成模式下将报表发布到 Repoorting Services。 可以计划报表处理，按需访问报表，订阅已发布的报表并将报表导出到其他应用程序，例如 Microsoft Excel。 可以在发布到 SharePoint 站点的报表上创建数据警报，并在报表数据更改时接收电子邮件。  

了解有关 [SharePoint 集成模式下的 Reporting Services 报表服务器](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md)的详细信息。

## [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 编程功能
<a id="includessrsnoversionincludesssrsnoversion-mdmd-programming-features" class="xliff"></a>

利用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 编程功能，你可以扩展和自定义报表功能，使用 API 在自定义应用程序中集成或扩展数据和报表处理。

更多 [Reporting Services 开发人员文档](../reporting-services/reporting-services-developer-documentation.md). 

## 后续步骤
<a id="next-steps" class="xliff"></a>

* [安装 Reporting Services](../reporting-services/install-windows/install-reporting-services.md)  
* [安装报表生成器](../reporting-services/install-windows/install-report-builder.md)   
* [下载 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)  
* [在 Reporting Services 中的 power BI 报表](../reporting-services/power-bi-reports-in-reporting-services.md)

更多问题？ [尝试的 Reporting Services 论坛](http://go.microsoft.com/fwlink/?LinkId=620231)